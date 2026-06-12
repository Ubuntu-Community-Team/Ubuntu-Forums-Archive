---
title: "Nvidia vs ATI and my results!!!"
date: 2011-08-05
forum: Multimedia Software
---

### Post by kcraptor82 on 2011-08-05
So I have been dealing with this for awhile and I finally come to a conclusion. ATI just sucks for Linux! Nvidia is so much better, and now I regret even buying ATI products!! I have noticed on many things between my three systems running Ubuntu 11.04 x64. I have been trying to play World of Warcraft on these machines, and only having luck with one of them. Sad thing is, its my laptop that plays WoW perfect!!!! 

Please note: Settings in game were set at lowest!

Server Box:
Ubuntu 11.04 x64
AMD Athlon x2 2.6Mhz
ATI Radeon HD 4200 - Onboard HDMI out to 42" LCD (1440x900)
4GB DDR2 Ram, 160GB Sata Drive

Directx Mode = 10fps in Stormwind
OpenGL Mode = 11fps in Stormwind
Game lags really bad on exit!!!

Main Desktop:
Ubuntu 11.04 x64
AMD Athlon x4 2.6Mhz
ATI Radeon HD 5770 - 1GB PCI-E out to dual DVI 20" LCD (1600x900)
8GB DDR2 Ram, 500GB Sata Drive

Directx Mode = 10fps in Stormwind
OpenGL Mode = 11fps in Stormwind
Game lags really bad on exit!!!

Laptop: Acer 8930G
Intel Core 2 Duo 2.0Mhz
Ubuntu 11.04 x64
Nvidia 9600M GT - 512MB dedicated to 18.4" LCD (1680x945)
4GB DDR3 Ram, 320GB Sata Drive

Directx Mode = 15fps in Stormwind
OpenGL Mode = 15fps in Stormwind
Game runs perfect, no lag on exit to character screen, etc!!!!

From what you can see, my laptop runs it better then both my desktops! WTF???? So anyone have any ideas how to make ATI work better or they suck that bad?

---

### Post by lkjoel on 2011-08-06
This is probably because you have the Open-Source ATI drivers (comes default in Ubuntu).
Try this in a Terminal window:
```
sudo apt-get install fglrx

```
And reboot.

---

### Post by kcraptor82 on 2011-08-06
I did try what you suggested, but I guess I alraedy have the latest installed. I did activate the ATI/AMD proprietary FGLRX graphics driver that you can activate by going into the additional drivers section. When I try to do your suggestion I get this:

raptor@server:~$ sudo apt-get install fglrx
[sudo] password for raptor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
raptor@server:~$

---

### Post by lkjoel on 2011-08-06
> **kcraptor82 said:**
> I did try what you suggested, but I guess I alraedy have the latest installed. I did activate the ATI/AMD proprietary FGLRX graphics driver that you can activate by going into the additional drivers section. When I try to do your suggestion I get this:

raptor@server:~$ sudo apt-get install fglrx
[sudo] password for raptor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
raptor@server:~$
Try this:
```
sudo dpkg-reconfigure fglrx
```
Then reboot.

---

### Post by PIDGINZ on 2011-08-07
You can't base this simply off of one game/application. You need to test more to make an accurate conclusion. Some games run better on ATI than on nvidia, while others run better on nvidia than ATI.

---

### Post by Claus7 on 2011-08-07
Hello,

first of I was content with both nvidia and ati, even though my experience is limited in a couple of cards and not a whole bunch of them. Yet, every time I was trying to get every single drop of capacity my card had to offer.

Concerning your question, I guess that in order to make an ATI card to work pretty decently in gaming, you have to install -at the time- the proprietary drivers found on AMD's website. I think also, that doing so, you might find a difference in performance between your different ati cards. That is my guess.

Happy ubuntuing,
Regards!

---

