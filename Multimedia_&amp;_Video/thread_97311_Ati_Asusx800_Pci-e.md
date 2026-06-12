---
title: "Ati Asusx800 Pci-e"
date: 2005-11-30
forum: Multimedia &amp; Video
---

### Post by uPilot on 2005-11-30
I finished the Ubuntu install, however I cannot get into startx because I get an error "No screens detected" which I can only assume is due to the fact that my video card drivers arent installed. As well, I cant connect to my router, and I figure thats because of a lack of wireless drivers.

The specs:
AMD Athlon X2 3800+
ASUS A8N-E nForce4 Ultra
ASUS AEX800 256MB PCI-E

The situation:
Im stuck in text mode (runmode 3?), and cannot startx nor connect to my router. ifconfig has wlan0 up, and iwconfig can identify wlan0. iwlist scanning cannot pick up my router on wlan0. Through iwconfig, I've tryed modifying ESSID, channel, AP, WEP, etc. Currently, my router's WEP is disabled.

I do not have make command, and my knowledge of Linux is VERY limited. I do have on a USB drive 2 versions of ATI's Linux drivers (off their website), I have the i386 and the x86_64 versions. I also have Linux drivers for my D-Link card, and the make command in .tar.gz However, when I try to install make, I get an error about a C compiler.

I've been stuck in this situation for a few days now, therefore any help is GREATLY appreciated

Pilot

---

