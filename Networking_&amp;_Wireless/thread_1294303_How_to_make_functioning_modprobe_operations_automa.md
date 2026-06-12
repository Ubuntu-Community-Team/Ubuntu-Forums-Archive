---
title: "How to make functioning modprobe operations automatic - Broadcom 4312 on Dell 1525"
date: 2009-10-18
forum: Networking &amp; Wireless
---

### Post by cefn on 2009-10-18
I've updated my Dell 1525 Jaunty installation (Linux Mint 7) to a Karmic Kernel. However, without a compatible build of linux-restricted-modules, my Broadcom wireless card didn't automatically work on boot.

I installed a replacement Broadcom driver (b44 and wl modules) from source, and found modprobe operations which make my wireless work, but how can I make them permanent?

I built and installed the Broadcom drivers as described here...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414281](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/414281)

Although my /etc/modprobe.d/blacklist.conf contains the lines....

```
blacklist bcm43xx 
blacklist b43 
blacklist ssb
```
...and my /etc/modules contains the lines...

```
lib80211
wl
b44
```
...I have to run the following sequence of instructions after each boot to load wireless. 

```
sudo modprobe -r b44 b43 ssb wl
sudo modprobe lib80211
sudo modprobe wl
sudo modprobe b44
```

What am I doing wrong with my modprobe.d and modules configuration?

---

### Post by kevdog on 2009-10-18
I believe something like this would be appropriate

You would modify the file:
Modifying /etc/modprobe.d/wl or simply one this script one to create the /etc/modprobe.d/wl file

echo -e '#wl workaround, added' `date` '\ninstall wl modprobe -r b43 b44 wl ssb; modprobe lib80211; modprobe --ignore-install wl $CMDLINE_OPTS; modprobe b44;' | sudo tee -a /etc/modprobe.d/wl

Basically this automates the loading of the wl driver.  Everytime the modprobe wl statement is run, it loads the the wl driver by first removing b43, b44, wl, ssb, and the loads lib80211, wl, and b44 in that order.  Basically making an alias for the modprobe wl statement that loads more than just the basic wl driver.

This was modified from the Jamie Jackson Feisty no fluff article.  I do not have a card that utilizes the wl driver so I'm not certain this will work, but please report back.

---

### Post by Bucky Ball on 2009-10-18
I understood the B43 driver and b43-fwcutter were the go for Broadcom ...

---

