# 🐬 MySQL Mastery - Complete Learning Repository

A comprehensive, structured learning resource for mastering MySQL from fundamentals to advanced concepts. This repository is organized according to a university-level database curriculum, covering everything from basic DDL commands to advanced SQL concepts.

> **Your personal SQL learning guide with real examples and outputs!** Learn by doing, not just reading.

---

## 🎯 Quick Start (5 Minutes)

### What is SQL?
**SQL (Structured Query Language)** is a language used to communicate with databases. It allows you to:
- **Create** tables to store data
- **Read** data from tables
- **Update** existing data
- **Delete** data when needed

### First Example: Create a Table

**Theory**: A table is like a spreadsheet with rows and columns. Each column has a name and data type.

**SQL Code**:
```sql
CREATE TABLE students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    email VARCHAR(100)
);
```

**What happens**: Creates an empty table ready to store student information.

---

### Second Example: Insert Data

**Theory**: INSERT adds new records (rows) to your table.

**SQL Code**:
```sql
INSERT INTO students VALUES 
(1, 'Ali', 20, 'ali@email.com'),
(2, 'Zara', 19, 'zara@email.com'),
(3, 'Hassan', 21, 'hassan@email.com');
```

**Output** - Table now looks like:
```
student_id | name   | age | email
-----------|--------|-----|------------------
1          | Ali    | 20  | ali@email.com
2          | Zara   | 19  | zara@email.com
3          | Hassan | 21  | hassan@email.com
```

---

### Third Example: Read Data

**Theory**: SELECT retrieves data from your table.

**SQL Code**:
```sql
SELECT name, age FROM students WHERE age > 19;
```

**Output**:
```
name   | age
-------|-----
Ali    | 20
Hassan | 21
```

---

## 📚 Repository Organization

## 📚 Repository Organization

This repository is organized into **3 major chapters**, each building upon the previous:

---

## 📖 CHAPTER 1: Introduction to SQL - Master the Basics

### What You'll Learn in Chapter 1
- How to **create** and **modify** tables (DDL)
- How to **retrieve** data using SELECT queries (DQL)
- How to **filter** results with WHERE clauses
- How to **sort** data and **handle NULL values**
- How to **combine** results from multiple queries

---

### 1️⃣ **01-DDL-Commands**: Define Database Structures

#### 📌 Theory: What is DDL?
**DDL = Data Definition Language** — These commands define how data is organized.

**Key Commands:**
- `CREATE TABLE` — Create a new table
- `ALTER TABLE` — Modify an existing table
- `DROP TABLE` — Delete a table

#### 💡 Example 1: CREATE TABLE
**Purpose**: Design a table to store employee information

