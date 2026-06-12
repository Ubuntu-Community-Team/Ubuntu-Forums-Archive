---
title: "Installing network adapters WUSB600n rt2870"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by CynicalPsycho on 2009-04-11
Um... Yeah, so I got this new USB wifi adapter WUSB600n it runs a Ralink rt2870 chipset. Which works great on my vista, but is dead on ubuntu.

From what I'd read prior, ralink was the way to go because they offered their source for linux to use. 

However this newer version doesn't seem to be out the box ready.
I did however find a linux driver at:
[http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)

and another one more fitting for what i need at:
[http://forum.aircrack-ng.org/index.php?topic=4397.0](http://forum.aircrack-ng.org/index.php?topic=4397.0)

I however have no clue how to implement them, could someone help me out?

[System Info]
Dual Booting 8.10 ubuntu and win vista
64 bit system
4 gig ram

If you need any other info to help me solve this issue, please ask.

---

### Post by marcelkoopman on 2009-04-18
Hello,

I've got it working. What you need to do is build a custom kernel.
Download from kernel.org version 2.6.29.1
When configuring it you will see that in the staging drivers you can choose the RT82870. Select that one.

Then edit the source files like in the howto's, configure /etc/Wireless and build the kernel.
Install the kernel, reboot and boot this custom kernel.
It should work.

---

