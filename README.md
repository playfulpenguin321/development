# Development

### Link to Deployed Website
https://playfulpenguin321.github.io/development

### Goal and Value of the Application
My application is a checklist for users to keep track of books that they have read. This checklist specifically includes entries from a collection of Star Wars novels, however in general I believe my site is a good foundation for larger collections of novels that can help avid readers keep track of their progress. I have included multiple sorting and filtering options that allow a user to conveniently find books from specific authors, eras and series. Also included is an aggregator that tallies up the number of pages a user has read based on what they add to their "checked" book list. Due to time, I was not able to include descriptions for each of these books, which both experts and newcomers to Star Wars books would find useful. Overall, I believe this application works well as both a source of information to learn about these novels as well as an efficient tracker for how much a user has read over time.

### Usability Principles Considered
Learnability: The checklist is set up in a fairly intuitive manner, displaying books and their information within a grid of boxes. The information is displayed with high color contrasts for clear readability. Using checkboxes as the primary interaction for adding/removing to the checklist, as well as choosing filters/sorts, is a simple yet effective way to convey to new users how they can manipulate the information that is displayed.

Memorability: There are no dynamic components to this site and users can always expect to find the same functionality every time they return to this site. Knowing how to use the checkboxes and the filters should be a fairly simple task to remember. 

Efficiency: Users who are familiar with checklists will find it convenient to narrow down a long set of books to a smaller selection via stacking of filters and sorts. The task itself is done very quickly and mistakes can be undone at the click of a button. Having a reset button is also convenient for quickly reverting the site to its original state. 

### Organization of Components

My application is broken down into the following:
- The data (in data.js) that contains all of the information that will be displayed for each book. This information is used to filter books out into different groups.
- BookItem.js comprises my "item component". It is here that the information from data.js is organized into a readable and comprehensive grid unit. A handler is passed in for each BookItem such that, when the checkbox is clicked on for a book, the page count aggregator gets updated and the book is added into the checklist set.
- App.js is where the majority of the logic takes place. Here there are functions that will display the sidebar of sorting and filtering options as well as the state handlers that update the display of books based on what the user clicks on. 

### How Data is Passed Down Through Components

There is only one case where information is passed from one file to another. This occurs in the "return" section of my App function where I map every book from the current state's set of books onto a grid. As mentioned above, every book item is passed in a handler that is paired up with a checkbox input such that it will update the page count and checklist set. 

Within App.js, data is passed frequently between functions and handlers to update information instanteneously with each user input. The most notable function is the sortAndFilter function which takes in several props: a book set (books), a filter set (filters), a checklist set (bRead), and some booleans (nSort, aSort, checked). Passsing all of this information in at once allows me to perform a series of calls to .sort and .filter, depending on what is currently 'active', to then return a new set of books that will replace the current state's book set. 

Another frequent data pass occurs with the onChange feature of the checkbox input. This is discussed in the section below. 

### How the User Triggers State Changes

All changes in states occur when the user decides to check or uncheck a box. There are four different assignments of checkboxes present throughout the site: 1) sorting, 2) filtering, 3) displaying checklist items and 4) adding/removing books to the checklist. For each of these actions, I have written out some const handler that makes use of React states to update information that is shared between all componentes of the App. 

I had to ensure that books that had been checked would remain checked even if a filter caused the book to disappear from display. This was the foundation for my boolean state structure in which I use the onChange event of the checkboxes to update booleans representing what filters/sorts are triggered. This made it easy to then call a sort and filter function without encountering conflicts of what was and wasn't checked. 

One last important state change is the handleReset const that I represent as a button on the screen. This triggers all the useState declarations I have such that we return to the original state of the site. This also triggers a forEach loop on all of the 'checked' booleans of the checkboxes to return to false so nothing is checked once reset. 

