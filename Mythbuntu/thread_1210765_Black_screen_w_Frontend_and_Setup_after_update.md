---
title: "Black screen w/ Frontend and Setup after update"
date: 2009-07-11
forum: Mythbuntu
---

### Post by lingenfr on 2009-07-11
After the most recent update, mythtv-setup and mythfronted produce a black screen with a white outline box. I can't figure out what is going on. I get the same behavior connecting to my backend remotely or with a local monitor. I have the following video card:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

running the ati driver in my xorg.conf.

---

### Post by louisc1 on 2009-07-12
Hi All,

First time user of Mythbuntu, having the exact same problem with a completely fresh install.(9.04)

Have tried two individual (fresh) installs one with the AMD driver one without, both with the same result. 

White box in the middle of screen, although if you mess with the keyboard you can get into what seems like set-up options with drop downs etc

Easier if I just get a picture up...BRB

---

### Post by louisc1 on 2009-07-12
[IMG]http://i32.tinypic.com/2945i8i.jpg[/IMG] 

[IMG]http://i25.tinypic.com/2djcpll.jpg[/IMG]

[IMG]http://i28.tinypic.com/fulc9.jpg[/IMG]

---

### Post by lingenfr on 2009-07-12
Thanks for the picture, same as mine. Seems to be a problem with the ati driver. Try the following:

sudo nano /etc/X11/xorg.conf

Look for the line that says:

Driver     "ati"

and change it to read:

Driver     "vesa"

That worked for me and as I don't use my backend as a frontend, that is not a problem. If this is your frontend or a combined backend/frontend, you will probably want to do some more searching to see what settings may need to be changed in your xorg.conf to make the ati driver work. Vesa will be less than optimal for you. Good luck. I will post back if I find the fix. Unfortunate that others on the forum are not sharing.

---

### Post by louisc1 on 2009-07-12
Cheers, will give that a shot when I get back. 

This will be my front end so will continue looking, may just swap the GFX card to another ATI I have handy, if that solves it might be able to narrow it down a little more. 

If anything this has been a big help in narrowing down the cause as I managed to convince myself it wasn't graphics related originally.

---

### Post by lingenfr on 2009-07-12
Louis,

The first thing I would try is outlined here:

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Disable_Composite_Extension_2](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Disable_Composite_Extension_2)

I will try it myself when I get time.

---

