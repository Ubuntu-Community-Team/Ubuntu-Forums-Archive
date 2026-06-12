---
title: "ATI 8.23.7 drivers and Ubuntu 5.10 for AMD 64"
date: 2006-03-31
forum: Multimedia &amp; Video
---

### Post by ThaRabbit on 2006-03-31
Hey all, I have recently used this guide to install my ati drivers (8.23.7) for my amd turion (MT 32, which is a 64 bit cpu) based laptop:
[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Installing_the_new_driver](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide#Installing_the_new_driver)

Now as you can see, the section which describes howto install the new drivers (I am talking about:  Method 2: Generating/Installing Ubuntu packages for the newer 8.23.7 drivers in Breezy Badger) does not mention anything about deselecting int10a when configuring xorg.conf to load fglrx as the graphics driver. Method 1 on the same site does suggest this.

I had to prevent loading of int10a on my system (in xorg.conf) to prevent a crash of my system. Is there a line in the guide missing for 64 bit users there ? I thought I would check with you all before I edit a wiki while I am the one doing something wrong :)

---

