# Twitter-Scraping

ABSTRACT MODEL:
A user of Cuisine Website can login using their twitter handle. This will enable them to search for their favourite foods and celebrity chefs on our website.
UML DIAGRAM FOR CUISINE WEBSITE
SQL Statements for Conceptual Model
User Table:-
CREATE TABLE `User` (
`Username` VARCHAR(100),
`name` VARCHAR(20),
`joined_at` VARCHAR(200),
`description` VARCHAR(100),
PRIMARY KEY (`Username’)
);
Website Table:-
CREATE TABLE ‘Website_User’ (
‘Username’ VARCHAR(100),
PRIMARY KEY (`Username `)
);
Dish Table:-
CREATE TABLE `Dish` (
`recipe_id` VARCHAR(100),
`dish_name` VARCHAR(100),
`cuisine_type` VARCHAR(200),
`servings` VARCHAR(100),
`spiciness` VARCHAR(100),
PRIMARY KEY (`recipe_id `)
);
Recipe Table:-
CREATE TABLE `Recipe` (
`recipe_id` VARCHAR(100),
`ingredients` VARCHAR(100),
`recipe` VARCHAR(200),
FOREIGN KEY (`recipe_id `)
);
Popular hashtags Table:-
CREATE TABLE `popular hashtags` (
`trend_name` VARCHAR(100),
`trend_url` VARCHAR(100),
`tweet_volume` VARCHAR(200),
PRIMARY KEY (`trend_name `)
);
USE-CASES
1. Use Case: Search for spicy Indian dishes
Description: User searches for spicy Indian dishes
Actor: User
Precondition: When a user wants to search for dishes, they will be registered with the website
Steps:
Actor action: User views dishes from india which are spicy.
System Responses: list of dishes from india with high spicy level
Post Condition: system displays list of dishes from india with high spicy level
2. Use Case: Search for dessert recipes from italy
Description: User searches for dessert recipes from italy
Actor: User
Precondition: they should be logged in to the website
Steps:
Actor action: User view dessert recipes from italy
System Responses: list of dessert recipes from italy
Post Condition: system displays list of dessert recipes from Italy
3. Use Case: Search for fried rice recipes
Description: User searches for fried rice recipes
Actor: User
Precondition: they should be logged in to the website
Steps:
Actor action: User views fried rice recipes
System Responses: list of fried rice recipes
Post Condition: system displays list of fried rice recipes
4. Use Case: Search for tweets related to #chickenbiryani
Description: User views tweets related to #chickenbiryani
Actor: User
Precondition: they should be logged in to the website
Steps:
Actor action: User views tweets related to #chickenbiryani
System Responses: list of tweets related to #chickenbiryani
Post Condition: system displays list of tweets related to #chickenbiryani
5. Use Case: Search for most popular tweets by a chef
Description: User views most popular tweets by a chef
Actor: User
Precondition: they should be logged in to the website
Steps:
Actor action: User views most popular tweets by a chef
System Responses: User views most popular tweets by a chef
Post Condition: system displays list of popular tweets by a chef
SQL for USE CASES
1. SELECT * FROM recipe
WHERE spiciness = “Most Spicy” AND cuisine = “Indian Subcontinent”;
σ{spiciness = “Most Spicy” ∧ cuisine = “Indian Subcontinent”}(recipe)
2. SELECT * FROM recipe
WHERE spiciness = “Sweet”;
3. SELECT dish.recipe_id, dish.dish_name, recipe.ingredient_name
FROM dish, recipe
WHERE dish.dish_name = “%fried rice%” AND dish.recipe_id = recipe.recipe_id;
4. SELECT * from hashtag
WHERE keyword = “#chickenbiryani”;
5. SELECT * FROM checftweets
ORDER BY LIKES DESC;
RELATIONAL-ALGEBRA EXPRESSIONS FOR THE USE CASES
1. σspiciness = “Most Spicy” ∧ cuisine = “Indian Subcontinent” recipe
2. σspiciness = “Sweet” recipe
3. Π dish.recipe_id, dish.dish_name, recipe.ingredient_name σdish.dish_name = “%fried rice%” ∧ dish.recipe_id = recipe.recipe_id recipe
4. σkeyword = “#chickenbiryani” hashtag
5. σ keyword = “#chickenbiryani” hashtag
SQL for 7 questions
1. What user posted this tweet? SELECT username FROM tweets WHERE tweet_id = '1591501045959647232'; 2. When did the user post this tweet? SELECT created_at FROM tweets WHERE username= gordonramsay;
3. What tweets have this user posted in the past 24 hours? SELECT Tweet_text FROM twitterscraping.user WHERE Created_at > now() – interval 24 hour; 4. How many tweets have this user posted in the past 24 hours? SELECT count(text) FROM twitterscraping.user WHERE Created_at >= NOW() - interval 24 hour; 5. When did this user join Twitter? SELECT Joined_at FROM tweets WHERE screen_name = '1591501045959647232'; 6. What keywords/ hashtags are popular? SELECT * FROM twitterscraping.hashtags ORDER BY Tweet_Volume desc; 7. What tweets are popular? SELECT Tweet_text, Likes FROM twitterscraping.cheftweets ORDER BY Likes desc;
