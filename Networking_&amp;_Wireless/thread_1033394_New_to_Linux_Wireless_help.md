---
title: "New to Linux: Wireless help"
date: 2009-01-07
forum: Networking &amp; Wireless
---

### Post by ShawnMichael on 2009-01-07
Hi.  I am new to Linux and Im having issues with the network.  I am on my Dell Inspiron B130 laptop using Intel(R)Pentium(R)M. Dell Wireless 1370 Wlan Mini-Pci Card. And for whatever reason, or whatever I do, it wont let me use the network on Ubuntu.  Can anyone give me step by step to get it working?  Remember I am a first time Linux user, and I would like to use Linux.  Any help would be appreciated!

---

### Post by Ayuthia on 2009-01-07
If you have a working internet connection in Ubuntu, you can try to activate the wireless card (I am thinking that you have a Broadcom card, you can check lspci -nn in the Terminal to verify) by going into System->Administration->Hardware Drivers and activating the Broadcom driver.  It will ask you if you want it to fetch the firmware for you.  If you have a working connection, say yes.

If you don't have a working connection, you can try this link:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)
It is a set of instructions on what to download and install into Ubuntu to get the Broadcom card to work.

---

