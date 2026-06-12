---
title: "Matrox P650 help request!"
date: 2006-01-07
forum: Multimedia &amp; Video
---

### Post by Makrie on 2006-01-07
Hi

I'm having trouble getting my Matrox P650 working. 

When I plug the card in, everything loads okay until it tries to start the X server (I think) when it kicks me out to the command line.

I've read the reasdme and the driver doesn't seem to be installing correctly, though even once it is installed, I expect I'll still be uncertain as to what to do...

At the moment the card is out of the computer, enabling me to write this by plugging in through my other graphics card.

Any help appreciated!

Thanks

Mark

---

### Post by Makrie on 2006-01-09
Okay... the key is to use the VESA driver when reconfiguring xserver-xorg... then you can access the desktop and use firefox to visit the matrox site to download the drivers you need... i think... 

I'm gonna work on installing the matrox drivers over the course of this week.

cheers!

---

### Post by nespa on 2006-01-12
If I understand correctly, the closed-source matrox driver doesn't even work on a 64bit machine :confused:

:arrow: I wonder how far one will get with the vesa-driver ( resolution, coulour depth, speed/fps )?
:arrow: ( linux32 or chroot 32 bit ) the xorg environment, can it be done?

---

### Post by drucer on 2006-04-05
Guys, we need to make some noise! Let's each post a message on Matrox Technical Support Forum and request more frequent updates to Matrox Linux drivers! They could even open source their drivers - that way we would have constant up to date Matrox drivers.

[http://forum.matrox.com/mga/viewforum.php?f=2](http://forum.matrox.com/mga/viewforum.php?f=2)

Some Matrox P650/750 or later users might find help by using unofficial drivers you can download here (these drivers are contributed by some Linux guy, who is a regular contributor on official Matrox Linux forums - I suppose he has access to Matrox Linux driver source):

[http://www.tuxx-home.at/archives/cat_2/](http://www.tuxx-home.at/archives/cat_2/)

I downloaded the 1.4.3.4 version of the driver and it compiled nicely and works fine with x.org 6.9.0. I have 32bit system, so I have no idea if it will work with 64bit systems.

---

### Post by nespa on 2006-07-21
round 15 jul 2006 matrox release a closed-source driver 1.4.4  ... 64bit at last!

---

