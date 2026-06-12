---
title: "BCM4321 Wireless Install Problem Serious Help Needed!"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by transversegirl on 2011-03-10
First off, I'm a total noob. Complete novice. I know next to nothing.

So, naturally, I've tried installing the updated driver from Broadcom for my BCM4321 wireless card and I've hit some roadblocks. I read several posts the on here, printed the replies, double-checked the instructions from Broadcom and thought I was ready. Nope. I think I'm just way out of my depth. Here is what I've done thus far.

So, following the instructions from Broadcom, I've completed all of the tasks below:

> BUILD INSTRUCTIONS
------------------
1. Setup the directory by untarring the proper tarball:

For 32 bit: 	hybrid-portsrc_x86-32_v5.100.82.38.tar.gz
For 64 bit: 	hybrid-portsrc_x86-64_v5.100.82.38.tar.gz

Example:
# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc_x86-32_v5.100.82.38.tar.gz

2. Build the driver as a Linux loadable kernel module (LKM):

# make clean   (optional)
# make

When the build completes, it will produce a wl.ko file in the top level
directory.

Now, when I attempt the second part of the instructions, listed here:

> If you were already running a previous version of wl, you'll want to provide
a clean transition from the older driver. (The path to previous driver is
usually /lib/modules/<kernel-version>/kernel/net/wireless)

# rmmod wl 
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

The new wl driver should now be operational and your all done.

I encounter the following problem:

> ERROR: Removing 'wl': Operation not permitted

When I attempt any of the other steps listed, I get fatal errors informing me "Permission denied."

I've ran

> sudo lshw -C network

and my device is showing up UNCLAIMED, meaning that the driver hasn't loaded.

I'm at a complete loss here. The user has administrative role so I don't understand why permission would be denied. The wl driver that is currently on the machine is not being used by the device so why can't I remove it? And, essentially, I'm at a dead stop.

I really really don't want to go back to using Snow Leopard. But, I also don't want to be stuck sitting on the floor with my Macbook plugged into the modem via ethernet.

Help?

---

### Post by transversegirl on 2011-03-10
I've marked this as solved because I'm up and running, though I'm not entirely sure how I did it. Beginners luck?

---

