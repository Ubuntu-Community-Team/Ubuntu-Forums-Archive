---
title: "Can't get fglrx or tv-out running on RV280 [Radeon 9200 PRO]"
date: 2008-12-26
forum: Multimedia Software
---

### Post by pollywog on 2008-12-26
Hey, I'm trying to set up mythtv to replace the Tivo system that I'm currently running. I've got a Radeon 9200 pro pci card (not express) that has composite and s-video out capabilities, but when I try to use tv-out, I lose the signal during boot, just at the point that X starts. This is happening for all the distributions that I've tried so far (Mythdora, Mythbuntu, Knoppmyth, Ubuntu 8.04, and 8.10). Currently I have straight ubuntu 8.10 installed to try to figure it out. I've read that in may be necessary to install fglrx in order to enable tv-out, but I can't seem to get the driver to install. The open source drivers that come with intrepid work well for my VGA desktop, and can enable advanced desktop effects. When I look in System>Administration>Hardware Drivers, I am told that there is no proprietary driver for this system. I went to ATI's website and downloaded what I believe to be the right driver/installer (ati-driver-installer-8.28.8.run) but installation fails with the error message "unable to locate X server". Next I went to synaptic and installed everything related to fglrx. After that still no video out, and lots of error messages during boot about video problems, low resolution mode only. Fglrx doesn't seem to actually be installing and running. ATI catalyst control center returns error saying that driver is not installed. Tried adding 
```
Section "Device"
      Driver	"fglrx"
```  
to my xorg.conf file but does not force driver to install. I'm limited in video card options as this motherboard lacks an AGP or PCI-E port. Any Ideas?

---

### Post by pollywog on 2008-12-30
bump

---

