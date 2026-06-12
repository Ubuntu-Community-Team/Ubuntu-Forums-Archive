---
title: "Karmic+ndiswrapper works in clear but cannot WEP"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by karger on 2009-12-31
I'm trying to install Karmic for a friend on an old thinkpad a22p. I've gotten it working except for WEP.  He has an old Netopia 3d Reach wireless card (acx 110 chipset).  The card handles WEP fine when I boot the laptop in windows.  I installed ndiswrapper and gave it the same windows driver, which allowed me to connect under Karmic to an open network without problems.  However, when I enable WEP on the network, the laptop can no longer connect.  It sees the card ("iwconfig wlan0" shows it present) and sees the network if I "iwlist scan".  However, "dmesg | grep wlan0" shows the troubling line "wlan0: encryption modes supported: none".  

I've trawled the net and found many similar complaints, but none that suggested solutions that worked for me. I'm not sure if this is a chipset-specific problem; how can it be when I am using the windows driver that handles this chipset just fine?

I'd love to leave my friend with a working laptop when I fly home sunday, so any advice would be greatly appreciated.

Thanks!

---

