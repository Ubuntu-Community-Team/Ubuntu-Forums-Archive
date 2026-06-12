---
title: "slow ubuntu downloads, win 7 downloads work fine."
date: 2013-04-12
forum: Networking &amp; Wireless
---

### Post by goodbye-windows(tm) on 2013-04-12
Hi All,

I have 3 computer systems, 2 linux systems and 1 windows 7 system.

System #1 My primary system, home built, modern ASUS motherboard with FX-6100 6 core processor, Xubuntu 12.10.

System #2 My daughters Dell 15R linux certified compatible, using an i5 processor and Unity 12.04.

System #3 My wife's work laptop, Windows 7, Dell, duo core processor, loaded with security software which is maintained by her employer due to the nature of the content on the hard drive. 

--------------

Background:

Have had poor internet service for the last 5 years, very slow downloads and an ISP that didn't care to dig in and fix their network so it worked properly. 

Recently, they cleaned up their network and it seems to work better, but still not working as well as it should. 

We use a Westell router, all 3 systems are wired with ethernet cables. Have swapped cables, and tested with a different Westell router.

--------------

After the latest round of repairs by the ISP, there are still disconnects from the internet, although much less often than previously. 

But, the internet downloads are about 2/3 of the rated speed on system #1 and #2. So, both Ubuntu systems download more slowly and the download speed is consistently poor (not intermittent). However, my wife's windows 7 computer downloads exactly as it should though!!!! 

The Ubuntu systems download a 20 MB test file from thinkbroadband.com at **3.2 MB per minute**, my wifes Win 7 system downloads the same file at [B]5.3 MB per Minute.

[/B]When I look at the network activity on the Ubuntu machines, **I can see the download speed capped just exactly as it should be, but the data flow stops often, just dropping to zero, sometimes for as long as 10 or 15 seconds.** So, these periods of low throughput appear to be responsible for the slow downloads on the Ubuntu systems. 

I have attached a .pdf showing the network activity of the Ubuntu systems. The data shown is from November last year, but a newer screen capture of the network activity looks identical. I did not obtain a network activity screen capture for the windows 7 machine, but it shows a nearly ruler straight line at .75 Kbits  per second, just as it should be....

I've tried different ethernet cables, a different router, nothing makes any difference. Wireless connections show the same results. 

[B]Does anyone have any idea what might be causing my slow internet download speeds on the Ubuntu systems??????
[/B]
TIA.


Art

---

### Post by goodbye-windows(tm) on 2013-04-16
I have an update.

I tried downloading chromium, download speed did not improve and symptoms of problem did not change.

I tried downloading from the terminal with a wget command, using no browser at all. No change.

I tried changing the MTU from 'automatic' to 1492 and 1500, no change.

I tried disconnecting all the ethernet cables from the router, except for the one going to the computer being tested. Again, no change.

I took my daughters laptop and put it in the car. Visited some local wifi hotspots. All the hotspots I could find downloaded well, without the characteristic drop outs shown in the attached pdf file.

Tried to update the firmware in the router, ISP refused to advise me how to do this (the procedure in the manual doesn't work). 

Everything I can see points to my ISP's network having some sort of incompatibility with Linux, but the actual mechanism causing the failed and slowed downloads remains a mystery to me.

I'd also like to reiterate that this has been a long standing issue with my isp, dating back about 5 years. Something they did to their network very recently made the windows 7 machine function, but both Linux machines fail in the same manner as they always did previously.

Over the years, we had 4 different routers, and 8 different computers on our network. So, it's likely not a router or an incompatibility with a particular computer type/vintage or cpu type.

I should also add that my daughters IPOD exhibits the same type of drop outs during downloads as both linux systems do. Her IPOD and her laptop have been to many many locations with wifi, and only fail to operate when at home on the network at our residence.

I hope someone has an idea what might be going on-I'm (obviously) stumped.

TIA

Art

---

