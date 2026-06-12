---
title: "[SOLVED] ATI radeon X1950 pro (PCI-e) installation"
date: 2008-07-15
forum: Multimedia Software
---

### Post by Sigiken on 2008-07-15
Hi,
I'm new to ubuntu, but I like it except the problem that my video card causes, I can't get it to work.
I've installed the restricted drivers from ubuntu, the drivers from the ati website and EnvyNG, when I install it, ubuntu crashes after the bootscreen when the login screen is loading.
I'm really desperate. i've looked on quite some forums but I have no idea what it can be.

I do can boot if I go to recovery mode, go into the console, and put Option "nodri" under the device section in /etc/X11/xorg.conf but thats not really a solution.

I hope someoen can help me with this.
Jonas

---

### Post by soxs on 2008-07-15
[http://ubuntuforums.org/showthread.php?t=859957](http://ubuntuforums.org/showthread.php?t=859957)
this is a radeonhd 3870 but install process should be the same, you may adjust the PCI id in the xorg.conf, the rest should go fine...

---

### Post by Sigiken on 2008-07-17
> **soxs said:**
> [http://ubuntuforums.org/showthread.php?t=859957](http://ubuntuforums.org/showthread.php?t=859957)
this is a radeonhd 3870 but install process should be the same, you may adjust the PCI id in the xorg.conf, the rest should go fine...

Hey, thanks for the help, but I couldnt do it, anyway, I really want linux, and since it's vacation I can work more, wich means more money :) I've bought me a nvidia 9600 GT, as I've read, nvidia works better on linux atleast it gives less complications/problems^^ so I can install linux in a while when I got it :-)

---

### Post by soxs on 2008-07-18
> **Sigiken said:**
> Hey, thanks for the help, but I couldnt do it, anyway, I really want linux, and since it's vacation I can work more, wich means more money :) 

Why "couldn't" you do it?
You just need to purge your drivers with envy and afterwards install fglrx driver with method 2 of that howto:[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)

In case you have 4GiB RAM or more this may be a required step too: [http://ubuntuforums.org/showthread.php?p=4766662](http://ubuntuforums.org/showthread.php?p=4766662)

> **Sigiken said:**
> I've bought me a nvidia 9600 GT, as I've read, nvidia works better on linux atleast it gives less complications/problems^^ so I can install linux in a while when I got it :-)

lol, this is outdated. Sure the driver frontend has some more oportunities, but ATI/AMD made its specs availiable for the open source community. Nvidia is unusable for normal 2D desktop usage due to driver problems which are there for some days now.
Atis fglrx driver is evolving and the current one (8.6) fixed all my troubles I had in the past few years.

---

