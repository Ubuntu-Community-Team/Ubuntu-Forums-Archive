---
title: "Broadcom Driver Issues"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by Rico1919 on 2010-01-15
I recently received a friends old Compaq Presario R4000 and was trying to get 9.10 installed but the Broadcom B43 wireless card won't cooperate.  I have read through multiple threads on here as well as many google searches and have not been able to get it working so any help would be greatly appreciated.

With the proprietary driver. the indicator light comes on upon a restart and appears to have some activity (flickers occasionally) but typically does not pick up any SSIDs being broadcast.  When it does, it picks up networks with nonsensical names such as:

%Ïõéâ^S`ªÒ²Ð…úTØ5èÔf‚d˜Ù¨‡uepZŠ

I tried to manually add the network and it either does not pick up anything or it says it connects to the network but has 0% signal strength and receives no packets.  Additionally, the network settings detect that it is an ad-hoc network which when changed to Infrastructure will drop the connection and fail to reconnect.  I have a Compaq R3000 also which uses the B43 driver and connects to the network fine (I have enabled broadcast and removed security for troubleshooting) so I don't think it is a router configuration issue.

I have also tried the ndiswrapper solution, adding several things to the blacklist, and using the bcmwl-kernel-source package with no luck.  Any help in resolving this issue would be greatly appreciated.

-Mike

---

### Post by efflandt on 2010-01-15
You forgot to say what wireless device that computer has (what shows for it in **sudo lspci -v**?).  Different Broadcom wireless devices may use different drivers.  For example BCM4318 in an old Compaq Presario V2000 I have uses Broadcom B43, but the BCM4311 in an older Dell or BCM4312 in newer Dell use Broadcom STA.  I have seen some other BCM devices mentioned, but have not paid attention to what they require.

---

### Post by Rico1919 on 2010-01-15
Both my R3000 and R4000 are using:   Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)  I suspected the generic B43 proprietary driver may have been the issue.  That is why I tried to ndiswrapper solution but then I ran into a whole different world of problems (ssb was an alternate driver and neither the blacklist configuration or manual configurations once in terminal could resolve this issue).  As I said, the proprietary driver at least gets the card responding but is producing these nonsense SSID's and a 0% connection.

---

### Post by Rico1919 on 2010-01-15
After further searching on these forms this morning, a thread was topped linking to this guide:

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

Despite the light coming on on my wireless button, the card was apparently not activated.  Pushing the button did the trick.  I'm still not sure why the strange SSID's were appearing if the card wasn't activated though.

---

