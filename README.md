```sql
CREATE DATABASE call_list;
CREATE TABLE users(
  id SERIAL PRIMARY KEY,
  first_name VARCHAR(20),
  email VARCHAR(50)
  );
INSERT INTO users (first_name, email) VALUES ('Carlos', 'carlos.castillo@gmail.com');
INSERT INTO users (first_name, email) VALUES ('Laura', 'laura.rubio@gmail.com');
CREATE TABLE calls(
  id SERIAL PRIMARY KEY,
  phone INTEGER,
  date DATE,
  user_id INTEGER REFERENCES users (id),
  length INTEGER
  );
ALTER TABLE users ADD COLUMN last_name VARCHAR(20);
UPDATE users SET last_name='Castillo' WHERE first_name='Carlos';
UPDATE users SET last_name='Rubio' WHERE first_name='Laura';
INSERT INTO calls (phone, date, user_id, length) VALUES (982126324, '2018-02-01', 1, 120);
INSERT INTO calls (phone, date, user_id, length) VALUES (982126324, '2018-02-01', 1, 120);
INSERT INTO calls (phone, date, user_id, length) VALUES (982126324, '2018-02-01', 1, 120);
INSERT INTO calls (phone, date, user_id, length) VALUES (982126324, '2018-02-01', 1, 120);
INSERT INTO calls (phone, date, user_id, length) VALUES (982126324, '2018-02-01', 2, 120);
INSERT INTO calls (phone, date, user_id, length) VALUES (982126324, '2018-02-01', 2, 120);
INSERT INTO calls (phone, date, user_id, length) VALUES (982126324, '2018-02-01', 2, 120);
INSERT INTO calls (phone, date, user_id, length) VALUES (982126324, '2018-02-01', 2, 120);
INSERT INTO calls (phone, date, user_id, length) VALUES (982126324, '2018-02-01', 2, 120);
INSERT INTO calls (phone, date, user_id, length) VALUES (982126324, '2018-02-01', 2, 120);
INSERT INTO users (first_name, last_name, email) VALUES ('Milenko', 'Castillo', 'milenko.castillo@gmail.com');
SELECT first_name, COUNT(first_name) FROM users INNER JOIN calls ON (users.id = calls.user_id) GROUP BY first_name;
SELECT first_name, COUNT(first_name) AS nombre FROM users INNER JOIN calls ON (users.id = calls.user_id) GROUP BY first_name ORDER BY nombre DESC LIMIT 1;
SELECT first_name, phone, date, length from calls INNER JOIN users ON (users.id = calls.user_id) WHERE first_name='Carlos' ORDER BY date DESC;
SELECT first_name, length FROM users INNER JOIN calls ON (users.id = calls.user_id) ORDER BY length DESC LIMIT 1;
SELECT first_name, SUM(length) AS total_llamadas FROM users INNER JOIN calls ON (users.id = calls.user_id) GROUP BY first_name;
SELECT first_name, COUNT(first_name) FROM users INNER JOIN calls ON (users.id = calls.user_id) GROUP BY first_name HAVING COUNT(first_name) < 5;
CREATE TABLE auditoria(
  id SERIAL PRIMARY KEY,
  motive VARCHAR(140),
  user_id INTEGER REFERENCES users (id)
  );
```
