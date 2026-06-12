---
title: "Struggling w/ NVIDIA GeForce 7600 GTS dual-monitor integration"
date: 2006-12-29
forum: Multimedia &amp; Video
---

### Post by mattengland on 2006-12-29
Hello,

I'm attempting to establish a Ubuntu-based, software-development workstation (as part of the Cleversafe project, for what it's worth) that supports dual monitors.

Here's the specs on my current system:

[http://www.powerspec.com/systems/system_specs.phtml?selection=7121](http://www.powerspec.com/systems/system_specs.phtml?selection=7121)
NVIDIA e-GeForce 7600 GTS (I can't find this specific model referenced anywhere, but that's what my box says; it's *not* a GS, _nor_ at GT; it's a "GTS")

I currently have a duo-core system that's 2GB-memory limited (I discovered the hard way that the first 4GB-memory capable system I tried was not going to work with pre-2.6.18 kernels or installs less then Feisty)--and the above--and hopefully compatible enough for a Dapper or Edgy install.  I also hope to upgrade the kernel from there to 2.6.18 based or higher so I can take advantage of the duo-core system I have.  However, if I can't get this combination to work, I can go get yet another system (this is currently my second one--I've been "downgrading" hardware to get this stuff to work) to make this stuff all work.  My main requirements are mostly a speedy/beefy machine to run a lot of compiles, systems tests, and some virtual machines (via VMware--which I already do on another Ubuntu system, so I'm familiar with that) AND...dual monitors.  I need a lot of code viewing space.  So if you have alternative hardware recommendations for either the system, video card, or anything else, please hit me with it.  I've got to get things working soon.

I see a remarkable number of refernces to get this stuff working, and I'm kind of overwhelmed.  There's so many differnet scenarios, references, documents, etc.  I'm trying to get at least a wee bit of direction to figure out which one of these references I should start with.

Here's my symptoms as they stand right now:

Dapper 6.06.1 default install will use at least one monitor ok, but when I upgrade the kernel to 2.6.18.6, my boot-up freezes with a strange pattern across the monitor.  Same thing for default Edgy and kernel-upgraded Edgy.  I have yet to try Feisty.  The 6.06.1 default install doesn't have a resultion selection above 800x640...or something like that.  I'd rather not mess around with the 2.6.15 kernel on Dapper because I'm going to upgrade the kernel anyway...unless I just dump this duo-core stuff and strip down the hardware even further?

My monitors are also the rotating kind (Samsung SyncMaster 204B: [http://www.samsung.com/Products/Monitor/LCD_Digital/LS20BRDBSQXAA.asp](http://www.samsung.com/Products/Monitor/LCD_Digital/LS20BRDBSQXAA.asp) ), and I will be rotating...and I'm going to want to get the nvRotate stuff to work.  But first thing's first--I've got to get the system to boot up first.

Note that my system has an ATI, built-in VGA card, and this ATI hardware may be contributing to my problems.

I'll also be happily willing to pay someone to give me interactive support preferably over the phone but possibly via instant message as well.

I'm trying to avoid having to go do another, non-Debian-based system like Fedora6, because non-Debian systems are a lot harder to manage.  But so far, I'm really struggling to get Ubuntu to work.

Also, for what it's worth:  I'm an experience Ubuntu user on my Thinkpad T41 laptop.  Unfortuantely, I'm so far finding Ubuntu installs on the desktop hardware I've tried thus far to be much harder than my laptop (which was mostly quite easy--until I upgraded to Edgy from Dapper, anyway, but that's a different story).

Thanks for any help,
-Matt
Dispersed storage: [http://cleversafe.org](http://cleversafe.org)

---

