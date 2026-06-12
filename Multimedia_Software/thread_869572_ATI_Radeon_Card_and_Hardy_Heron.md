---
title: "ATI Radeon Card and Hardy Heron"
date: 2008-07-24
forum: Multimedia Software
---

### Post by keystroker on 2008-07-24
Ubuntu 8.04 installs on my desktop right out of the box without any problems.  An icon pops up in the tray telling me restricted drivers are available for my graphics card. An ATI accelerated graphics driver to give me top performance (which is what I want).  When I install it and reboot, I am no longer able to boot up and I get a black screen that just sits there.  Booting in recovery mode and using the fix Xterm option does not help to restore it back to normal.  Anything that could help me with this problem would be great.  Other threads, instructions on how to fix it, or any other strategy.  I'm assuming this means I'm using a basic generic video driver after install, and ATI doesn't really support linux distro drivers.  I just want to use the full potential of my graphics card.  Thanks guys!


Intel 64bit Core 2 Duo @ 2.4 ghz
ATI Radeon HD 2400 XT
4 GB of Ram
250 GB Seagate Hard Drive

---

### Post by tuxxy on 2008-07-24
If you can get to a prompt by doing ctrl + alt +f1 then try and 

```
startx

```

If no luck you could attempt to reconfigure the xorg and then install the drivers again but with envy perhaps,

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by keystroker on 2008-07-25
Just did a fresh install to get back to normal, not able to get to console otherwise.  System completely froze on reboot after installing drivers.  From what I've read envy won't solve the problem either.  Can't even fix it from root terminal, or using fix Xterm option from recovery console (gives me a blank white screen instead).  I hope i'm not stuck using the generic video drivers...

---

### Post by markbuntu on 2008-07-25
If your HD2400 is an agp card, it is supported by the latest ati drivers, 8.6 and 8.7. The release notes for the 8.6 driver are here:


[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_86_linux.html)

If you want to get the latest 8.7 driver, you can follow the directions here (use Method 2):

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

It is extremely important to follow these directions VERY CAREFULLY.

The directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)


ATI has made a new commitment to linux drivers and has promised to have them on par with their windows drivers. Crossfire support is coming in the fall along with some other good things.

---

### Post by keystroker on 2008-07-27
Works like a charm, thanks so much man.  I can't tell you how pleased I am that I'm able to run compiz fusion.

---

