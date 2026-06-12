---
title: "Installing ATI Radeon 200M"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by matteospqr on 2007-06-04
Hello!

I have feisty and I am trying to install the ATI drivers for my video card and getting the 3d accelartor to work.
I followed some steps in a forum but when I am near the end and I need to configure the xorg.conf file I get these messages:

matteo@matteo:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
matteo@matteo:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3

Before installing the new drivers and before doing all this the 3d accelator was working fine.  The onlything did I couldn't get it to do was to start Google Earth.  It would freeze and not run.

Is there a way to fix the mess I did trying to install the ATI drivers or do a rool back?

Thanks!

---

### Post by Alex Fernandez on 2007-06-04
those messages are fine, retart x / pc then do fglrxinfo and it should now say ati

Here is how I did it for the same card:

[http://ubuntuforums.org/showthread.php?t=221320&page=21](http://ubuntuforums.org/showthread.php?t=221320&page=21)

---

### Post by stchman on 2007-06-04
> **matteospqr said:**
> Hello!

I have feisty and I am trying to install the ATI drivers for my video card and getting the 3d accelartor to work.
I followed some steps in a forum but when I am near the end and I need to configure the xorg.conf file I get these messages:

matteo@matteo:~$ sudo aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.
matteo@matteo:~$ sudo aticonfig --overlay-type=Xv
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-3

Before installing the new drivers and before doing all this the 3d accelator was working fine.  The onlything did I couldn't get it to do was to start Google Earth.  It would freeze and not run.

Is there a way to fix the mess I did trying to install the ATI drivers or do a rool back?

Thanks!

If you are using Feisty then just enable the restricted drivers.  I have a 200M in my laptop and 3D acceleration works fine.  Google earth works awesome as well.

---

### Post by hhpeter on 2007-06-04
> **stchman said:**
> If you are using Feisty then just enable the restricted drivers.  I have a 200M in my laptop and 3D acceleration works fine.  Google earth works awesome as well.

Yap the same here just enable the restricted drivers
System>Administration>Restricted drivers manager
restart and it should work I have 1280x1024 resolution and beryl is running like a champ

---

### Post by matteospqr on 2007-06-04
I think I messed something up because when I try and access the restricted drivers it wont let me open it saying my computer does not need restricted drivers.
I was able to create a new xorg.conf file but I think I installed some "masa" drivers and other things that I dont know how to get rid off.
Is there a way to delete all video drivers and restart from the beginning?

---

### Post by stchman on 2007-06-06
> **hhpeter said:**
> Yap the same here just enable the restricted drivers
System>Administration>Restricted drivers manager
restart and it should work I have 1280x1024 resolution and beryl is running like a champ

My laptop uses 1280x800.  There are many out there that don't want to taint their kernel with the restricted drivers.

I have not tried Beryl on my laptop.  I tried to enable desktop effects and it would not work.  I am not too much into eye candy.  I do see that Beryl is in the Add/Remove in Feisty.  Did you install Beryl that way?

---

### Post by gunbladeiv on 2007-06-06
im using dapper.
how can i configure my ATI Radeon Xpress 200M to work?
please help me

---

### Post by stchman on 2007-06-06
> **gunbladeiv said:**
> im using dapper.
how can i configure my ATI Radeon Xpress 200M to work?
please help me

Three options:

1. Do a clean install of Feisty as it has ATI restricted drivers.
2. Follow my procedure to install ATI drivers:  [http://www.stchman.com/video_drivers.html](http://www.stchman.com/video_drivers.html)
3. Install Envy for Dapper [here]("http://www.stchman.com/tools/envy_0.9.3-0ubuntu6_all.deb").  This version of Envy works for Dapper, Edgy and Feisty.

Envy is the easiest option, clean install of Feisty is the best IMO.

If you decide to do a clean install of Feisty go to my website as there are a great many procedures to configure Feisty.  I have a script to get that Broadcom card working as well.

---

