---
title: "combine mp3 file"
date: 2009-09-16
forum: Multimedia Software
---

### Post by dave r on 2009-09-16
I have been looking to combine some mp3 files and have come across this
f your MP3's are all numerically named and zero padded (eg: 01.mp3, 02.mp3 etc) you can navigate to the directory
Code:
cd /path/to/directory
and combine them all at once with this command:
Code:
cat *.mp3 > joined.mp3
but cannot make it work, can someone explain it in plain english that someone new to the command line can understand or point me to somewhere that explains it simply.

---

### Post by dave r on 2009-09-16
OK lets get specific, what exactly does this line mean?
cd /path/to/directory
What do I use for path? What do I use for directory?
I have the MP3's in a folder called mp3s for joining, in a folder called temp tracks, in a folder called daves music box located in my home folder, how do I get to them using the first line?
With the second line
cat *.mp3 > joined.mp3
do I add it to the first line? do I use it after the first line has done its business?
I am confused and have a head full of questions, even though in all probability its dead easy

---

### Post by DaithiF on 2009-09-16
So, first step, you've opened a terminal, right?  (Accessories -> Terminal from the menu)
```
cd /path/to/directory
```
The cd command means 'change directory'.  When the terminal opens first you are located in your home directory.  That presumably isn't where your music files are, so you need to change to the directory where your music files are.  This may be something like Music/Albums/, or Music/mp3s, or whatever.
You should be able to figure out from your File Manager what location you need.  One point to note here -- you should probably enclose the path in double quotes, like:
cd "Music/Albums"
for example..., so that you don't need to worry about files or directories with spaces in their names, which might otherwise trip you up.

```
cat *.mp3 > joined.mp3
```
The cat command stands for 'concatenate', and it basically outputs the content of a file or files.  The '*.mp3' is an example of a 'wildcard', the '*' is a special character which says 'expand to list every possible file, so '*.mp3' results in a list of every mp3 file in this directory.  So cat *.mp3 says output the content of every mp3 file in this directory, and the '> joined.mp3' says take all that output and create a file called joined.mp3 from 
it.

what part hasn't worked for you?  post any errors that you get & we can help further.

---

### Post by DaithiF on 2009-09-16
I was writing mine while you posted your follow-up, but to answer your first question then ... your cd command will be:
```
cd "daves music box/temp tracks/mp3s"
```
so you type this in, and hit Return.  Note that these folder names are case-sensitive, so they need to match exactly, or you'll get an error like 'No such file or directory'

once that part has worked, then you enter the second command (and again hit return)
```
cat *.mp3 > joined.mp3
```
In the terminal you are nearly always doing things interactively one line at a time like this (except when you get to writing scripts!).  That is, you enter a command, it executes.  When its finished, then you enter your next command etc.

---

### Post by dave r on 2009-09-17
Thanks for the replies lads, I will have a play with it after I get home from work, I'm writing this at 5:40am.

---

### Post by dave r on 2009-09-17
:P Thanks for that DaithiF, it worked a treat, I have made a note of that so I don't forget.

---

