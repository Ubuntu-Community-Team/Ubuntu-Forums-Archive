---
title: "Madwifi instalation"
date: 2008-12-15
forum: Networking &amp; Wireless
---

### Post by hotel86 on 2008-12-15
How do I install madwifi  I am an Ubuntu newb so please I need help

---

### Post by hotel86 on 2008-12-18
Bump

---

### Post by hotel86 on 2008-12-18
Ok now I finally got Madwifi installed but for some reason I still cant get a network connection through my wireless connection I have an Atheros AR5418 802.11abgn Wireless PCI Express Adapter on a dual boot vista/ubuntu toshiba satellite with an AMD TL-64 x2.....   Could it be the driver?  Might I need to download and install ndiswrapper?  Or could it be the network manager?

and its probably one of those id 10 t things that Im gonna say doh when i get it figured out but I really need help right now... 

Any help that can be given here would be greatly appreciated...

---

### Post by rixtr66 on 2008-12-18
First wich madwifi driver did you install?
what is the output of
```
sudo iwconfig
```
to do this  you have to open a terminal;applications>accesories>terminal.
i have an atheros pci express chip as well ;this is what i did to make my wireless work;first i downloaded madwifi-hal-0.10.5.6,then i made sure i had build essentials;```
sudo apt-get install build-essential
```
I then uninstalled gnome network-manager```
sudo apt-get remove network-manager
```I then installed wicd network manager [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)
then```
sudo modprobe ath_pci
```then ```
sudo echo ath_pci >> /etc/modules
```
you may just have to install wicd and in prefrences make sure you type in ath0,and onthe wpa supplicant choose madwifi.
I hope this helps!!!!
Rick

---

