---
title: "Failed to start the Xserver"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by bharathyd on 2007-08-17
Hello friends

I am using UBUNTU distribution of LINUX from the past 1 month

Now I am facing a problem and I actually tried to solve it out byseeing the threads but i couldnt do it

Can any one please help...the problem is...
When I am starting the system Im seeing this error message
**Failed to start the Xserver (your graphical interface). It is likely that it is not setup correctly. Would you like to view the X-server output to diagnoise the problem**

<YES>      <NO>

then i clicked YES, its showing

**X: cannot stat /tmp/.X11-unix (Permission denied),aborting**


Can any one please help me what to do.....

---

### Post by archangel1701 on 2007-08-17
hi im having the same problem with my nvidia 8800gts it is driving me crazy:confused: I wish there was someone to help

---

### Post by ZipoTe on 2007-08-17
what kind of video card have you got?

---

### Post by archangel1701 on 2007-08-17
nvidia 8800gts

---

### Post by ZipoTe on 2007-08-17
> **archangel1701 said:**
> nvidia 8800gts

I was asking to **bharathyd** :-P
About you,archangel1701, ... I think i answered a post you made about some nvidia problem, didn't I?

---

### Post by archangel1701 on 2007-08-17
hey i told you i was desperate but it didnt work:lolflag:

---

### Post by bharathyd on 2007-08-17
heyy first of all i thank u for replying


My mother boards name is VIA

and I have a slot for keeping a graphics card but i dont have that

by the way 

my mother board driver name is SAVAGE

---

### Post by ZipoTe on 2007-08-17
Did this problem appear after an update? If yes, what did you update?

---

### Post by bharathyd on 2007-08-17
Heyy to be clear ....my system worked normally as usual upto yesterday

While I was playing A game called PLANETS PENGUIN RACER...some body pinged me through GAIM
and suddenly my system got struck. When I restarted ...I got this problem

I am now running through DEBIAN which i already have as dual boot.
Now thing peculiar I observed is while accesing the UBUNTU file system I cannot see /tmp folder
but a file named tmp is there but im unable to access it.

By seeing some posts in forum regarding Xserver error
I tried thsi command through root in the terminal window

dpkg-reconfigure xserver-xorg  ...and there is no use of it

then i did  root@ubunsys# vi /etc/X11/xorg.conf

and i changed graphics driver to vesa instead of savage.... and then did gdm restart
then also there is no use.

---

