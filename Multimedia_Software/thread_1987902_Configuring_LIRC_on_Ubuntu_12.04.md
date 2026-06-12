---
title: "Configuring LIRC on Ubuntu 12.04"
date: 2012-05-26
forum: Multimedia Software
---

### Post by mike_kenobi on 2012-05-26
Hi,

I'm trying to configure lirc on my Toshiba Qosmio F60-159 with Ubuntu 12.04 (lirc is on version 0.9). I've tried to follow the instructions on [http://www.linlap.com/wiki/toshiba+qosmio+f50-f55](http://www.linlap.com/wiki/toshiba+qosmio+f50-f55), but the linux-modules-source package does not exist anymore for kernel 3.x. Please, how can I configure this for my ir remote controller (mo. G83C0008A110)? It is starting to be tricky.

All the best,
Miguel

---

### Post by Stampede on 2012-06-27
Same problem here! I have a Toshiba Satellite A500-1EK with a CIR (ene0200) remote controller mod. G83C0008A110 ([http://lirc.sourceforge.net/remotes/toshiba/G83C0008A110.jpg](http://lirc.sourceforge.net/remotes/toshiba/G83C0008A110.jpg)) and I cannot make it work.
I think the problem could be in properly editing /etc/lirc/hardware.conf and /etc/lirc/lircd.conf.

Any idea?

---

### Post by vidtek on 2012-06-27
> **mike_kenobi said:**
> Hi,

I'm trying to configure lirc on my Toshiba Qosmio F60-159 with Ubuntu 12.04 (lirc is on version 0.9). I've tried to follow the instructions on [http://www.linlap.com/wiki/toshiba+qosmio+f50-f55](http://www.linlap.com/wiki/toshiba+qosmio+f50-f55), but the linux-modules-source package does not exist anymore for kernel 3.x. Please, how can I configure this for my ir remote controller (mo. G83C0008A110)? It is starting to be tricky.

All the best,
Miguel

Miguel

Lirc has been subsumed into the kernel, it breaks much more than it fixes.  I've been struggling with this for a couple of weeks and just keep going round in circles.  My biggest problem is the mceusb driver is now event-driven, and when I change my Mythtv from the computer interface it automatically puts my machine to sleep--no recordings.

I have trawled all over the net for a fix, but it seems I have no option but to compile a new kernel, removing this blo...dy event mceusb device.  The Toshiba remotes you and stampede have are similar to the mceusb driver and are also probably in the kernel.  

Other than compiling the kernel, our only option is to go back to Natty or Lucid, unless someone with more knowldge than I can come up with a way of disabling the kernel drivers without a compile.

Best of luck, Tony.

---

