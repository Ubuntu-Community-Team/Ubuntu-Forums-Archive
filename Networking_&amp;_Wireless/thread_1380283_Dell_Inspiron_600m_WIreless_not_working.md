---
title: "Dell Inspiron 600m WIreless not working"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by Ishmayl on 2010-01-13
I am new to Linux and Ubuntu.  I have a Dell Inspiron 600m with a Broadcom BRCM1016 wireless card.  I can connect directly to my router just fine, but when I try to connect wirelessly, I have nothing.  At the top, where it shows my connections, the option to connect wirelessly is "grayed out."   I have checked the bios, and my wireless card is enabled.  I ran the command, "sudo lshw -C network," and received back this information:

```

*-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:faffc000-faffdfff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:4f:e2:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```It mentions DISABLED down below, but like I said, in the bios I'm showing enabled.

Now, when I firsts installed ubuntu 9.10, and clicked on "System>Administration>Hardware Drivers," it always showed that no proprietary drivers were available.  However, I recently (just a couple hours ago) updated my Software Sources, and now it is showing that I have a proprietary driver for a Broadcom B43 Wireless Driver.  I activated it, but I still don't have the option to connect wirelessly for some reason.  Is there a stop I'm missing somewhere?

Thanks!
-Ish

---

### Post by bkratz on 2010-01-13
Have you rebooted since installing the b43 driver?

See post 9 of this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Ishmayl on 2010-01-13
Worked!  Thanks, I actually made it to that thread the first time I was looking around, just didn't make it all the way to post 9.  Thanks again!

---

### Post by bkratz on 2010-01-13
> **Ishmayl said:**
> Worked!  Thanks, I actually made it to that thread the first time I was looking around, just didn't make it all the way to post 9.  Thanks again!

Please go to the thread tools and mark as [solved] just in case it helps someone else.




Forgot to say Congratulations!

---

### Post by rumplestilts on 2010-01-26
Thanks to all. Had the same issue this evening with a new (well, new for me but a discarded wreck for the guy who gave it to me) 600m with the same Broadcom adapter. Followed the directions and all is now fine. Again, thanks to all!

---

