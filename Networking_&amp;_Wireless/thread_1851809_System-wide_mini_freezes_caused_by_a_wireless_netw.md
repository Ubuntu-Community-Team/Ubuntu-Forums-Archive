---
title: "System-wide mini freezes caused by a wireless network?"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by Maximus559 on 2011-09-29
This thread's title can be a little confusing. Let me start from the beginning...

About a week ago, I moved my desktop PC from my house to my college dorm. The machine in question is a Dell Dimension 4500 with a 1.8 GHz Pentium 4, 1 GB of RAM, a Geforce4 MX420, and a Trendnet TEW-443PI PCI wireless adapter (revision A1.1R). It currently dual boots Windows XP and Ubuntu 10.04, and had no problems prior to the move.

Upon arriving at my dorm and setting up my computer, I almost immediately noticed an odd little problem: the system seemed to have developed a nervous tick. From time to time, the entire system will freeze up for a fraction of a second, then continue on as if nothing had happened. These ticks often occur in clusters, and vary in frequency from several in a minute to one every few minutes. The freezes make themselves apparent during many activities, including mouse cursor movement, YouTube video playback, CD audio playback, typing, and animated screensaver display. To be clear, **nothing** appears to be happening during the brief periods that the system is locked up. If a freeze occurs while I am moving the mouse cursor, the cursor will stop moving, then begin moving a split second later. It will **not** jump from one location to another, a behavior which would indicate that the system was continuing to process input while the display was unresponsive.

After doing some basic troubleshooting, I've traced the problem to my wireless internet connection. The only way I can reliably induce a freeze or series of freezes is by disconnecting and then connecting to the school's free wireless network. If I disconnect from the network and stay disconnected, the intermittent freezes continue; however, if I disable networking entirely, the freezes cease. Incidentally, the school's wireless network is very slow and unreliable, and I am now using a roommate's private network. This does not prevent the freezes, however, as it seems I need only be in range of the free wireless network in order for this problem to occur.

So... yeah, I'm kind of stumped at this point. I can't disable wireless, as I need to be able to connect to my roommate's network (wired Ethernet is a no-go for a number of reasons.) Is there any way that I could tell Ubuntu to completely ignore the free wireless network - as in, not monitor it at all and pretend it doesn't even exist? Is there any other way I could solve this problem? Any pointers at all would be much appreciated.

---

### Post by Maximus559 on 2011-10-01
Any ideas?

---

### Post by kinggo on 2011-10-01
have you tried with some other wifi card? Some cards doesn't work good with some routers. I have linksys router that doesn't like intel cards. It connects normally at first try and everything seems to be fine but after a while the whole wifi network gets locked. Wired net work fines but wireless is dead for all devices. I can see the network but that's it, no way to connect to it or do anything else and the only thing that helps is to reboot the router. After replacing intel card with broadcom from my old hp I never had any problems again. Not once. 
Remove your PCI card and try with some USB wifi stick.

---

### Post by Maximus559 on 2012-02-23
For reference, upgrading to Xubuntu 11.10 solved this problem. Never did find a fix for 10.04, though.

---

