---
title: "Lag in games"
date: 2009-03-31
forum: Multimedia Software
---

### Post by sourya_s7 on 2009-03-31
Hey all...
I'm trying to run a game (assault cube) on ubuntu. The game has native linux binary. The problem is that the game used to run smoothly on windows but there is a great performance lag when run on linux.

I have a Dell Inspiron 1410. lshw -C display gives:

        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
I guess this means the intel driver is not installed. But the compiz effects does run(with performance lag again). And i guess compiz requires these drivers so they must be installed.Also, i checked out synaptic.It also says the intel drivers are installed.

Here's the xorg-conf

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Well, I guess, yes xorg is not configured to use the intel drivers. I could have played with this file but i got scared. I read a tutorial on xorg and it said playing with these values may 'smoke' your laptops and i really dont want that to happen .Please tell me what to do..(by the way "sudo dpkg-reconfigure xserver-xorg" does not help) 

Thanks.

---

### Post by Melcar on 2009-03-31
Open source drivers are much slower than their Windows counterparts.  There's your lag.

---

