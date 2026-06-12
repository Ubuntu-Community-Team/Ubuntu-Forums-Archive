---
title: "Connecting to AP causes crash on Toshiba Satellite C655D-S5138"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by dexterowns on 2011-07-15
When I'm running Ubuntu everything seems to work perfectly until I try to connect to a wireless network. My wireless card supposedly works out of the box because I can scan for wireless networks without a problem. The only time it becomes a problem is when I try to connect to a wireless network. Doing so causes my computer to freeze, requiring a hard-restart. I disabled the driver that comes with Ubuntu, and installed ndiswrapper with my card's corresponding windows driver. As soon as I modprobe'd ndiswrapper, my computer froze as it did before and required a hard restart. This was about a month ago, and since then I have tried OpenSUSE and Fedora, but these distros also did the same thing. I eventually gave up and installed Windows 7 and everything works perfectly. However, I'm now growing tired of using Windows. (I do a lot of linux server administration, and it's much nicer to do from a linux machine.) I would very much like to try to get Ubuntu working on this laptop again. Does anyone know what the solution may be?



EDIT: If you are experiencing the same problem, DISABLE your PCI LAN card in your BIOS. Wireless should work fine. Seems that the LAN and WLAN card have a similar ID or something and linux confuses the two, so disabling LAN card solves the issue of not being able to use the wireless.

---

### Post by dexterowns on 2011-07-15
bump

---

### Post by dexterowns on 2011-07-16
Does anyone have a clue?

---

### Post by crh0831 on 2011-07-18
I don't have an answer, but I wanted to put my .02 in to say that I'm having a similar problem.  Same machine, same Ubuntu distro.  

Nothing that correlates to the freeze though.  I can connect to AP's or connect via ETH1.  When it's not frozen everything works fine.  Sometimes it works great for almost an hour and then all of the sudden... freeze.  Nothing to do but hold down the power button and reboot.

I've also tried a couple different distros (crunchbang 10 and Ubuntu 10.04 LTS) with similar results.  I can't even find evidence of anything in the logs (I don't even know where to look)

Anyway - I'm subscribing to this thread in the hopes that somebody responds.  If I figure anything out - I'll be sure to post here.

NOTE: oops... I just noticed that my unit is a C655D-S5210.  So, it's not the same exact machine.  Similar problems though.  Maybe they're related?

---

### Post by dexterowns on 2011-07-20
I'm almost certain it's the wireless. I was having trouble installing openSUSE on my machine. It kept freezing at the same percentage every time. I checked the disk and everything checked out. So the next time I tried, I disabled the driver before installation...voila. The machine runs beautifully with Ubuntu installed...as long as the wireless driver is disabled lol. It's extremely annoying...I've tried everything. Most people with Toshiba laptops complain about their wireless card not being recognized...well my problem is that it's recognized but doesn't work. :confused: I would really love to get this working! I'm still in the same situation...Linux doesn't work on this machine. No distros I've tried at least. So confused. Guess who's not buying another Toshiba...lol

---

### Post by dexterowns on 2011-07-22
Bump

---

### Post by dexterowns on 2011-07-28
Bump

---

### Post by dexterowns on 2011-08-31
Bump

---

### Post by praseodym on 2011-08-31
You may try "acpi=off" as a boot parameter, or you may reset your BIOS?

---

### Post by dexterowns on 2011-09-17
Doesn't seem to do anything. Still unable to install Ubuntu on this brand new machine.

---

### Post by dexterowns on 2011-09-21
Bump

---

