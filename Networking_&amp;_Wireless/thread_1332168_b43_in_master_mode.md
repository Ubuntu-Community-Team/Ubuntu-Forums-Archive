---
title: "b43 in master mode"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by think2box on 2009-11-20
Hey y'all

As a trial, I bought Asus WL-138g v2 wireless card based on Broadcom 4318 chipset. I installed 32 ubuntu server 9.04 successfully on machine and have disable bcm43xx driver and tried to load b43 driver. My card is not being detected. Here's the exact message 

b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 15, Type 15, Revision 255)

I did all the b43-fwcutter and compact-linux-2.6 steps but the card is not coming up. :( Any comments greatly appreciated.

---

### Post by t0mppa on 2009-11-20
B43 doesn't currently support all Broadcom devices, see their [Linux wireless page]("http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices") for the details.

Just check your PCI-ID and compare it against the table there, [14e4:4315] for instance gives exactly the message you posted and the common solution for it is to use the Broadcom STA driver. Of course, that doesn't work with master mode, since it's one written by Broadcom instead of being an open source one and they didn't bother supporting all the modes.

I did run across a post claiming there was some newer piece of firmware lying around that would make these unsupported chips work with b43 though, so I'll see if I can find the post for you to test.

---

