---
title: "Problem using Brasero to copy CD"
date: 2012-04-03
forum: Multimedia Software
---

### Post by johnnydoe on 2012-04-03
I am getting an error while trying to make a copy of a CD that holds medical images.  I get this error when trying to burn the image to a file or to another CD in waiting.  I am using Brasero 2.30.2 I am getting this error.

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1741)
Unsupported type of task operation
Session error : An internal error occurred (brasero_burn_record brasero-burn.c:2839)
```When trying to make a copy to an image file, I am getting this error.

```
Please install the following manually and try again:
toc2cue (application)
cdrdao (application).
```Should I use another program, or is it possible this is protected with DRM or something, and if so what should I do?

---

### Post by jerrrys on 2012-04-03
Its just asking that two packages be installed, but [FONT=monospace]toc[/FONT]2cue can be problematic.

[https://www.google.com/search?client=ubuntu&channel=fs&q=toc2cue&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=toc2cue&ie=utf-8&oe=utf-8)

An alternative would be to use k3b.

[http://sourceforge.net/projects/k3b/](http://sourceforge.net/projects/k3b/)

Its in the software center or in terminal enter:

sudo apt-get install k3b

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by johnnydoe on 2012-04-03
Thanks.  I am still having problems with k3b.  The CD uses some .exe programs to autorun when the user inserts the CD, so I thought I should make an image of that CD so I do not distort anything.  I tried "copying medium" and making a data copy, but those did not work.  

I think I want to make an ISO of the original and then burn it to another CD, but it asks me for the source image file, but one does not exist at the moment.  The CD just has several folders and a couple of .exe programs.

---

### Post by robert shearer on 2012-04-04
Brasero can be a right pain and it has never copied a disc for me.
The best I can get is to open the source disc and copy the contents to a folder on the hard drive then insert a blank cd, start Brasero and burn the folder to cd.

---

