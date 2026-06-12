---
title: "HD 3650 Problem"
date: 2008-08-24
forum: Multimedia Software
---

### Post by chaosdesigner on 2008-08-24
Hello,

I have a big problem with my new ati HD 3650 on my Hardy Heron. I just cant get the drivers to work properly... it just doesnt work. I know that there ar ea million guides on how to install ati drivers and catalyst and everything, and i have tried everything but nothing has worked. Sofwar I have come to a state where I have the right resolution but I have this black boxe around my caro-dock and i dont have the compiz effects. Im pretty sure that i messed up because i just tried every method, ive tried it with the "linux-restricted-modules-generic", i have treid the Catalyst 8.4 and i have tried it with envygn. 

I have no Idea how I can make this worke, could somebody help me?

thx


Edit:

This is a screen of this "black box":

[[IMG]http://img144.imageshack.us/img144/8445/screenshotap1.th.png[/IMG]](http://img144.imageshack.us/my.php?image=screenshotap1.png)

---

### Post by chaosdesigner on 2008-08-25
I hate to push this but doesnt anybody have a solution?

---

### Post by markbuntu on 2008-08-25
Just enabling the restriced drivers in System/Adminstration/Hardware Drivers and let them download and install themselves should work just fine.

But anyway, as far as following guides goes, this is the only guide that ever worked for me with my HD3650 (use method 2, follow it very carefully, if you are using amd64 it is very important to follow the special directions for 64bit. This will also get you the latest 8.8 driver):

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by chaosdesigner on 2008-08-26
I have tried just enabling the restriced driver but i count log in afer the reboot and I had to recover the xorg.conf.

Im going to try out that guide soon, but could it be a problem that i already tried to install a different driver?

Edit:

I have a stupid question, it says ```
sudo dpkg -i xorg-driver-fglrx_*.deb fglrx-kernel-source_*.deb fglrx-amdcccle_*.deb
```

Now where do I get theses debs?

---

### Post by chaosdesigner on 2008-08-26
ok, i used the guide and it worked with the second method, thx!

---

