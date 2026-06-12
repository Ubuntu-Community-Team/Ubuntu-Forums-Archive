---
title: "Asus WLAN 167G"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by H0lyGanGs7eR on 2010-05-03
Hello guys, i have wireless lan adapter Asus WLAN 167G. I see big difference in the speed in Win7 and my Ubuntu10.4 /updated from 9.10/. In the beginning everything was OK, but after some updates my internet is really bad! I tried ndiswrapper but, my network applet stopped showing any wireless connections, i removed network-manager and installed wicd, but wicd shows no connections too. I saw this guide [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) i had made some mistakes, i changed the driver and i got to step 3.5, but when i write ifconfig there is no wlan0... I used the lattest driver from the ralink site and it is installed correctly i think. I don't see where is the problem, please give some ideas or tell me how to move back on network-manager and linux drivers.. 


PS: I changed the names ~/ndiswrapper to ~/ndiswrapper.conf and moved the text from ~/blacklist to ~/blacklist.conf

PPS: I have WPA key secure on my connection.

---

### Post by H0lyGanGs7eR on 2010-05-03
When i write this command i i got nothing ```
*lshw -C Network*
``` just new line.... Please help me, i switch for 12th time ubuntu/windows, give some ideas how to do it, or if you can't help me please tell how to start my internet with the linux driver again :( The linux driver is rt73usb

---

