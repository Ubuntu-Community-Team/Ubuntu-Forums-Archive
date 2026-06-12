---
title: "Wireless driver on LIVE but not on finished installation"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by Tensdale on 2010-10-17
When I boot the Ubuntu Live CD everything works and after a while I get a popup with Resticted Drivers Available and I can install the driver for my Broadcom Wireless card.
But this only happens on the Live DVD..

When I boot up on my intalled Ubuntu partiton the Wireless is not working. There is now no additonal drivers to install. What the hell?

---

### Post by JackNocturne on 2010-10-17
Well just to be sure ,can you find those **Restricted Drivers** enabled in Synaptic when you boot your installed Ubuntu partition?

---

### Post by fbobraga on 2010-10-17
I've passed trough this before, on a DELL laptop - solved by unblacklisting the *bcm43xx* on */etc/modprobe.d/blacklist.conf* (but, probably there is an easier/better solution)

---

### Post by JackNocturne on 2010-10-17
What **drivers** do you use for your Broadcom chipset? do you use Broadcom 802.11 Linux STA wireless driver?

---

### Post by Tensdale on 2010-10-17
Guys you need to be a little more specific.

Linux noob here.

"solved by unblacklisting the bcm43xx on /etc/modprobe.d/blacklist.conf "

Ahem, you might as well be speaking another language

---

### Post by JackNocturne on 2010-10-17
Sorry ,


[LIST]
[*]We need to know what wireless chipset do you use 
```
lspci | grep -i network

``` type in terminal   ( **Applications>Accessories>Terminal** )
[*]If you know already then check if drivers for it are installed in  **System>Administration>Synaptic Package manager** (search for it)
[/LIST]

---

