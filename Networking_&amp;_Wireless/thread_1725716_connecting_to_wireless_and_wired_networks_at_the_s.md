---
title: "connecting to wireless and wired networks at the same time"
date: 2011-04-10
forum: Networking &amp; Wireless
---

### Post by jimmythegeek on 2011-04-10
I'm using 9.10

I have a local network with storage and a printer that I access with wired gigabit ethernet, but I need to use the wifi card for internet access.  I installed wicd because network manager wasn't handling my smc n2 usb card effectively.  It will only allow me to have one interface or the other enabled, not both at once.  If I enable one in wicd, it disables the other.  I've tried manually configuring, but I don't seem to be getting it right. I'm using static addresses on the wired side, no dhcp, no router.  

The wired and wireless networks are on different subnets.  All the resources on the wired net are on the same switch, should be easy.  No routing needed.  The default gateway needs to be on the wifi net, and dns will have to come from there as well.

I've had multiple interfaces working fine in the past, but they were all wired.  Is there something magical preventing me from using a wireless interface at the same time as a wired interface?  Can I just import the settings from /etc/wicd/wireless-settings.conf to /etc/networking/interfaces under the wlan0 stanza?

---

