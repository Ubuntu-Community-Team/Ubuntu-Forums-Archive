---
title: "unExtreme Airport browse scan HOWTO"
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by svref on 2006-02-27
If you're like me, you're annoyed that you can't take your cute little G3 with you to coffee shops, since it can't browse or scan the aether for essids.  Well, it can, but you need to do some work.

Take a deep breath, this is going to take 3 hours, but you won't be actively typing during most of that time.

First, you have built a kernel ON YOUR MACHINE.  Refer here on how to do that.  
[https://wiki.ubuntu.com/KernelHowto?highlight=%28CategoryKernel%29](https://wiki.ubuntu.com/KernelHowto?highlight=%28CategoryKernel%29)
Tip1: steal the /usr/src/linux/.config from /boot, so you don't have to ponder all the imponderables of kernel configuration.  That's what we're paying^H^H^H^H^H^H giving-props-to the Ubuntu hackers for.

Install the kernel image and headers from the package.

reboot.

In a new directory get the current orinoco sources with:
```
cvs -z3 -d:pserver:anonymous@cvs.savannah.nongnu.org:/sources/orinoco co orinoco
```

Follow the orinoco driver build instructions here:
[http://www.nongnu.org/orinoco/documentation/index.html#q2](http://www.nongnu.org/orinoco/documentation/index.html#q2)
(basically make && make install)
:-k **Warning**: Make install craps into your newly built kernel package.  In other words, after doing this, the files installed by your so-laboriously-built kernel package are no longer exactly what's on the disk.  I don't like this at all, but I don't know how to do it the right way (which would be patching the kernel sources somehow, methinks).

Reboot another time for good luck.

Now **iwlist eth*1* scan** returns a list of detected networks.  Enjoy yourself a coffee and a pastry, coffee-shop monkey!

Ps, I reccomend NetworkManager from universe.  Its a neat little applet that does a good job of interfacing with your newly working driver.

PPS: remember that you have to pay attention to when ubuntu notices security holes in their kernel, since you'll have to, ugh, recompile from scratch all over again every time that happens.

---

### Post by svref on 2006-02-28
PS: Another better way to do it might be to upgrade to 2.6.15 or higher kernel.  According to NetworkManager page 2.6.13 and support browse/scan.  So go with 2.6.15 or whatever's current.

---

