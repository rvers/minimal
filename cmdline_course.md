---
layout: default
---
# Command-line course
In this course the student would learn:
*operate in a Unix-like environment.
*use Unix command-line on a Windows or Mac OSX computer.
*use the Unix command-line.
*use regular expressions.
*processing corpora at a basic level.
*run programs from the command-line.
*install programs.
*write basic scripts.
*use version control tools.
*work on a remote server
This course was an online course with optional workshop classes.


## Introduction to Command-Line Environments
This week we learned the basics of unix environment - how to move from directory to directory and how to create new directories etc.
This week I got comfortable with unix and with using different shells in terminal and using different editors such as nano and to understand different file types. 
! [alt text](assets/img/Binary_executable_file2.png)


## Navigating a UNIX System
In this week got familiarized even more with unix environment. We learned that chmod changes acess persmissions and sudo that lets us commit commands as another user, usually the root user.
They are convenient when working in different shells. We also read about ssh and scp. Ssh is a  is a secure connection protocol over which we can connect to a remote server.
But ssh can't copy files over the ssh connetctions thats why we need scp that copies things from remote servers and vice versa.

## Corpus processing
This week we learned to work with tools such as regex to help us search and process large amounts of text. We also had a look of character encodings and character sets.
Regex is a very powerful tool that allows us to search very specific patterns from large amounts of text. In this week I learned to manually sort alphabetically and count the frequencies 
of the concordances appearing in the corpora. We also used sed that is used to edit text:
cat life_of_bee.sent | sed -E 's/.* //' | tr -cd "A-Za-z0-9\n'" | sort | uniq -c | sort -nr | head -1
In this commmand we have a file where every sentence of a book is on it's own line and with sed we remove every other word than the last of the sentece.
then we remove the punctuation and finally count and sort the data to get the most used last word of the book. 

## Installing and Running Programs
In this week we learned to install programs and also to use  pakage managers for installing them. 
We also used make and made makefiles to process corpora. For me this week was interesting because of the makefiles. 
Make turned out to be a very powerful and timesaving tool to process and edit corpora. If a week before we did everything manually with a makefile
we could do a file that has all the commands and when we run it for many different data it will sort the corpora automatically using the commands in
the makefile.
Here's a example of a makefile code that removes metatexts, counts all of the concordance frequencies and sorts the data a sentence per line:

>BOOKS=ulysses  dracula frankenstein
>
>FREQLISTS=$(BOOKS:%=results/%.freq.txt)
>SENTEDBOOKS=$(BOOKS:%=results/%.sent.txt)
>
>all: $(FREQLISTS) $(SENTEDBOOKS)
>
>clean:
>	rm -f results/* data/*no_md.txt
>
>%.no_md.txt: %.txt
>	python3 src/remove_gutenberg_metadata.py $< $@
>
>results/%.freq.txt: data/%.no_md.txt 
>	src/freqlist.sh $< $@
>
>results/%.sent.txt: data/%.no_md.txt
>	src/sent_per_line.sh $< $@ 



## Version Control
This week we familiarized ourselves with github that is a online hosting-service for version control. Version control means the tracking of changes in a large program, document or other collections of information. 
It is good to keep track of versions because for example in computer programs a small change can create a bug and for this humans must be able to track down the different versions and changes for everything to run smoothly.
We also learned to use repositories that are sort of the directories where all the current data and the history data is. Repositories can be cloned so that they can be modified without the master brach being changed.
We did a little project which you can see [here](https://github.com/rvers/cmdline-course)