**SQL Code**:
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY AUTO_INCREMENT,
    first_name VARCHAR(50) NOT NULL,
    last_name VARCHAR(50) NOT NULL,
    salary DECIMAL(10,2),
    hire_date DATE
);
```

**Explanation**:
- `emp_id INT PRIMARY KEY` — Unique identifier for each employee
- `first_name VARCHAR(50) NOT NULL` — Name field, max 50 characters, required
- `salary DECIMAL(10,2)` — Salary with 2 decimal places (e.g., 50000.00)

**Output**: ✅ Table created successfully

---

#### 💡 Example 2: ALTER TABLE
**Purpose**: Add a new column to store phone numbers

**SQL Code**:
```sql
ALTER TABLE employees ADD COLUMN phone VARCHAR(20);
```

**Output**: ✅ New column added

**Result** — Table structure changes:
```
Column Name | Type        | Can Be Null
------------|-------------|-------------
emp_id      | INT         | No
first_name  | VARCHAR(50) | No
last_name   | VARCHAR(50) | No
salary      | DECIMAL     | Yes
hire_date   | DATE        | Yes
phone       | VARCHAR(20) | Yes (NEW)
```

**Files to Study**:
- `01-Create-Table-Construct.sql` — Create tables with data types
- `02-Alter-Table-Commands.sql` — Modify table structures
- `03-Drop-Table-Command.sql` — Remove tables safely

---

### 2️⃣ **02-Basic-Query-Components**: Retrieve and Filter Data

#### 📌 Theory: The SELECT Statement
SELECT is the most used command in SQL. It follows this structure:
```
SELECT [what columns] FROM [which table] WHERE [conditions];
```

#### 💡 Example 1: SELECT All Columns
**Purpose**: View all employee information

**SQL Code**:
```sql
SELECT * FROM employees;
```

**Output**:
```
emp_id | first_name | last_name | salary    | hire_date  | phone
-------|------------|-----------|-----------|------------|----------
1      | Ahmed      | Ali       | 75000.00  | 2023-01-15 | 0300-1111
2      | Fatima     | Khan      | 65000.00  | 2023-02-20 | 0300-2222
3      | Hassan     | Malik     | 80000.00  | 2023-01-10 | 0300-3333
```

---

#### 💡 Example 2: SELECT Specific Columns
**Purpose**: View only names and salaries

**SQL Code**:
```sql
SELECT first_name, last_name, salary FROM employees;
```

**Output**:
```
first_name | last_name | salary
-----------|-----------|----------
Ahmed      | Ali       | 75000.00
Fatima     | Khan      | 65000.00
Hassan     | Malik     | 80000.00
```

---

#### 💡 Example 3: WHERE Clause - Filter Data
**Purpose**: Find employees earning more than 70,000

**SQL Code**:
```sql
SELECT first_name, last_name, salary FROM employees WHERE salary > 70000;
```

**Output**:
```
first_name | last_name | salary
-----------|-----------|----------
Ahmed      | Ali       | 75000.00
Hassan     | Malik     | 80000.00
```

**Why**: Only 2 employees earn more than 70,000. Fatima's 65,000 doesn't match.

---

#### 💡 Example 4: AND Operator - Multiple Conditions
**Purpose**: Find employees in Sales earning more than 70,000

**SQL Code**:
```sql
SELECT first_name, salary FROM employees 
WHERE salary > 70000 AND hire_date > '2023-01-15';
```

**Output**:
```
first_name | salary
-----------|----------
Hassan     | 80000.00
```

**Why**: Hassan is hired after Jan 15 AND earns > 70,000

---

#### 💡 Example 5: ORDER BY - Sort Results
**Purpose**: List employees from highest to lowest salary

**SQL Code**:
```sql
SELECT first_name, salary FROM employees ORDER BY salary DESC;
```

**Output**:
```
first_name | salary
-----------|----------
Hassan     | 80000.00
Ahmed      | 75000.00
Fatima     | 65000.00
```

**DESC** = Descending (highest first). Use **ASC** for ascending (lowest first).

**Files to Study**:
- `01-SELECT-Clause.sql` — Select columns, create aliases
- `02-WHERE-Clause.sql` — Filter with conditions
- `03-FROM-Clause.sql` — Understand table sources

---

### 3️⃣ **03-Additional-Base-Operations**: Advanced Single-Table Queries

#### 💡 Example 1: AS Clause - Rename Columns
**Purpose**: Make output more readable with custom column names

**SQL Code**:
```sql
SELECT 
    first_name AS "Employee Name",
    salary AS "Monthly Salary",
    salary * 12 AS "Annual Salary"
