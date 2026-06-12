---
title: "[SOLVED] Anyone here familiar with dBpoweramp Music Converter?"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by bobleny on 2007-08-14
Anyone here familiar with dBpoweramp Music Converter?

It is a windows program that has two VERY important features to me. First, it can convert music files (Thats the easy one).....  Second, it can strip the files of there ID tags!

I'm finding it difficult to get a Linux based program that can do that. Most people want ID tags, so most music converters preserve the ID tags.... I don't want them....

Anyone know of a program that can do this?

Thanks!

---

### Post by RudolfMDLT on 2007-08-14
Hi there,

Try eyeD3 - it's command based but very effective.

to install it -** sudo apt-get install eyed3**

Here is an example on how to use it. To remove all info from the IDE tag, effectively removing the tag just type in this:

eyeD3 --remove-all /stuff/Kelly\ \ Clarkson\ -\ My\ December/

where /stuff/FOLDER/FOLDER is the folder that contains your mp3's. If you have, like ne, spaces in your file names, just start typing the first 2 or 3 letters of the path and press TAB once or twice to complete the entire folder path.

Goodluck!

---

### Post by benerivo on 2007-08-14
How about exfalso?

---

### Post by bobleny on 2007-08-14
Perfect, eyed3 works perfectly!

Thanks!

---

### Post by RudolfMDLT on 2007-08-14
:popcorn: Cool! just for interest sake - why would you want to get rid of the Tags?

Please mark the thread resolved by clicking on the thread tools button.

---

### Post by bobleny on 2007-08-14
Most of the music I have is downloaded. Often times i get stupid comments and stupid tag info. So when I put it on my Ipod, it does stupid things with the songs... I don't like it when stupid programs such as Itunes, do stupid things with my music files...

In general, I would rather just not have tags, then edit 1,000 plus songs...

Ok, Topic solved!

---

