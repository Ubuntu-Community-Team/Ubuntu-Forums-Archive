---
title: "Broadcom Wireless Card Trouble, New User."
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by grahambythepound on 2009-01-21
Hello, I'm new with Ubuntu and was having problems getting my wireless card to function correctly. I've been searching through the forums for awhile and have yet to come across a solution that does the trick. I've updated Ubuntu through a wired connection, and then enabled the Broadcom Wireless STA driver under the hardware drivers menu. This changed the led on the front of the laptop from orange to blue, indicating the wireless card was active, but i'm still unable to get a wireless connection, let alone search for an available network. Would this be done under the wireless tab in edit connections?  Any help would be great. Thanks.

---

### Post by Ayuthia on 2009-01-21
Welcome to the forums!  Can you help me out a little by going into the Terminal and posting the results of lspci -nn?  I just want to confirm the chipset of your wireless card.  It will be something like [14e4:43xx].

Can you also check in the Terminal and post the following also:
```
ifconfig
iwconfig
sudo iwlist scan
```
They will provide some information about your wireless connection.  It is sometimes easier to troubleshoot in the Terminal before trying to get the normal version working.

---

