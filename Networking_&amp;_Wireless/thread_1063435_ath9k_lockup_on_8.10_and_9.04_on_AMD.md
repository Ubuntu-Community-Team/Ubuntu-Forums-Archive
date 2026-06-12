---
title: "ath9k lockup on 8.10 and 9.04 on AMD"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by kdx7214 on 2009-02-07
I've just updated to 9.04 alpha in hopes that it would correct the ath9k driver bug that causes the system to lock up when running on a system with an AMD X2 4200+ cpu.  I've finally gotten swapped back to madwifi (since that works and is blacklisted for some reason).

I was wondering if, since ath9k freezes so many systems, it will be blacklisted just like ath_pci is 9.04?  Both cause solid system locks (i.e. no SysRq, etc.)  If so instructions *NEED* to be included during the install on how to correct this.  I never found those instructions on the forums but thankfully my google-fu was sound and had results.

I would hope that ath9k would actually be fixed before the feature freeze for 9.04 but it looks like it won't make it.  Any thoughts?  This cost me a great deal of time.

System specs:

MB:  Asus A8N-SLI Deluxe
CPU:  AMD Athlon 64 X2 4200+
Wifi:  D-Link DWA-542 (draft N)
Video:  NVidia GeForce 6800GS OC

Note:  I did try removing the custom NVidia hardware driver (as mentioned on the forums) but that did not resolve the system hang.

---

### Post by phreadom on 2009-03-28
Would you mind sharing your information as to how to fix the lock-up?

I just did a fresh install of the 9.04 64bit beta... the install went smoothly. I booted to the desktop and was pleasantly surprised to see the notification for available wifi connections... clicked on the icon to connect and FULL FREEZE.

Not only that, but even after a reboot the mouse and keyboard no longer worked. I shut down and cold booted and they STILL didn't work. :( !!!!

I booted back into Windows (dual boot box) and everything works fine there. :(

System:
ASUS P6T Deluxe/OC Palm motherboard
Intel core-i7 965EE (quad 3.2ghz) CPU
6GB DDR3 (OCZ Platinum PC3 12800) (3 x 2GB @ 1066mhz currently)
Sapphire Radeon HD 4870X2 2GB PCIE x16
D-Link DWA-552 PCI Wifi (802.11N)

EDIT:

I also tried the same thing with the 8.10 64bit release. Same thing happens. Hard lock of system as soon as you click to connect.

I'll try a few other things and update if I have any luck working around this.

---

### Post by sio2 on 2009-04-10
I have an Asus sr59x and i have the same problem with the ath928x wifi connection. On top of that i can't get any wired connection at all.

So now i have a laptop with no internet connection - like a fish without water!!:mad:

I have tried and installed 8.10 + 8.10 64-bit + 9.04 + 9.04 64-bit.
I have tried the madwifi - no work!
I have tried Volanin compat solutions - no work
I have even installed windows vista ( 1 hour and 35 min!!) I works! but i can't work in windows it is alien and it don't want to do what i want.

So what do i do? 

I'm using an 6 years old Acer laptop (64mb shared grafik card and 256mb ram) that was small to begin with, and next to me i have this useless 4 gb Asus with an just ok grafik card that can only be used as a typewriter!!;)

---

### Post by Free Thinker on 2009-05-03
Mine crashes about 2/3 times that I connect to a wireless network. 

Atheros Communications Inc. AR5008 Wireless Network Adapter

---

### Post by jodiemaceachern on 2009-06-13
I get a kernel panic consistently... These are the steps

After resuming from a suspend, I will experience a kernel panic.
This can be reproduced every time by doing the following steps:
1. Suspend to Ram.
2. Press a key to wake it up.
3. On a console type "sudo apt-get install mc".
4. The package will download correctly, but as soon as it attempts to install it will cause a kernel panic.

I reported the bug with the full information here, including a  photo of the kernel panic:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375257](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/375257)

I would even like to know a good work around so I can use it.

---

### Post by dazer26 on 2009-06-29
Seems like I have the same problem.  Ever since I put a wireless card in my box (D-link DWA-552) Kubuntu 9 locks up about 75% of the time when connecting to the internet, and eventually freezes while browsing the internet.  I tried the new linux Mint and had the same results.  I keep logging on just to download updates and still there seems to be no fix.

AMD X2 3800
2gb Ram 
Nvidia 8600GT
D-link DWA-552 wireless N card
Kubuntu 9.04
Linux Mint 7

---

### Post by Stingxgl on 2009-08-11
I'm having the same problem... Crash on connect to Wireless internet - DWA-542. Is their a way to clear the auto-connect settings from a pre-login prompt so I dont have to keep reinstalling Unbuntu every time I try a new driver/setup? If I could clear the auto-connect during login I could at least login and try new drivers... Thanks

---

### Post by ebharv on 2009-09-02
It seems that there just might be a problem with the D-Link wifi adapters. 
I'm having the same troubles. I've tried 8.10(32-bit), 9.04(32-bit), and 9.04(64-bit). Since
none of them seem to work I'm back to trying to fix 9.04(64-bit). 
I also have the D-Link DWA-552 802.11n.  Every time I connect to my network my system freezes, crashes, then reboots on its own. Has anyone found anything that might possibly be a fix to this.

Side note I'm still kinda new to Ubuntu so if you need like errors logs or something you may have to tell me where to look. Oh, and my router is the D-Link DGL-4500 Xtreme N gaming router of course with WPA.

---

### Post by Paul7777 on 2009-09-02
I have the same issue..
I have tried Ubuntu 9's Suse11.1, PCLinux and lastly the WUBI version of Ubuntu.

My Wireless completely calls it quits...Even Windows Vista quits.(Dual Boot ) It's as if you have no network card. 

The Computer has to be restored. Right now I am not going to put another version of Linux on the machine until this issue is fixed. Any help would be appreciated...

---

### Post by ebharv on 2009-09-03
> **Paul7777 said:**
> I have the same issue..
I have tried Ubuntu 9's Suse11.1, PCLinux and lastly the WUBI version of Ubuntu.

My Wireless completely calls it quits...Even Windows Vista quits.(Dual Boot ) It's as if you have no network card. 

The Computer has to be restored. Right now I am not going to put another version of Linux on the machine until this issue is fixed. Any help would be appreciated...

If you want to use linux then try fedora 11. I was running the 32-bit version a few days ago with no problems out-of-the-box. I just didn't like the appearance of it (blue themes are so played) and some of the functionality, plus I didn't feel like learning a new system so I'm back to ubuntu. Try the fedora live cd and see if it works for you.

Which beckons another question, what drivers does fedora 11 use for wifi adapters? I'll let you all know when and if I find out.

---

### Post by timeking on 2009-10-08
Same thing with Xubuntu 9.10 dev edition. Whenever you select a wireless network and click it, the thing freezes. Not the entire system, just the Network Manager.
 
DWA-552
Celeron 550
512 Mb RAM

---

### Post by ebharv on 2009-11-03
I'm finally back on Ubuntu. Upgrade to Karmic fixed the problems. No lock-ups no crashing. Upgrade when you can. 

It's great to be back.

---

