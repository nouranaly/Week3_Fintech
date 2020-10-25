# Week 3-Fintech
## Day 11: APIs
#### Overview
**Students will be able to** 
- Explain what an API is 
- Go to a developers website for an API and get a Key
- Retrieve data by making GET requests to a specified endpoint 
- Make a request with parameters
- Parse through JSON responses (lists and dictionaries) from an API
- Explore data structure to isolate the elements that you want and build an API/Flask App

### Intro 
**Framing**

At the start of instruction frame for students that some of them may have worked with APIs before and for others, today will be their first day! For that purpose, API play time will give everyone a chance to explore APIs and build something new that they have not tried before. Expect that students will be at different levels today and be willing to provide the space for them to choose their own route for how they want to build and play with APIs. 

**What is an API**

An API is an *application programming interface*. It refers to connection points between 2 entities of code. Think of it as a set of rules that allows programs to talk to each other. Computer programs frequently need to communicate amongst themselves and APIs are one way they do that. Every time you go online shopping, browse a social media app, play a game on your smartphone, or visit a page online, you’re interacting with an API. A more specific example is when you’re listening to music on Spotify, the music playing application on Spotify communicated with your systems API in order to send music to your speaker. 

To use an API, you make a request to a remote web server and retrieve the data you need. 

**But why use an API?**

It’s worth taking time in the beginning of class to have students construct their own understanding of why APIs are useful. 
Before heading into the Giphy API Lab, have students go through the process of building a program that returns a gif based on the users query **WITHOUT** the use of an api.  

**To Get Started**

1. Clone the Giphy API Lab: (modify the flask-api template to a giphy api) 
2. Flask Run. 

**Questions for Students**
- Have students search for a “cat” gif and ask them what was the result of their search. Then have them search for a “koala” gif and ask them what was the result of that search 
- Ask students to explore the program and try to uncover why they received a gif for cat but not koala. Ask students to put a green check mark once they feel that they have uncovered why. *(Provide a hint halfway during wait time, directing students to the model.py file.)* 
- Once all students have their attention on the getImageUrlFrom function,  ask students what can a user search up and have a gif returned to them and where are those gifs stored?

At this point, students understand that only two gifs have been manually stored in the program, and if the program was to respond to more queries, then more gifs need to be uploaded in the images file. 

#### Time for the pain point: Challenge students to return a gif for as many animals from the list below as they possibly can in 10 min.
- Llama
- Chipmunk
- Alpaca
- Raccoon
- Hippo
- Koala
- Penguin
- Panda
- Rabbit
- Piglet
- Goat 

**Reflection:** as students return from the challenge have them reflect on their experience of what it was like searching, uploading and returning a gif for all the animals on the list and to try to imagine what it would it would be like if they were tasked with an even larger list or other categories that someone can possibly search for. 

**Take-away:** reveal to students that the hard work of compiling large data sets is already taken care of through APIs. While this process was made to be intentionally painful, it will pave the way for their understanding of why APIs provide a much more seamless and efficient way to request and retrieve data from data bases that have already been created.  

--- 
### Giphy API Lab 
As you head into lab time, have students select from the following two options based on their preference: 
* **Option 1:** If this is their first time working with APIs, provide them the option of doing the Giphy API Lab as a code-along with a teacher
* **Option 2:** Students who are comfortable working with APIs can opt into completing the Giphy API Lab with a partner in a separate breakout room. 

**The Goal**: We’re going to build a Flask app using the Giphy API. When it’s finished it will look something like this: 

![Gifbot](https://media.giphy.com/media/NPdrfe4ox96zm8QCMW/giphy.gif)

We're going to write a program to asks the user what kind of gif they would like to see and return a gif based on the user’s request. 

#### Part 1: Getting Started
- Go to developer.giphy.com 
- Sign up for a developers key
- Clone the flask API template:(https://github.com/upperlinecode/Flask-API-Template) 
- Flask run 

#### Part 2: Create a route for yourgif.html page 
- Try submitting something in the form, figure out why it doesn’t work!
- Create a route for (‘/yourgif’, methods=[‘GET’, ‘POST’]), which returns any text for now ex: “Yay” 
- After confirming that your route works, render_template the yourgif.html page instead of the text. 

#### Part 3: Write the API request
- Go to https://developers.giphy.com/explorer
- Choose an endpoint (you probably want “search”) 
- Copy the URL
- Go to the model.py file, create a variable called “endpoint” that stores your URL as a string inside the function *getImageUrlFrom*
- Create a variable called “response” where the data from your URL will be stored and convert it to a JSON to view the data as a python dictionary 
   response = requests.get(endpoint).json( ) 
- Add: print(response) to the end of the *getImageUrlFrom* function to view the data from your search 

#### Part 4: Retrieve and request data for your query 
- In app.py uncomment from model import *getImageUrlFrom*
- In  the yourgif route, add image = getImageUrlFrom(“pugs”) 
- Make sure you import requests in model.py
- Run the program and make sure it works- if you search for pugs, the program should print the data from your query in your terminal.

#### Part 5: Parse and narrow down your response 
- Open the response in your browser. Use JSONView or similar extension to figure out your data structure 
- Your first key is “data”.  Keep digging to find the specific data elements you want.  Try to specify the response in model.py to print the fixed height images.

#### Part 6: Return the data to the user 
- Rather than print, Return the data element you want in your *getImageUrlFrom* function 
- In app.py set image=image in your render_template
- Display the image from your query in yourgif.html,  <img src=”{{ image }}” />
- Flask run to make sure it works before moving on 

#### Part 7: Respond to different user queries 
- Now, what happens if you request a cat gif?
- In the yourgif route, create a variable called query that takes in the user’s query from the form in index.html   
- In app.py, replace “pugs” with “query” in your route
- In model.py replace “pugs” with “query” using string formatting endpoint = f”...{query}...”







