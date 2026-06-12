---
title: "how do i get checkmp3 package to fix mp3s recursively from a starting directory"
date: 2007-08-21
forum: Multimedia &amp; Video
---

### Post by kraymore on 2007-08-21
how do i get checkmp3 package to fix mp3s recursively from a starting directory ?

essentially my mp3s are in /home/user/music/album 1

and /home/user/music/album 2
/home/user/music/album 3  etc

how would i have checkmp3 correct the mp3s inside of /home/user/music

thank you

---

### Post by mohnkern on 2007-08-22
checkmp3 doesn't actuallly fix mp3's, however, if you want to recursively run checkmp3 on a series of directories:

find ./ -name \*.mp3 -exec checkmp3 {} \;

When you are in the top directory of your mp3's will run it.

---

### Post by kraymore on 2007-08-22
thank you so much

this command actually fixes mp3s

 To fix a broken mp3 run:

           $ checkmp3 -sf file.mp3 > fixed-file.mp3

i am wondering it you might consider adjusting your command line to reflect this from mp3s that need fixing ?

thank you so much.  i am not that adept at bash

---

### Post by mohnkern on 2007-08-23
This was the quick and dirty method:

From the Shell:

find ./ -name \*.mp3 > mp3list.txt


Then create the following perl script
------begin perl script ------
#!/usr/bin/perl
open (FRED, "./mp3list.txt");
while (<FRED>)
{
`checkmp3" -sf \"$_\" > \"$_.fixed.mp3\"`;
}

This does have the unfortunate problem of not handling question marks in file names well, and also it names files --- <originalfilename>.fixed.mp3  but it does make the corrections.

---

### Post by mohnkern on 2007-08-23
You could probably fix the file naming convention in the perl script with a split.  Something akin to:

@shortname=split(/./,$_);

and then change the section after the > where it checks to something like:


> $shortname[1]_fixed.mp3

Or something like that, you'd want to look and see how your find got structured first.

---

### Post by kraymore on 2007-08-23
i was able to create a mp3list.txt

could you kindly implement the shortname stuff in a perl or other script so i can have the .fixed files return to their original names ?  i dont know perl or bash all that well.

thank you

btw you said it depended on the output of mp3list.txt ?  one output of mine if it helps you is:

./music/New Order - Brotherhood/07 - All Day Long.mp3

this was done when the find string was run from /home/username 

would greatly appreciate your help.  

> **mohnkern said:**
> You could probably fix the file naming convention in the perl script with a split.  Something akin to:

@shortname=split(/./,$_);

and then change the section after the > where it checks to something like:


> $shortname[1]_fixed.mp3

Or something like that, you'd want to look and see how your find got structured first.

---

### Post by mohnkern on 2007-08-30
Sorry I haven't had time to work on this, I've been busy at work, getting the mp3 script to work the way you want may take some effort, I'll try to get to it in the next couple of weeks, or maybe someone else can take it from here.

---

