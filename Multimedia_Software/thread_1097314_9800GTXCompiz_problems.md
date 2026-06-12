---
title: "9800GTX/Compiz problems"
date: 2009-03-15
forum: Multimedia Software
---

### Post by dhysk on 2009-03-15
Ok, I think it may be more of a refresh issue but here is the problem.  Every so often I especially when typing the video doesn't seem to keep up with what I'm doing.  For instance I'll be typing something like this line and it will look like this.

Forinstance ill be type |||.  

then when i move the window it will look correct.  Kinda like on old computers when you type to fast and it couldn't catch up.  Also when I'm on the menus and move the mouse from one object to another multiple things will appear to be highlighted. (see attached photo) 

The later problem I don't care much about however I think its the same thing.  The only thing that bothers me is when I'm typing and I cant see it.  It's really bad when I try to edit because I cant tell if I deleted the item already or not... URG....

---

### Post by RedRat on 2009-03-15
How much memory do you have and what video driver are you using? How do the other compiz effects work for you, e.g., the cube, and desktop effects? What version of Ubuntu are you running?

---

### Post by dhysk on 2009-03-15
sorry how newbish of me...

Ubuntu 8.04
Nvidia's 180.29 driver, was using .22 and just installed .29 didn't help/hurt any.

GFroce 9800GTX+ 512Mb Ram 256-bit PCIe x16
4 GB of system ram

All other effects work great.  Cube, transparency, 3D games such as TC:E and astromenace are flawless.  I can even run half life windowed threw wine with no problems.  just this refresh thing that makes it realy hard to type and chat.

---

### Post by RedRat on 2009-03-16
> **dhysk said:**
> sorry how newbish of me...

Ubuntu 8.04
Nvidia's 180.29 driver, was using .22 and just installed .29 didn't help/hurt any.

GFroce 9800GTX+ 512Mb Ram 256-bit PCIe x16
4 GB of system ram

All other effects work great.  Cube, transparency, 3D games such as TC:E and astromenace are flawless.  I can even run half life windowed threw wine with no problems.  just this refresh thing that makes it realy hard to type and chat.

I think it might be a site problem because you have all things going for you. I notice that when I blog on some sites that have "comment windows" (much like here) I also get that poor response, e.g., Washington Post. What I do to circumvent that is to type my responses into my text editor (gedit) and then just copy&paste it into the comment box. 

Not all sites are that bad, e.g., this one for Ubuntu forums seems to work fairly well. However, early on (several months ago) it too was slow. So I suspect that it is just site dependent.

Do you have problems like that with say OpenOffice word processor or gedit?? Is it only like that using Firefox or some other browser?

---

### Post by dhysk on 2009-03-16
Ya it still happens with OpenOffice, thats why i think its a video problem.  Another example is with taped windows(firefox or in a tabbed shell) when i switch to tab #2 it still displays tab #1 untill i move the window, then it refreshes the window.  It's all a bit irratating realy.

---

### Post by RedRat on 2009-03-16
> **dhysk said:**
> Ya it still happens with OpenOffice, thats why i think its a video problem.  Another example is with taped windows(firefox or in a tabbed shell) when i switch to tab #2 it still displays tab #1 untill i move the window, then it refreshes the window.  It's all a bit irratating realy.
You know, I noticed that you are using the 180 NVidia driver and the 9600 card series. I don't know if this will work but you could try falling back to the older driver, I think it is 170 version. 

I hesitate to suggest this (it may not be possible) because fooling around with these video drivers in Ubuntu brings on a lot frustration and annoyances. But if you feel confident, you might try that. I have seen here and in the newsgroups some problems with the latest 180 drivers. It may not solve your problem, but sometimes these drivers get ahead of the curve and can create problems.

Oh, BTW, you might want to check your monitor sync rate too, while you are at it. You can do that by running:
gksudo nvidia-settings

Note that you need to run using gksudo or sudo otherwise if you make any changes, it doesn't "take".

---

