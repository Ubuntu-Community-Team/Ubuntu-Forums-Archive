---
title: "Mythtv video issue"
date: 2009-07-03
forum: Multimedia Software
---

### Post by David Starling on 2009-07-03
I recently made the switch to Ubuntu 9.04 from Windows XP. My hardware:

Intel Core 2 Duo 2.13 GHz
2 GB RAM
20" 1680 x 1050 LCD (DVI)
ATI X1650
WinTV-PVR USB2

So, I installed Mythtv (front-end) via synaptic and when I go to load it, the screen just totally messes up. It basically shows my desktop with a black rectangle in the middle of the screen. The application is nearly full-screen, so I can't click on the other windows (the mouse cursor is invisible), but I can access the task bar at the top (the mouse becomes visible here), and the dock below.

Any idea what's going on? Thanks!

---

### Post by David Starling on 2009-07-03
Here is a screen shot: 

[IMG]http://i946.photobucket.com/albums/ad308/david-starling/Mythtv.png[/IMG]

---

### Post by jasonsjunk on 2009-07-03
MythTv requires a frontend and a backend.  In the setup you can run mythtv in a window so its easy to minimize and you can access your desktop.  I believe the option to run it in a window is in the frontend setup but you will need to get the backend working first.  

Here are some good links to help you get things setup.

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)
[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by David Starling on 2009-07-04
I followed these instructions (2nd link), but have the same result. The mythtv-setup produces the same black rectangle as mythtv itself. Short of installing mythbuntu, not sure what I could do differently.

---

### Post by fbugnon on 2009-07-18
I'm experiencing the same problem here on a fresh and updated install of Ubuntu 9.04 x86_64.

First I just installed the Mythtv-Frontback-End (sypactics manager) and after reading this post I also installed the rest of it with command-line *aptitude install mythtv*.

I have tried to run the Backend Setup couple of times, but I have the same strange black rectangle plus a terminal that pop-up but is sort of hidden by the rectangle so I can't see what's going on.

___________________________________________
HP Pavilion a1130n
AMD Athlon 64 Processor +3500
Ubuntu 9.04 x86_64 Kernel 2.6.28-13-generic

---

### Post by mmstahlman on 2009-10-01
Same issue here.

I installed Ubuntu 9.04 and installed MythTV via Synaptic.

I would bet the problem is with the video drivers.  I have an X1050 ATI card and other stuff seems to work but Ubuntu 9.04 does not use drivers from ATI, and most of the advanced features seem to be lost using the open source driver for this card.

This is the most promising link I found, but I am not sure I want to go through the hassle.
[http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

If you find another solution please post.  I am stuck using Vista Media Center until I can get a working linux DVR.

Thanks,

Marc

---

### Post by dundee5 on 2009-11-04
A have mouse cursor invisible too, but I have Nvidia drivers. Probably some bug in Mythtv.

---

