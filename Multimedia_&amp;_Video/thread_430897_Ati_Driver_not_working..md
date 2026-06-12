---
title: "Ati Driver not working."
date: 2007-05-02
forum: Multimedia &amp; Video
---

### Post by .Com on 2007-05-02
I feel like I've tried just about everything, including Envy and some manual ways.. but I'm not giving up.

Anyways I have ATI Radeon 9250 graphics card, the problem is I can't use it at all. If I insert it into my computer it shows me my 'boot' screen as do all computers displaying it's -type- mine says Compaq. Ok, moving on. After that it shows me the Grub boot screen then loads into the very nice looking Ubuntu loader with load bar underneath, now here lies my problem, if I have the graphics card inside my computer and hooked up to my moniter, it DOES NOT make it past that Ubuntu boot screen, it goes black and I can't proceed any further, If I attempt to use the DEFAULT video card that came with the computer while the ATI driver is installed it doesn't work AT ALL, the only sign of it working is after the Ubuntu Load screen with the nice load bar etc, and the screen is sitting black and I unplug my moniter from my ATI card and plug it into the default one I get something almost equivilent to a T.V not hooked up to cable (The fuzzy load annoying thing, minus the sound of course.)


If I take out the ATI card then my default one works fine and shows everything and all is well.

This is VERY frustrating seeing as how I can't get my ati driver to install, or even work past the boot screen.


Please help me, give me suggestions and I'll gladly tell you if I've tried it, (I probably have.) so we can move on.


Thanks in advance, and if anything at all looks unclear, let me know so I can fix it or explain it better.

---

### Post by .Com on 2007-05-02
So I figured out how to boot up with the default video driver while my ati card is inside my computer, just had to fidle with my bios a bit, anyways.. still need help getting this in, thanks!

---

### Post by tyboon on 2007-05-02
What kind of monitor do you use?Do you use ati now?If so...try this...
open the terminal and enter..

 sudo dpkg-reconfigure -phigh xserver-xorg

It will prompt you to a screen..use cursors up-down and find Ati...press enter..pick which resolution you like and press SPACE to tick it..Press enter to leave screen..
It should be working...Let me now.:guitar:

---

### Post by .Com on 2007-05-02
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20070502185312

I got that error.. Thanks for your help!

---

