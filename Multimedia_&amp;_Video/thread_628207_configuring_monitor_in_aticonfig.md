---
title: "configuring monitor in aticonfig"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by devosion on 2007-12-01
Im still getting the hang of using aticonfig to setup my video card but early on i've noticed that when I run a query on my monitor this is what I get.

>   
Connected monitors: none
Enabled monitors: none


The problem is that when I run

>  aticonfig --resolution=0,1600x1200,1280x1024,1024x768,800x600


To set up the resolution to my monitor, since when I adjust the screen resolution in system > preferences > screen res it seems to stay at 1024x768 even when I set it to 1280x1024, im getting this error message.

> error at set screen resolution : screen0 does not exist

Which pretty much leaves me scratching my head. Im not sure where to keep going after this. Although I did find a blog that describes the problem being between XGL and X. 

[http://www.lunders-and.no/wp/?p=96]("http://www.lunders-and.no/wp/?p=96")

Which I cant say im totally sure about since I dont know how to access XGL settings to see how it is affecting my monitor. 

Please help!

---

### Post by devosion on 2007-12-01
As if things werent complicated enough. I went ahead and attempted to setup a single monitor through the command..

> aticonfig --desktop-setup=single

I get this lovely error message.

> Warning: Option 'DesktopSetup' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-1
*** glibc detected *** aticonfig: munmap_chunk(): invalid pointer: 0xbff039d2 ***
======= Backtrace: =========


======= Memory map: ========

Aborted (core dumped)


I checked to see if I could open my xorg.conf file after this and found out it had been deleted after the command was executed. Luckily I had a backup.

---

### Post by devosion on 2007-12-01
Well it has gotten to the point where I cant do anything with aticonfig without causing a 'core dump' and losing my xorg.conf file. This includes something as simple as seeing what aticonfig is currently doing with aticonfig --v. Im surprised --help even works...

Well not really fixed. I'll just edit the xorg.conf file on my own since aticonfig seems to be buggy.

---

