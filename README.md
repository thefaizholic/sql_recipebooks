📌 Overview

This project is a recipe-sharing platform named Secukuprasa.com, hosted locally using XAMPP and developed using SQL Developer / MySQL.
The system supports:

Recipe creation by authors
Categorisation of recipes
User reviews
User account information linked to author and reviewer roles

Below is the link of ERD used to model the relational database.

https://drive.google.com/file/d/1vBm2iSOl-J146_rYbsyFQPGoBhqwGIdd/view?usp=sharing

🗄️ Database Structure & Explanation

The system consists of 6 main tables:

1. Account_Details

Stores authentication and identity information for all users (authors + regular users).

Field	Type	Description
account_id (PK)	INT	Unique account identifier
username	VARCHAR	Login username
FullName	VARCHAR	User’s full name
email	VARCHAR	Email address
password	VARCHAR	Hashed password
DateOfBirth	DATE	Birthday

Purpose:
Provides a centralized identity table so all profiles can reference one account.

2. Users

Represents general platform users who can leave reviews.

Field	Type	Description
user_id (PK)	INT	Unique ID for normal users
account_id (FK)	INT	Links to Account_Details

Relationship:

One Account → One User (1:1)

3. Author

Represents users who publish recipes.

Field	Type	Description
author_id (PK)	INT	Unique author ID
account_id (FK)	INT	Links to Account_Details
author_specialty	VARCHAR	Cuisine or cooking specialty

Relationship:

One Account → One Author (1:1)

Allows user accounts to also be recipe authors.

4. Recipe_Categories

Defines different recipe classifications.

Field	Type
category_id (PK)	INT
category_name	VARCHAR

Relationship:

One Category → Many Recipes (1:N

5. Recipes

Core table storing all recipe information.

Field	Type
recipe_id (PK)	INT
author_id (FK)	INT
category_id (FK)	INT
title	VARCHAR
instructions	TEXT
ingredients	TEXT
estimate_cost	DECIMAL

Relationships:

Many Recipes per Author
Many Recipes per Category

6. Review

Stores user feedback on recipes.

Field	Type
review_id (PK)	INT
recipe_id (FK)	INT
user_id (FK)	INT
rating	INT
comment	TEXT
timestamp	DATETIME

Relationships:

One Recipe → Many Reviews
One User → Many Reviews
