---
title: "nm-applet doesn't show the network activities"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by kapilajayanath on 2009-07-17
Hi,

I've got ubuntu9.04 installed on hp520 laptop. My problem is that the nm-applet doesn't flash/show any network activities. Even when I do *pinging* , it's idle. Please help me to fix this. Please find my ethernet adapter details as follows.

02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
	Subsystem: Hewlett-Packard Company Device 30d5
	Flags: bus master, medium devsel, latency 64, IRQ 20
	Memory at f0101000 (32-bit, non-prefetchable) [size=4K]
	I/O ports at 2000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: e100
	Kernel modules: e100


Thanks,
Kapila

---

### Post by kapilajayanath on 2009-07-20
Hi,

Someone please help me on this. Is this something to do with my ethernet driver?

Thanks,
Kapila

---

### Post by kapilajayanath on 2009-07-22
> **kapilajayanath said:**
> Hi,

Someone please help me on this. Is this something to do with my ethernet driver?

Thanks,
Kapila

I tried installing wicd. The installation was successful. hanBut it also doesn't flash/blink when I do any network activity. Someone please help me on this.

Thanks

---

### Post by Iowan on 2009-07-23
This Gutsy machine doesn't show activity via NM applet, either, but the Network Monitor applet does.  Unfortunately, I can't locate that (network monitor) applet on my Jaunty laptop...

---

### Post by kapilajayanath on 2009-07-24
I installed gnome-netstatus-applet as I got to know that it shows the network traffic/activities. But it doesn't come to the gnome-panel automatically. I tried adding it through "Add to Panel" button but couldn't locate the installed application. Someone please tell me how to add it to the panel.

Thanks

---

### Post by kapilajayanath on 2009-07-28
Hi All,

Finally I got it worked. I tried two network monitoring applets and both of them are working fine now.

sudo apt-get install gnome-netstatus-applet

sudo apt-get install netspeed 

Once you installed any of the above applets, you have to manually add it to the gnome panel. That's it.


Cheers!
Kapila:D

---

