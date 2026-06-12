---
title: "HP Pavillion ze4900"
date: 2010-06-02
forum: Networking &amp; Wireless
---

### Post by Jemop430 on 2010-06-02
I recently installed Ubuntu 8.10 onto my computer and neither the ethernet nor the wireless worked, I am currently updating the operating system to 10.04. But seeing as there have been posts on this and I'm new to linux Iknow ther is still a problem (during the update linux told me it found no network drivers). I also know that I need the solution explained in the simplest terms. I am on my home computer for the internet so I can transfer things using a usb drive.

---

### Post by pdc on 2010-06-02
this link 

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1909550.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1909550.html)

says

> This computer has a built-in Broadcom bc4306 wireless.

and spells it out

> 02:06.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03) 

I think you will need the b43 driver for that, described here

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

so look for this heading

>  Broadcom BCM4301/03/06/09 Hardware (B43 driver):

decide if you will have your computer wired to a router, or use the liveCD  ... and you need to follow the instructions carefully: maybe have a means to print them out ..

let us know how you get along

---

### Post by Jemop430 on 2010-06-02
No I don't plan to have it going through a router. As there any reason it can't find the ethernet port? Is that a driver issue as well?

---

### Post by Jemop430 on 2010-06-02
The solutions that were supplied by that thread did not work. "bcmwl-kernel-source" did not show up in the packet manager and I installed b43-fwcutter and it did nothing. The laptop has a wireless button on the front but as far as I can tell, when I press it it does nothing. I've heard of people disabling these from their BIOS, how do I do this?

---

