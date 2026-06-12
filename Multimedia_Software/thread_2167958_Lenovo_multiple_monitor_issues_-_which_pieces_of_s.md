---
title: "Lenovo multiple monitor issues - which pieces of software are relevant?"
date: 2013-08-15
forum: Multimedia Software
---

### Post by ArlieS on 2013-08-15
I am cursed with a lenovo laptop. It has a docking station with two external monitors attached to the dock. It's dual boot, windows 7 and Ubuntu 12.10 (previously 12.04) 

It's been a PITA from the day I got it. It variously forgets the existence of one or more monitors, comes up in low graphics mode, reports errors on resume, and reports crashes of programs like compiz. Sometimes it gets confused when idle, and recovers when undocked and redocked. Sometimes it works fine for weeks at a time - then loses it when docked/undocked.  Often it loses it on reboot, but eventually gets it right after multiple reboots, not all of them on the then-current kernel. One time it got unconfused when I used the Unity GUI tool to make all monitors mirrored, and didn't accept the change. The next time I tried the same gambit, it went from bad to worse, resulting in a hard reboot. (Hard reboots pretty much reliably result in it coming back up in low graphics mode, or worse.) 

Windows 7 had some trouble originally, which was fixed by a driver upgrade - until last week, when Windows began showing similar symptoms. I gleefully turned it over to IT, who swapped docks and monitors without success, and finally called in Lenovo, who replaced the mother board. 

Now Windows is working fine, but Ubuntu is only reliable on the laptop's own screen, in rescue mode (without graphics). I get similar misbehaviour when I boot from the 12.10 install DVD - making it less likely that it's either an unfortunate update or a now-inappropriate configuration left over from the prior motherboard. 

OK, so much for the long setup. My questions are pretty straightforward -

- what's the division of labour between kernel, X server, compiz, and other parts here? 
- where do I find error logs and configurations for each relevant part - accessible from a non-GUI shell window, if at all possible?
-which of these parts might have the smarts to reconfigure based on my hardware, if asked, and how would I ask it? (I tried "sudo dpkg-reconfigure ..." of various relevant seeming packages, without any luck ... or any visible output. 

I fear I'm going to find out that the new mother board is (a) not the same as the old and (b) even less linux friendly, and there's no way I can run linux natively on this POS. But I don't want to decide that without a bit more information.

---

