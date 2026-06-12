---
title: "Xubuntu Lucid 10.4 wifi ndiswrapper usb adapter autoconnect"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by nilou on 2010-05-04
Hi,

I have installed Xubuntu 10.4 (Lucid) on a PC at my uncle's. He is the happy owner of a Netgear wg121 wireless usb-adapter.

I have followed the instructions concerning installation of the ndiswrapper here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

The wg is up and running and everything seems to work perfect... except that, when I reeboot and log in, I have to issue the following commands again, to make the network initialize the wep-encrypted connection. If I do not issue these commands, the wifi-part of the Xubuntu network manager (I don't know the exact name of the program) is invisible in the menu or anywhere on the desktop. (It just says no network where the wifi should be appended). But when I issue these commands in a terminal, then the adapter (wg121) opens and connects to the network:
 
sudo depmod -a
sudo modprobe ndiswrapper

I have tried the command:
sudo ndiswrapper -m
in order to make Xubuntu connect automatically on opening, but no success. When i look through the log it says something about a .conf file, but not which and how, so I'm a bit lost.

I do hope that someone can give me a useful hint or direction.

Kind regards, Mich.

---

### Post by demanzzz on 2010-05-09
I have the same problem with a Netgear PCI device. But how could you follow the instructions you have linked when the versions available do not include one for 10.4?

Is it safe to use the earlier version?

Best of luck in any case.

---

### Post by kachkeis on 2010-05-09
Hi there,

Try this thread, it's for the WPN111 but i heard that it COULD be helping for other Netgear adapters. Or You just use it for inspiration to find a solution.

[http://ubuntuforums.org/showthread.php?t=1477931](http://ubuntuforums.org/showthread.php?t=1477931)

Cheers,
kachkeis :)

---

### Post by demanzzz on 2010-05-11
Thanks, friends, I've got it now. To answer my own question, yes. The existing ndiswrapper DOES work with Lucid Lynx.

Also, it took me a while to spot the instruction that says ndisgtk is included in the installation disk.  Actually, this doesn't help much because the disk also relies on the internet to get the other 2 modules, so I had to download them elsewhere, transfer them to the 10.4 desktop and install them.

This puts the "Windows Wireless Drivers" entry into the Administration menu and it was clear sailing from there. I clicked on "Install" the windows drivers and ignored the part where the GUI suggests it isn't working. Then I just hit the "configure" button and all was well.

Thanks again for the links you directed me to. :)

---

### Post by oimon on 2010-05-19
hi guys
in lucid i've also had some success with installing the package linux-firmware-nonfree
this should mean that ndiswrapper is not required for wg121.

however i'm experiencing occasional disconnects which i'm not sure if they are due to a hardware problem or not. i'm also going to try ndiswrapper to see if it helps. (i'm using WPA encryption)

---

