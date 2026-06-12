---
title: "ATI graphic card and xorg related issue"
date: 2007-05-28
forum: Multimedia &amp; Video
---

### Post by xanvier on 2007-05-28
Greetings,

i'm pretty new to Linux scene. Therefore recently, when i did some modification to the xorg.conf file and saved it, the next restart i did made my PC unsuable because the xorg server thingy can't start. 

So can anyone tell me what is the exact command to somehow go into their DOS and access the xorg.conf file and delete extra lines i inserted?

Next up, is this the correct way of installing a ATI AGP graphic card? I followed the steps indicated on this page - [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

However i am confused, do i have to put in the ATI graphic card into the AGP slot first then boot it up, after which then continue with the instruction on the wiki page above?

Please enlighten me! Thank you!

---

### Post by frozinfire on 2007-05-29
From the command line, try:
sudo nano -w /etc/X11/xorg.conf

---

### Post by xanvier on 2007-05-29
Oh ya, i'm using Xubuntu by the way. So i hope nano is available?

---

### Post by sloggerkhan on 2007-05-29
Nano should be there.

---

### Post by frozinfire on 2007-05-29
Oh, and about that installation guide ... it seems okay, although a bit dense. It'd be unfortunate if you had to use method 2, but hopefully you'll just need to grab the fglrx driver. I see that it suggests editing the xorg.conf file; did you run into trouble with that? I just did "sudo dpkg-reconfigure xserver-xorg" and manually changed the driver to fglrx. If that driver's screwing up your display, though, you could just leave it at "vesa" or whatever.

---

### Post by eye208 on 2007-05-29
I recommend using the new restricted drivers manager to install the ATI driver, especially if you are new to Linux.

---

