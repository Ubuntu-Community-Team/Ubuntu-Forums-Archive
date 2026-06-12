---
title: "Jaunty does not detect my Wifi Card"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by kierpaul on 2009-10-06
Can anyone help me here? When I first installed my Zydas 1215 Wifi card Ubuntu connected to it, but it was slow. I was told to install the Windows driver using ndiswrapper in a forum and I did. After this was done my system lost all capability to detect my wireless card. lsusb does not list it, lshw -C network does not show it being detected either. ndiswrapper -l shows the driver installed. I am at the end of my rope here and I know the USB card is good as I tried it in a Windows Machine and it worked. I also have Wifi Radar installed. Thank you ahead of time!

---

### Post by kierpaul on 2009-10-06
OK I found my problem by going to Places.....Search for files.....searched for zd1211 and checked for the proper kernel. Ndiswrapper never started because it did not have a proper kernel compiled for its driver. The driver for Zydas using the Ndiswrapper is ZD1211bu.inf. The driver that was compiled for Linux, being zd1211rw had the proper kernel compiled so I just uninstalled Ndiswrapper, rebooted, then did a modprobe zd1211rw, iwconfig, ifconfig wlan0 up and my wireless started up nicely (signal was not that strong though). I am under the impression that Ndiswrapper will work if you compile the right kernel. I will do this over the next few days and report back.

---

