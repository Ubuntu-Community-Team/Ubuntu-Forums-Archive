---
title: "Accton WN4201B - DISABLED"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by ahaman on 2006-02-24
Tried the most (at least it feels like it). Desktop system (DELL with PCI card)

iwconfig says NOT READY!

lshw says *-network DISABLED

no green LEDs

Product Intersil ISL3890 (prism ...)

Tried to boot w98se and enabled the card

same situation

firmware downloaded and renamed "und so weiter"

What do i try next?

I have used the WirelessTroubleshooting guide - but that says - google...
(like i didnt try...)

Would prefer not to try ndiswrapper solutions ....

---

### Post by ahaman on 2006-02-24
... som more inf

lspci -v
network controller Intersil Corporation Intersil ISL3890
....
.... unknown device 4203


...

modprobe -l | grep prism
.... prism54.ko
..... prism2_usb.ko                  ???? usb?

ifconfig => says only about lo (local loopback)
(device is eth0) - i have disabled normal ethernet card


lsmod | grep prism                           - says:
prism54 47752 0
firmware_class  9472 1 prism54   (is this the problem? should it say 3890?)

---

