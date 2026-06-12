---
title: "will you please help me?  Can't get Broadcom wireless working"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by hotpinkflamingo on 2009-11-28
Hello,
I just installed Ubuntu on my daughter's laptop.  She's got an Acer with a Broadcom wireless modem.  It's the exact modem on this page:
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

04:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I can't follow the directions on that page.  I don't know how to install b43-fwcutter.  I've got the laptop on a wired connection right now, and I can't find that in the synaptic package manager.

I've been searching all over the forums, and have tried many things and I just can't do it.  Will someone please help me?

In the restricted drivers area, when I try to select the "firmware for Broadcom...", I get a message saying "the software source for the package "bcm43xx-fwcutter" is not enabled.

---

### Post by RedSingularity on 2009-11-28
In a terminal do 

sudo apt-get install b43-fwcutter

See if that works for you.

---

### Post by hotpinkflamingo on 2009-11-28
That worked.  Thank you very much.  :D

---

