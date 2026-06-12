---
title: "WUSB11 v2.8 Linksys USB Wireless Adapter"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by stalemath on 2011-01-28
Hi, I am completely new to Linux and have just installed Xubuntu on an old HP machine. Until I buy a long enough ethernet cord to reach my router upstairs, I would like to try to make use of a Linksys wireless USB network adapter that I have (WUSB11 ver. 2.8). I looked around online and I got pretty confused. I don't know where to start.

---

### Post by darkhelmetchris on 2011-01-28
Out of curiousity, have you tried simply connecting the USB adapter and see if it works right away?  I think this version is old enough to be recognized automatically - if it's the one I am thinking of - the blue/grey unit with the fold-up popsicle-stick-looking antenna.  I have used this type a few times with my Ubuntu before.

Plug in the unit, wait for it to be identified (usually in a few seconds) then click your network manager icon near your clock.  If you see wireless networks, then you should be ready to go, just click the network you want to connect to.

If you have plugged it in, and it does not appear in your network manager (taskbar icon) automatically, then what is the output of the command:

```
lsusb
```

---

### Post by stalemath on 2011-01-28
I'm not able to connect just by simply plugging it in. When I go to the network settings, I get 5 tabs: Wired, Wireless, Mobile Broadband, VPN, and DSL; all are empty except for "Wired": It has 2 selections - "Auto eth1" and "Auto eth0" (both say never used).

In response to lsusb, I get:
```

Bus 001 Device 002: ID 1915:2233 Linksys WUSB11 v2.8 802.11b Adapter
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by subzero27 on 2011-01-28
Does the device gets recognized ? As dark said that the device is pretty old to be recognized. SO i don't see any problems running it

---

### Post by stalemath on 2011-01-28
I believe it gets recognized, however I can't seem to get it to work. I'm using Xubuntu also, if that makes a difference.

---

### Post by stalemath on 2011-01-29
Now it tells me that networking is disabled. How do I fix this?

---

### Post by darkhelmetchris on 2011-01-31
Okay, let's see what we can find out then..

What is the output of:
```
ifconfig -a
```

---

### Post by Digital Viking on 2011-04-23
After days of bashing my head on the keyboard, I finally got my WUSB11 v2.8 working in Maverick on kernel 2.6.35, with Gnome and KDE4 (depending on what I'm doing...) Thanks, by the way, to Google and everybody who documented the same problem on posts like these. On to the fix:
You need to download two packages from Synaptic: HAL (the Hardware Application Layer) and atmel-firmware. Don't panic when it says a few kernel-related packages have to be removed; this didn't affect my kernel one bit. This is important: READ THE DOCUMENTATION ON BOTH - that's why they wrote it.
Now, here's the untested variable: I don't think it picked up initially in Gnome. The device was only recognised and assigned to wlan1 (it's a secondary adapter for network monitoring...) *after* I downloaded and installed the KDE desktop. I don't yet know if this made a difference, but I'll probably post it here when I do.
If a newbie like me can do this, anyone can!
Now I just need to get it to connect...
On to the next thread!

---

