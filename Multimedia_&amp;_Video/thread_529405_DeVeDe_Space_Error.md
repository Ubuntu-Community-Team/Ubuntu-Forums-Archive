---
title: "DeVeDe Space Error"
date: 2007-08-19
forum: Multimedia &amp; Video
---

### Post by HwH on 2007-08-19
For some reason when i try to create a DVD disk structure with DeVeDe i get this error:

> Failed to create the DVD tree
Maybe you ran out of disk space

I have checked and i dont see how it can be a space problem, because im trying to make a DVD on a 4.7gb DVD disk and i have 16.2gb free in /home where im trying to create the DVD tree.

Does anyone know if DeVeDe tries to create temporary files somewhere  and if i might need to make more space there?

Or if this is not the problem anyone know what the problem is?


Thanks in advance for any help.

---

### Post by ulpiano on 2007-08-19
I have the same problem. I'm trying to convert an .avi file to DVD playable in any DVD home player and DEVEDE fails when it finishes the conversion .avi to .mpeg. The error message is exactly the same. I've been looking for the problem. My .avi file weighs 700Mb aprox.Will it be the problem? I don't understand, I have enough disk space to complete the process. I will continue looking for the answer.
PD: Sorry, my English is bad...

---

### Post by pizpot on 2007-11-28
I notice that there is a .devede file in my home folder with only two lines:

video_format:ntsc
temp_folder:/var/tmp/

I did have 30 GB free but I guess its not enough. So, I changed the 2nd line to point to a bigger drive like this:

temp_folder:/media/hda4/devede_temp/

and I am willing to bet my problems are over. I have 125 GB free there. It probably matters that you have a / at the end of that line, like it had before I edited it, eh.

Say no to war, and stick your yellow ribbon up the old oak tree....

---

### Post by funkythumb on 2008-01-01
Any updates on the space issue? I get the same error message - so I modified my .devede to point to my 1.3TB volume, with over 700GB of free space. Still get same message complaining about space.

I'm only creating a 1.8GB dvd, so I'm baffled why it stops just shy of finishing the directory structure (where all of the mpg files **are** created) and making the final iso image.

Help...!

---

### Post by pizpot on 2008-01-29
The solution is actually funny. Don't use a fat32 partition for the output file. It's funny because devede says not to do so when it asks you for the output folder. Fat32 can only do 4GB files and a dvd is bigger than that, it is 4 and a half. :-)

---

### Post by afkaos on 2008-06-12
I'm getting the same problem, but I'm using an EXT3 formatted drive, so that's confusing me..

---

