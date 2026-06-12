---
title: "Ubuntu 11.10 disables WLAN also for Windows 7 ?!?"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by alex-brueck on 2011-11-29
Hello guys,
 
a few weeks ago I installed Ubuntu 11.10 on top of Windows 7 Pro on my laptop, cause I needed it for Uni.
 
First, the installation process wasn't completed successfully and i had to repead it, second: booting Ubuntu takes moreless 5 times longer compared to Win7.
 
But my main problem right now is, that every time I boot Ubuntu, it first doesn't show any WLAN networks AND from that time on, also my Windows doesn't find any WLAN networks anymore! Crazy, but the truth and neither reinstallation of the Broadcom 802.11g-driver or the Windows repair tools solved the problem. 

When this happend first, I had to reinstall Windows 7 and now, lol my nerves .... it happened again after I startet Ubuntu once again. Windows doesn't show any networks anymore.

Please what's going on on my PC and what is Ubuntu doing with my wireless?

Thx and best wishes from Berlin
Alex

---

### Post by praseodym on 2011-11-29
Check the BIOS settings, if there is sth. like "on", "last state", etc.

Ansonsten: [Hier]("http://forum.ubuntuusers.de/forum/internetzugang/") anmelden ;-)

---

### Post by Scott Baker on 2011-11-29
Hi Alex, need some more info to properly address your problem. When you say that you "installed UBUNTU on top of your windows installation", what do you mean? Did you install UBUNTU on your hard drive next to windows (dual boot), or did you install from within windows as a WUBI install? Having this info will help greatly.:p

---

### Post by gordintoronto on 2011-11-29
Then you could tell us the brand and model of your computer. Then open a terminal and run this command: lspci

It should produce about a dozen lines of output. One of them should include "802.11" Copy that line into a message here.

Or perhaps you have a USB wireless adapter? If so, use this command: lsusb

---

### Post by Scott Baker on 2011-11-30
Morning from the U.S. Alex. Since you haven't had the time to respond yet, I'm going to take a quick shot here. I suspect that you may have installed your UBUNTU from the WUBI files directly into your Windows installation. I've personally seen this cause the problems you're describing. IF this is the issue, remove the WUBI installation from your Windows, then see if your Windows installation recognizes the wireless card again. As to installing UBUNTU, you may to install it NEXT to the Windows on your hard drive. Keep us all up to date, and don't worry. We'll get you through this.

---

