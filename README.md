java c
CSC108H Assignment 1: Wordlock 
Due Date:Wednesday September 25,2024 before 4:00 p.m
Wordlock: A Word Game In this assignment,you will write functions to implement a puzzle game that requires the player to use a number of simple moves to unscrambled a given word.The goal of the game is to discover the correct answer word.
Goals of this Assignment 
·Use  the Function Design Recipe (https:/lq.utoronto.calcourses/352998/files/32275858?wrap=1)  (https://q.utoronto.calcourses/352998/files/32275858/download?download_frd=1) to  plan,implement, and test functions.
·Write function  bodies  using  variables,numeric types,strings,and  conditional  statements.You can do this whole assignment with only the concepts from the Weeks 1,2,and 3 Prepare Exercises for CSC108.
·Learn to use  Python 3,Wing  101,provided  starter code,a checker module,and other tools.
The Wordlock Game 
Before you begin writing any code,you first need to understand the Wordlock game.Gameplay is described in the paragraphs below,so read carefully!
Game Mechanics
In the game,the player is presented with a scrambled version of the answer string.The answer string has been scrambled by first spliting it into sections,each having the same length,and then rearranging each section randomly,as in Figure 1.
Figure 1:Strings are scrambled in sections.

In Figure 1,the section'ROCK' has been scrambled to become'OCKR'and the section|'LAKE'has been
scrambled to become  EAKL' 
The sections in the string are numbered 1 to N,where N is the total number of sections.The section length is fixed for each run of the game,and every section will have the same length.For example,
consider   the   string 'treerocklake' and   a   section   length   of[4.There  are  3  sections  in  total  and  section  2
is  'rock 
The player's objective is to unscramble the string using as few moves as they can.The player has three   types of move available each turn:Check,Rotate,and Swap.Each move is applied to a single section of the string.We will use the phrase game state to refer to the current state of the string that the player is    trying to unscramble.
The   three    move   types:Check,Rotate,and    Swap
The Check move does not modify the game state.It is used to check if a given section of the game state has been correctly rearranged to match the corresponding section in the answer string.
The  Rotate  move  is  a  circular  Rotate  of  the  string  to  the   right,which   means  each  character  is  moved  one position to the right and the last character is moved to the front.For example,the second last character   of the section becomes the last character of the section in the new game state,and the last character
before the rotate is moved to be at the beginning of the section.
In the Swap move,the first and last characters of the section are exchanged in the game state.
The Rotate and Swap moves are illustrated in the figure below. 

The   three   modes   of   gameplay:Test,Normal,and   Hint
The game allows for 3 modes of play:Test,Normal,and Hint.Enabling Test mode allows the player to set the correct answer and the number of sections before the game begins.(Otherwise,the player is presented with a scrambled word and told the section size.)Normal mode involves playing the game as we have described above.Hint mode provides one additional move that allows the player to receive hints  on  which  sections  and  moves  to  choose  each  round.
Gameplay 
When the game begins,the player is first asked to choose a game mode.Then,the player is repeatedly asked to provide both:
1.The section number corresponding to the section they want to manipulate.(A string with N sections will have its sections numbered 1 to N.)
2.The move they would like to apply to the section.
If the player is playing in Hint mode,they will be offered the chance to get a hint for a section to choose,
or a move to make on a particular section.Getting a hint counts towards the player's total number of moves.
The game continues until the player has completely unscrambled the string and discovered the answer string.When the game is over,the player's total number of moves代 写CSC108H Assignment 1: WordlockPython
代做程序编程语言 is reported.
Here is a video of the game being played (note that the video is difficult to see unless you watch it in the highest quality,use the settings gear and set the video quality to the highest number of kbps):

Files to Download 
Click here to download the Assianment 1 Files (https://a.utoronto.ca/courses/352998/files/33105723? wrap=1)_山 (https://q.utoronto.calcourses/352998/files/33105723/download?download_frd=1),and  then    extract the zip file.The following paragraphs explain the files you have been given.
Starter code: wordlock functions.py This file contains some constants,and a complete docstring (but not body!)for the first function you are  to write.You will update this file to include the complete functions that you write.This is the only file you will submit for grading.
Main program code: wordlock game.py 
This file contains the main program code for playing the game.When it is run,the functions that you
wrote and put in the wordlock functions.py file will be called.When you have written all of the functions in wordlock functions.py ,you may play the full game by running wordlock game.py].You can further test your   code by running in Test mode where you are prompted for the ANSWER and SECTION LENGTH] that the game  should use.Do NOT make any changes to the wordlock game.py file,as you will  not submit this file.We    do not expect you to understand all of the code in this file at this point in the course.
Checker: a1 checker.py      checker generic.py   and  al   pyta.json
These files provide a checker program that you should use to perform. a simple test of your code.See   below in the section called CSC108 A1 Checker for more information about a1 checker.py].The   checker program requires the files checker generic.py and  a1 pyta.json]. You do not need to do anything with
these files,other than keep them all in the same folder as your wordlock functions.py and wordlock game.py file.
What to do 
In  the  starter  code  file wordlock functions.py ,complete  the  functions   as   described  in  the  table   below.Use
the Function     Design      Recipe      (https://g,utoronto.calcourses/352998/files/32275858?wrap=1)↓
(https://q.utoronto.calcourses/352998/files/32275858/download?download_frd=1)       that   we have    been learning  in  class,and  write  complete  docstrings  for  each  function.
Using Constants 
The starter code in wordlock functions.py starts with the definition of some constants.Your code should make use of these provided constants.If the value of one of those constants were changed,and your
program rerun,your functions should work with those new values.We will test your code using different   values for the various moves and modes by updating the values of the constants -your code should sill  work with these updated values!The one exception to this is the constant HINT MoDE SECTION LENGTH].This   constant will always be set to 3 and your functions only need to work for this value.(We are constraining this value in order to make the assignment difficulty level appropriate for this stage in the course.)
Your docstring examples can use the values of the constants in the provided starter code,and do not need to changeif we change the values of the constants.
Students often choose to use the literal values of constants when references to the constants should be used instead.If you are confused about the difference,look into Piazza or come in to office hours!
Preconditions 
When writing your functions,you may always assume that:1.the game state is a valid scrambling of the answer,and 2.both the game state and answer can be evenly split into sections with the given section    length.Yo u must not make any other assumptions other than this and what is given in the table below for each function.For example,you must not assume all characters are uppercase.
Regarding preconditions:1.You do not have to write any of the preconditions into the docstrings for this assignment,and 2.You can not assume any preconditions other than what we already mention about    the type contracts and parameters in the table below.





         
加QQ：99515681  WX：codinghelp
