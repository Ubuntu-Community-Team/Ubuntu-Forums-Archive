---
title: "Primus does not use Nvidia GFX"
date: 2013-05-30
forum: Multimedia Software
---

### Post by YongQing on 2013-05-30
Hi all

I've run into a bit of a problem with getting Primus to work. Primus installs fine. The problem is, using the command "primusrun glxspheres", the program does not use my nvidia graphics card. It defaults to the onboard graphics.

This is what I get when I use "primusrun glxspheres"
[IMG]http://i2.minus.com/i2X5zbq5hh6n7.png[/IMG]

This is what I get when I use "vblank_mode=0 primusrun glxspheres"
[IMG]http://i.minus.com/ibmNub7myfZHZH.png[/IMG]

Notice how in both cases, the Intel onboard graphics is used

Now, if I use "optirun glxspheres", I get this
[IMG]http://i.minus.com/ibh7E5GMJTDqVi.png[/IMG]
So, optirun would use my NVIDIA graphics but for some reason primusrun wouldn't

I'm using Xubuntu 13.04 64 bit
I need to get this to work because I'm having trouble playing L4D2 on my machine. (Here's a dump of the log when I try "primusrun steam": [http://pastebin.com/hEhm9mdd](http://pastebin.com/hEhm9mdd))

---

### Post by Perfect Storm on 2013-05-31
Moved to Multimedia & Video.

---

### Post by YongQing on 2013-05-31
Help plsss =(

---

### Post by YongQing on 2013-06-06
I read on WebUpd8 that 64-bit OS users need to install an i386 package.
I installed that but primusrun still defaults to the onboard graphics.

Help please!!!

---

