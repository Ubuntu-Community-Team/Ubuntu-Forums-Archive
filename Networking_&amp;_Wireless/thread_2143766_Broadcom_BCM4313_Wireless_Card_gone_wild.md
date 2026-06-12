---
title: "Broadcom BCM4313 Wireless Card gone wild"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by Yasashii on 2013-05-10
Hello.


A few months ago I bought an Acer Aspire One 722 netbook. On the first run I installed Windows 7 (since it had Linpus Linux with no GUI pre-installed) and I installed all the drivers. After some time I decided to use Xubuntu 12.10 and I was happy with it. It automatically installed the proprietary driver for the wi-fi card and all was good.


The trouble came when Ubuntu 13.04 got released and I decided to look for another distro since the one I was using was out of date and not as fast as I had wished anyway. I've installed Manjaro Linux and everything worked nicely until one time I went downstairs for a moment and came back to see my screen blanked out (default power settings), which was normal, and... my wi-fi led turned off. The internet still worked but now the led wouldn't light up no matter what. I figured that it must have burned out or something so I ignored the problem.


I realized the problem was more serious when I decided to try Lubuntu. When the installer asked me to connect to a network, at first it connected properly and then, when I wanted to continue the installation, it probably downloaded and installed the proprietary driver, because the led switched on but the installer tried to connect to my network over and over again unsuccessfully.


To get a better idea of what's going on I installed Xubuntu 12.10 again (because the wi-fi card worked fine on it before) and checked the wi-fi driver selection in software sources>additional drivers tab. It turns out, the internet works fine when the selection is "Do not use the device" (which, by the way, was NOT selected all the time while I was using the system before the problem occured), the internet works but the led doesn't light up, and when I select "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source", the led lights up but I can't connect to my network (despite it being visible on the networks list).


I decided to go even further back in an attempt to fix the problem. I remember that whenever I turned on the netbook, the wi-fi led lit up every time even before the system loading screen (and it doesn't now). I also remember that the very first time I turned on the netbook, it also didn't light up. It started lighting up only after I've installed the broadcom driver on Windows 7 for the first time. I deducted that the driver must have also installed some kind of internal driver or firmware onto the device and for whatever reason that firmware now doesn't work. Turns out I was right. Debian installer reported bcm43xx-0.fw firmware missing before network configuration. That's the firmware for my wi-fi card.


I hoped that if I installed Windows 7 again and installed the driver once more, the firmware would get installed with it again, just like it did the first time. But, unfortunately, it didn't. The led doesn't light up before the Windows loading screen, it only lights up after that and the internet works with the led lit up but only on windows. The problem remains unchanged when I try to install any linux distro again.




Can anyone tell me how I should install the firmware itself? (no matter on what OS. Whichever is required, I will install it).


I've read that the Broadcom cards are not exactly the most reliable ones so I'm considering getting a new wi-fi card but then again this seems like it might be a software problem so if it can be fixed and save me some money, it would be great.


ps. I know it might not exactly be a Ubuntu-related problem, especially since the problem first occurred on Manjaro Linux, but then again it also occurs on Ubuntu and its derivatives so... please help?

---

### Post by Yasashii on 2013-05-10
Yes it can. I've done my research before posting this thread and I've seen many people with the exact same problem as you and the same wi-fi card.

---

### Post by stefanokan on 2013-05-10
i have the same card. i solved the problem deactivating the sta driver and installing this:
sudo apt-get install firmware-b43-installer

---

### Post by stefanokan on 2013-05-10
of course you have to reboot after installing it.

---

### Post by Yasashii on 2013-05-11
Unfortunately, that doesn't solve the problem.

---