FROM employees;
```

**Output**:
```
Employee Name | Monthly Salary | Annual Salary
--------------|----------------|---------------
Ahmed         | 75000.00       | 900000.00
Fatima        | 65000.00       | 780000.00
Hassan        | 80000.00       | 960000.00
```

---

#### 💡 Example 2: LIKE - Pattern Matching
**Purpose**: Find employees whose name starts with 'A'

**SQL Code**:
```sql
SELECT first_name, last_name FROM employees WHERE first_name LIKE 'A%';
```

**Output**:
```
first_name | last_name
-----------|----------
Ahmed      | Ali
```

**Wildcards**:
- `%` = any characters (0 or more)
- `_` = exactly one character
- `'A%'` = starts with A
- `'%z'` = ends with z
- `'%en%'` = contains 'en'

---

#### 💡 Example 3: String Functions
**Purpose**: Display names in uppercase

**SQL Code**:
```sql
SELECT UPPER(first_name), LOWER(last_name), LENGTH(first_name) FROM employees;
```

**Output**:
```
UPPER(first_name) | LOWER(last_name) | LENGTH(first_name)
------------------|------------------|-------------------
AHMED             | ali              | 5
FATIMA            | khan             | 6
HASSAN            | malik            | 6
```

**Files to Study**:
- `01-Rename-AS-Clause.sql` — Column aliasing
- `02-Self-Join-Queries.sql` — Compare rows in same table
- `03-String-Operations-Pattern-Matching.sql` — LIKE and string functions
- `04-Order-By-Clause.sql` — Sorting and LIMIT

---

### 4️⃣ **04-Set-Operations**: Combine Multiple Queries

#### 📌 Theory: What are Set Operations?
Combine results from multiple SELECT statements.

#### 💡 Example: UNION - Combine Results
**Purpose**: Get all unique employees from two departments

**SQL Code**:
```sql
SELECT name FROM it_employees
UNION
SELECT name FROM sales_employees;
```

**Output**:
```
name
--------
Ahmed
Hassan
Fatima
```

**UNION removes duplicates. Use UNION ALL to keep duplicates.**

**Files to Study**:
- `01-Union-Union-All.sql` — Combine result sets
- `02-Intersect-Intersect-All.sql` — Find common rows
- `03-Except-Except-All.sql` — Find differences

---

### 5️⃣ **05-Null-Value-Handling**: Handle Missing Data

#### 📌 Theory: What is NULL?
**NULL** means "no value" or "unknown". It's different from empty string or zero.

#### 💡 Example: Check for NULL Values
**Purpose**: Find employees without phone numbers

**SQL Code**:
```sql
SELECT first_name FROM employees WHERE phone IS NULL;
```

**Output**:
```
first_name
----------
Fatima
```

**Why**: Fatima has no phone number stored.

---

## 📖 CHAPTER 2: Advanced SQL - Master Complex Queries

### What You'll Learn in Chapter 2
- How to **summarize** data with aggregate functions
- How to **group** data and filter groups
- How to **modify** data (INSERT, UPDATE, DELETE)
- How to **enforce** data integrity with constraints

---

### 1️⃣ **01-Aggregate-Functions**: Summarize Data

#### 📌 Theory: What are Aggregate Functions?
Functions that calculate values from multiple rows:
- `COUNT()` — Count rows
- `SUM()` — Add values
- `AVG()` — Calculate average
- `MIN()` — Find minimum
- `MAX()` — Find maximum

#### 💡 Example 1: COUNT - Count Rows
**Purpose**: How many employees do we have?

**SQL Code**:
```sql
SELECT COUNT(*) AS "Total Employees" FROM employees;
```

**Output**:
```
Total Employees
---------------
3
```

---

#### 💡 Example 2: SUM and AVG - Calculate Totals
**Purpose**: What's the total and average salary?

**SQL Code**:
```sql
SELECT 
    SUM(salary) AS "Total Salary",
    AVG(salary) AS "Average Salary",
    COUNT(*) AS "Number of Employees"
