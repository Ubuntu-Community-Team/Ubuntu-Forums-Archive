---
title: "Is   bt ~ # ifconfig   a good command"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by lindsay7 on 2009-03-10
On a web document there is a comment about configuring a my usb wireless adaptor, it gives this syntax for two commands, do these make sense

bt ~ # ifconfig rasb0 up
bt ~ # iwconfig rasb0 mode monitor

Do I enter this in the terminal box as shown or not?

Here is the info from the site:

"Linksys WUSB54GC 
Driver : RT73 
Chipset : Ralink Technology, Corp. 802.11b/g WiFi 
Notice 1: The interface is named rausb0, not eth0 or ath0 etc. 
Notice 2: Built-in [BackTrack] Driver does not support fragmentation attack; however, the following driver does: 

[http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-2.0.1.tar.bz2](http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt73-k2wrlz-2.0.1.tar.bz2) 

Needs activation before use 
  bt ~ # ifconfig rausb0 up
  bt ~ # iwconfig rausb0 mode monitor

Everything works out of the BT3 box!"


Thanks for the advise.

---

### Post by Iowan on 2009-03-10
Just my opinion - for what its worth...
bt ~ # looks more like a prompt (at least I've never seen those "commands").  the **ifconfig** and **iwconfig** (and what follows) look like valid commands.

---

