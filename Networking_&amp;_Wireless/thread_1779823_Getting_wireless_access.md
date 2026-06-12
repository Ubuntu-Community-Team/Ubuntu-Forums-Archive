---
title: "Getting wireless access?"
date: 2011-06-11
forum: Networking &amp; Wireless
---

### Post by emno on 2011-06-11
I just installed 11.04 on a partition on my pc, but can't get any wireless internet access to work.

its the server ediiton

---

### Post by NetDoc on 2011-06-11
Are you posting from this PC? If so, just enable third party drivers. If not, attach it to the internet via wire first and be sure to enable those drivers.

---

### Post by emno on 2011-06-11
Hmm im not.. although I can access windows fine from the pc im running it on.

how would i go about enabling third party drivers?

---

### Post by NetDoc on 2011-06-11
So this is a dual boot machine and you're posting from the Windows portion. Find a wired connection and use it. It's really the simplest way to go.

---

### Post by emno on 2011-06-11
unfortunately i dont have access to a wired connection

---

### Post by walt.smith1960 on 2011-06-11
The first question is usually " which wireless device?" Assuming it's a PCI device, posting the results of "lspci" (or lsusb for usb devices) might be a good start.  The relevant line would may have something like Broadcom or Realtek in it.

---

### Post by emno on 2011-06-11
NEtwork controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by bkratz on 2011-06-11
There is a section here (toward the bottom) on installing the b43 driver with no internet access that will probably help you.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by emno on 2011-06-11
I've gone through all that except for Step 4 as I dont have access to the desktop menu to activate the driver

---

### Post by emno on 2011-06-11
ok got it to work finally after hours of googling and trying different things. first thing followed the steps on the link above up to step 4 where i got stuck

then i ran 

~$ sudo modprobe -r b43 ssb
~$ sudo modprobe b43

then 
ip link wlan0 set 

and finally 

sudo ifup wlan0

i tested it with ipaddr and saw that i got a connection finally.

---

### Post by bkratz on 2011-06-11
> **emno said:**
> ok got it to work finally after hours of googling and trying different things. first thing followed the steps on the link above up to step 4 where i got stuck

then i ran 

~$ sudo modprobe -r b43 ssb
~$ sudo modprobe b43

then 
ip link wlan0 set 

and finally 

sudo ifup wlan0


 tested it with ipaddr and saw that i got a connection finally.


Just got back and see that you got it congratulations!

---

