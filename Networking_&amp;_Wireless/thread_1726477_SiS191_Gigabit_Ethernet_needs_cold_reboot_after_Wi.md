---
title: "SiS191 Gigabit Ethernet needs cold reboot after Windows (power saving related?)"
date: 2011-04-11
forum: Networking &amp; Wireless
---

### Post by kiwibird on 2011-04-11
I'm dual-booting Windows XP with 64-bit Ubuntu. The machine has a SiS LAN card (lspci says Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)), which works fine in Windows.

If I turn off the computer, unplug for 10 seconds, and boot Ubuntu, the net connection works perfectly.

If I reboot straight from Windows into Ubuntu, I, oddly, only get access to Google-hosted web sites and some very few others (thought it was a DNS thing at first, but that's definitely not it). Browsing the forums I see some other reports like this, and it seems to be related to the Power Saving feature that the Windows driver uses. I can reboot Ubuntu and still have full connection, but whenever Windows shuts down, it brings the card down with it and I have to unplug to get it back up.

(I assume [http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6](http://www.howtoforge.com/creating-the-sis191-gigabit-ethernet-driver-on-linux-2.6) is an unrelated problem, since modprobe sis190 works perfectly here. Also, some forums mention MTU 1500 not working, but changing to 1492 made no difference here.)

I've tried, in Windows, to uncheck the "Allow the computer to turn off this device to save power", but that seems to have no effect. If anyone knows of where I can make Windows actually stop turning off my LAN card, please let me know!

But the best thing would of course be if I could get Ubuntu to wake it back up fully... I've tried to install the sislan ndiswrapper driver from [http://ubuntuforums.org/showpost.php?p=3284853&postcount=12](http://ubuntuforums.org/showpost.php?p=3284853&postcount=12) but no joy, eth0 doesn't show up when I ifconfig, even though ndiswrapper -l tells me that sisgbe is an alternate to sis190. 

I figured it might be because that sislan tarball was 32-bit drivers, but I can't find the official SiS 64-bit drivers. I downloaded from sis.com/download what they said was 64-bit Win XP drivers for SiS191, but when I ndiswrapper -i that one (WinXP64/NETG654.inf), ifconfig just tells me I now have a wlan0, not eth0...

---