FROM employees;
```

**Output**:
```
Total Salary | Average Salary | Number of Employees
-------------|----------------|-------------------
220000.00    | 73333.33       | 3
```

---

#### 💡 Example 3: GROUP BY - Summarize by Department
**Purpose**: Count employees in each department

**SQL Code**:
```sql
SELECT department, COUNT(*) AS "Employee Count" FROM employees GROUP BY department;
```

**Output**:
```
department | Employee Count
-----------|---------------
IT         | 2
Sales      | 1
```

---

#### 💡 Example 4: HAVING - Filter Groups
**Purpose**: Show departments with more than 1 employee

**SQL Code**:
```sql
SELECT department, COUNT(*) AS "Employee Count" 
FROM employees 
GROUP BY department 
HAVING COUNT(*) > 1;
```

**Output**:
```
department | Employee Count
-----------|---------------
IT         | 2
```

**Note**: HAVING filters GROUPS (use it after GROUP BY). WHERE filters ROWS (use before GROUP BY).

**Files to Study**:
- `01-Basic-Column-Aggregations.sql` — COUNT, SUM, AVG, MIN, MAX
- `02-Group-By-Clause.sql` — Partition data into groups
- `03-Having-Clause.sql` — Filter grouped results

---

### 2️⃣ **03-Database-Modification-Commands**: Insert, Update, Delete

#### 💡 Example 1: INSERT - Add New Data
**Purpose**: Add a new employee

**SQL Code**:
```sql
INSERT INTO employees (emp_id, first_name, last_name, salary, hire_date) 
VALUES (4, 'Amina', 'Shah', 78000.00, '2023-03-01');
```

**Output**: ✅ 1 row inserted

**Verification**:
```sql
SELECT * FROM employees;
```

**Output**:
```
emp_id | first_name | last_name | salary    | hire_date
-------|------------|-----------|-----------|----------
1      | Ahmed      | Ali       | 75000.00  | 2023-01-15
2      | Fatima     | Khan      | 65000.00  | 2023-02-20
3      | Hassan     | Malik     | 80000.00  | 2023-01-10
4      | Amina      | Shah      | 78000.00  | 2023-03-01 (NEW)
```

---

#### 💡 Example 2: UPDATE - Modify Data
**Purpose**: Increase Hassan's salary to 85,000

**SQL Code**:
```sql
UPDATE employees SET salary = 85000 WHERE first_name = 'Hassan';
```

**Output**: ✅ 1 row updated

**Verification**:
```sql
SELECT first_name, salary FROM employees WHERE first_name = 'Hassan';
```

**Output**:
```
first_name | salary
-----------|----------
Hassan     | 85000.00 (UPDATED)
```

---

#### 💡 Example 3: DELETE - Remove Data
**Purpose**: Remove the employee with ID 4

**SQL Code**:
```sql
DELETE FROM employees WHERE emp_id = 4;
```

**Output**: ✅ 1 row deleted

**Verification**:
```sql
SELECT COUNT(*) FROM employees;
```

**Output**:
```
COUNT(*)
--------
3
```

**Warning ⚠️**: Always use WHERE clause with DELETE! Without it, ALL rows are deleted!

**Files to Study**:
- `01-Insert-Commands.sql` — Insert single/multiple rows
- `02-Update-Commands.sql` — Modify existing data
- `03-Delete-Commands.sql` — Remove data safely

---

### 3️⃣ **04-Data-Constraints**: Enforce Data Integrity

#### 📌 Theory: What are Constraints?
Rules that ensure data quality and relationships.

#### 💡 Example 1: PRIMARY KEY
**Purpose**: Ensure each employee has a unique ID

**SQL Code**:
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(100)
);
```

**What happens**: You can't insert duplicate emp_id values.

**Test**:
```sql
INSERT INTO employees VALUES (1, 'Ahmed');
INSERT INTO employees VALUES (1, 'Hassan');  -- ERROR! emp_id 1 already exists
```

---

#### 💡 Example 2: FOREIGN KEY
**Purpose**: Link employees to departments

**SQL Code**:
```sql
CREATE TABLE departments (
    dept_id INT PRIMARY KEY,
    dept_name VARCHAR(100)
);

CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(100),
    dept_id INT,
    FOREIGN KEY (dept_id) REFERENCES departments(dept_id)
);
```

**What happens**: emp_id can only reference valid department IDs.

**Test**:
```sql
INSERT INTO employees VALUES (1, 'Ahmed', 999);  -- ERROR! dept_id 999 doesn't exist
```

---

#### 💡 Example 3: NOT NULL
**Purpose**: Ensure every employee has a name

