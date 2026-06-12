---
title: "nVidia GeForce Go 7300 - Visual Effects"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by Popple3 on 2007-10-23
Basically I want to use the Compiz Fusion visual effects on Gutsy, but when I turn them on, I get a message saying:
> The software source for the package

   nvidia-glx-new

is not enabled.

When using the Live CD it attempted to get the appropriate driver for it. I downloaded this package, but when I try install it wouldn't install (there was an error message, but I cant remember what it was). Any idea how to sort this out?

---

### Post by Popple3 on 2007-10-24
Can anybody help me with this?

---

### Post by sboyd on 2007-10-26
I have this same problem on my Dell Inspiron 6400 - GeForce G0 7300, can't install the drivers to enable the effects.

---

### Post by siralphred on 2007-10-26
try to install nvidia-glx-new look in synaptic first if its not there google "installing nvidia-glx-new"  or u can use envy to install the new nvidia driver....envy installs nvidia-glx-new as well
heres the link to envy [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by sboyd on 2007-10-26
Installing Envy says that a dependency is missing, xserver related.  This was a fresh install, formatted the partition, and started over.  The video was working fine under 7.04.

---

### Post by siralphred on 2007-10-26
> **sboyd said:**
> Installing Envy says that a dependency is missing, xserver related.  This was a fresh install, formatted the partition, and started over.  The video was working fine under 7.04.

use envy in text mode then,,,, reboot and go to recovery and then type: envy -t    that will bring up the text menu of envy, since xserver is not running that error shouldnt come up...after that reboot and hopefully it should work

---

