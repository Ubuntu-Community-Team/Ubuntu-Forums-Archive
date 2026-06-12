---
title: "Belkin F5D8053 v6 working in Karmic!!!!!"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by lokonai on 2010-04-07
Hello, I'm quite new in ubuntu, but I tried to work my Belkin F5D8053 USB wireless in Karmic. I read a lot and finally, I got the solution.

This is what I did:

1) Install Karmic and update it (I used my internal wireless card Intel 5100)
2) Install ndiswrapper (you can do it from terminal with apt-get or in the Synaptic Manager on System menu)
3) Install WICD (network manager software) from Synaptics (it will automatic replace the default Ubuntu Network Manager) VERY IMPORTANT to change to WICD!!!
4) In console type:
[INDENT]sudo su (and write your password)

ndiswrapper -i driver.inf 
(I took the driver from windows hard disk in Program Files/Belkin/F5D8052/v6/Driver/XP_x86/net8192su.inf, but you have it in the original CD of Belkin) For starters, you can take the file with mouse and drop inside the console window to copy the route.

ndiswrapper -m

depmod -a

modprobe ndiswrapper

[/INDENT]5) Go to System/Administration/Network Tools and you will check that new wlan1 is available (wlan0 in my case is Intel 5100)

6) Reboot and** open WICD** (I still have to solve a little problem with modprobe, because I have to do modprobe ndiswrapper when I reboot to start wlan1....any help??)

7) In WICD preferences, change wlan0 for wlan1 
8) In Preferences/Advanced Settings change driver to **atmel**
9) Choose your net and conect Enjoy Internet!!!

Hope it will help anyone. :guitar:

---