**SQL Code**:
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL
);
```

**Test**:
```sql
INSERT INTO employees VALUES (1, 'Ahmed');  ✅ OK
INSERT INTO employees VALUES (2, NULL);     ❌ ERROR! Name cannot be empty
```

---

#### 💡 Example 4: UNIQUE
**Purpose**: Ensure each email address is unique

**SQL Code**:
```sql
CREATE TABLE employees (
    emp_id INT PRIMARY KEY,
    email VARCHAR(100) UNIQUE
);
```

**Test**:
```sql
INSERT INTO employees VALUES (1, 'ahmed@email.com');
INSERT INTO employees VALUES (2, 'ahmed@email.com');  -- ERROR! Email already exists
```

**Files to Study**:
- `01-Primary-Key.sql` — Unique row identifiers
- `02-Foreign-Key.sql` — Maintain relationships
- `03-Not-Null-Constraint.sql` — Require values
- `04-Unique-And-Check-Constraints.sql` — Enforce uniqueness and validation

---

## 📖 CHAPTER 3: Intermediate SQL - Master Advanced Techniques

### What You'll Learn in Chapter 3
- How to **join** data from multiple tables
- How to create **views** for simplified access
- How to create **triggers** for automation

---

### 1️⃣ **01-Advanced-Join-Expressions**: Combine Multiple Tables

#### 📌 Theory: What are JOINs?
JOINs combine data from multiple tables based on relationships.

#### 💡 Example: INNER JOIN
**Purpose**: Get employee names with department names

**Tables**:
```
employees table:           departments table:
emp_id | name    | dept_id  |  dept_id | dept_name
-------|---------|----------|----------|----------
1      | Ahmed   | 1        |  1       | IT
2      | Fatima  | 2        |  2       | Sales
3      | Hassan  | 1        |  3       | HR
```

**SQL Code**:
```sql
SELECT e.name, d.dept_name 
FROM employees e
INNER JOIN departments d ON e.dept_id = d.dept_id;
```

**Output**:
```
name   | dept_name
-------|----------
Ahmed  | IT
Fatima | Sales
Hassan | IT
```

**Why**: INNER JOIN shows only rows that exist in BOTH tables.

---

#### 💡 Example 2: LEFT JOIN
**Purpose**: Show all employees, even those without departments

**SQL Code**:
```sql
SELECT e.name, d.dept_name 
FROM employees e
LEFT JOIN departments d ON e.dept_id = d.dept_id;
```

**Output**:
```
name   | dept_name
-------|----------
Ahmed  | IT
Fatima | Sales
Hassan | IT
Amina  | (NULL)  -- No department assigned
```

**LEFT JOIN includes ALL rows from left table, even if no match.**

**Files to Study**:
- `01-Joins-Comprehensive.sql` — All JOIN types (INNER, LEFT, RIGHT, FULL, CROSS)

---

### 2️⃣ **02-View-Architectures**: Create Virtual Tables

#### 📌 Theory: What is a VIEW?
A VIEW is a saved query that acts like a virtual table.

#### 💡 Example: CREATE VIEW
**Purpose**: Create a view showing IT department employees

**SQL Code**:
```sql
CREATE VIEW it_employees AS
SELECT emp_id, name, salary 
FROM employees 
WHERE dept_id = 1;
```

**Usage**:
```sql
SELECT * FROM it_employees;
```

**Output**:
```
emp_id | name   | salary
-------|--------|----------
1      | Ahmed  | 75000.00
3      | Hassan | 85000.00
```

**Why use VIEWs?**
- Simplify complex queries
- Hide sensitive data
- Improve security
- Reuse queries

**Files to Study**:
- `01-Create-View.sql` — Create and use views

---

### 3️⃣ **03-Triggers**: Automate Database Actions

#### 📌 Theory: What is a TRIGGER?
A TRIGGER automatically executes SQL code when data changes.

#### 💡 Example: BEFORE INSERT Trigger
**Purpose**: Ensure salary is always positive

**SQL Code**:
```sql
CREATE TRIGGER check_salary 
BEFORE INSERT ON employees
FOR EACH ROW
BEGIN
    IF NEW.salary < 0 THEN
        SET NEW.salary = 0;
    END IF;
END;
```

**What happens**:
```sql
INSERT INTO employees VALUES (5, 'Zara', 1, -5000);
```

The trigger automatically sets salary to 0 instead of allowing negative value.

**Result in table**:
```
emp_id | name | salary
-------|------|-------
5      | Zara | 0 (not -5000)
```

**Files to Study**:
- `01-Introduction-to-Triggers.sql` — Create automated actions

---

## 🎯 Learning Path

## 🎯 Learning Path

**Recommended Study Sequence:**

1. **Week 1-2: Create Tables (Chapter 1 - DDL)**
   - ✅ Understand table structure and data types
   - ✅ Learn CREATE TABLE and ALTER TABLE
   - ✅ Complete Assignment 1

2. **Week 3-4: Query Data (Chapter 1 - Basic Components)**
   - ✅ Master SELECT and WHERE
   - ✅ Use ORDER BY, LIKE, and NULL handling
   - ✅ Complete Assignment 2

3. **Week 5-6: Summarize Data (Chapter 2 - Aggregates)**
   - ✅ Use COUNT, SUM, AVG, MIN, MAX
   - ✅ Learn GROUP BY and HAVING
   - ✅ Complete Assignment 3

4. **Week 7-8: Modify Data (Chapter 2 - DML)**
   - ✅ Insert, Update, Delete data safely
   - ✅ Understand transaction safety

5. **Week 9-10: Enforce Integrity (Chapter 2 - Constraints)**
   - ✅ Create PRIMARY and FOREIGN KEYs
   - ✅ Apply NOT NULL, UNIQUE, CHECK constraints

6. **Week 11-12: Combine Tables (Chapter 3 - JOINs)**
   - ✅ Master INNER, LEFT, RIGHT