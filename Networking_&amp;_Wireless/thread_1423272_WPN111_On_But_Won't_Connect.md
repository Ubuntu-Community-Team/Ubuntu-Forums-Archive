---
title: "WPN111 On But Won't Connect"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by Shadow21 on 2010-03-06
I installed Ubuntu 9.10 on my desktop computer yesterday and I followed [this]("http://ubuntuforums.org/showthread.php?t=652910") guide to install the drivers for my WPN111 Netgear Wireless adapter. When I was finished following the guide the adapter light was blinking and I was able to connect to the internet just fine. After I turned my computer the next time the light on the adapter was lighting up but there weren't any access points showing up so I restarted my computer and the adapter light still lit up and I was able to connect to the internet again. 

I turned my computer on this morning and adapter light turned on but there weren't any access points showing up again so I restarted my computer a few times and every time I wasn't able to connect to the internet even though it looked like my adapter was on working.

How do I make my adapter connect to the internet every time I turn on my computer?

---

### Post by Shadow21 on 2010-03-08
Bump

---

### Post by ThreeColoursBlue on 2010-07-08
I've been struggling with my own WPN111 but I think I've now got to grips with it.

It seems like the WPN111 driver (or maybe ndiswrapper) doesn't handle reboot/shutdown well, leaving the device in a strange state. So just make sure the power is _completely_ off before starting the PC - note that a PC being 'off' may well leave its USB ports on. So see what happens if you turn off your PC at the wall socket, then turn it back on and start the PC - or just unplug the WPN111 and re-insert it before turning on the PC.

Tell the forum how you get on...

cheers,

Andrew.

---

