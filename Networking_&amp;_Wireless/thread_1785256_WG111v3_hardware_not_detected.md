---
title: "WG111v3 hardware not detected"
date: 2011-06-18
forum: Networking &amp; Wireless
---

### Post by Lelephant on 2011-06-18
Hi, I'm pretty new to Ubuntu so this might be an obvious mistake but I can't find a solution anywhere. I'm trying to install my WG111v3 usb wireless adapter on Ubuntu 10.04.2 LTS 32 bit. I found the .inf for it and installed it with ndiswrapper ("Windows Wireless Drivers"). It says that the driver is installed but "Hardware present: No". 

When I type 'iwconfig' I get:
lo       no wireless extensions.
eth0     no wireless extensions.

I'm running Ubuntu through VM VirtualBox. I'm not connected to ethernet (windows recognizes my adapter) but I still have internet access in ubuntu.

When I type 'iwlist scan' I get:

lo       Interface doesn't support scanning.
eth0     Interface doesn't support scanning.

When I try installing the usb drivers for my motherboard through the same method of installing the .inf with ndiswrapper, I get the same "Hardware present: No". 

Please help, I'm completely lost.

---

### Post by nbound on 2011-06-18
Plz post the output of the command: lsusb

---

### Post by Lelephant on 2011-06-18
lsusb gives me:

Bus 001 Device 002: ID 80ee:0021  
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by nbound on 2011-06-18
The device is yet supported natively, you need to use ndiswrapper and the **XP Driver** (not 2000, not Vista, Not 7) check this is what you are using, you should uninstall the drivers you've previously added to nidswrapper. For future reference adding your USB drivers wont help.

---

### Post by Lelephant on 2011-06-18
I installed the driver to my desktop, but I just have what's shown in the attached photos:

desktop:
[http://s1207.photobucket.com/albums/bb477/lelephant5/?action=view&current=desktopubuntu.png](http://s1207.photobucket.com/albums/bb477/lelephant5/?action=view&current=desktopubuntu.png)

Inside OEM folder:
[http://s1207.photobucket.com/albums/bb477/lelephant5/?action=view&current=desktopubuntu.png#!oZZ2QQcurrentZZhttp%3A%2F%2Fs1207.photobucket.com%2Falbums%2Fbb477%2Flelephant5%2F%3Faction%3Dview%26current%3Ddesktopubuntu2.png](http://s1207.photobucket.com/albums/bb477/lelephant5/?action=view&current=desktopubuntu.png#!oZZ2QQcurrentZZhttp%3A%2F%2Fs1207.photobucket.com%2Falbums%2Fbb477%2Flelephant5%2F%3Faction%3Dview%26current%3Ddesktopubuntu2.png)

No .inf to use with ndiswrapper.

---

### Post by nbound on 2011-06-18
found that info may have been incorrect, ive tracked down a driver module that supports it.

[http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187)

though it may need some tinkering to support as the device code is different.



```
modprobe rtl8187
``` may get it working temporarily. YMMV

---

### Post by Lelephant on 2011-06-18
I did this to get the driver from the website:

[http://pastebin.com/vTENEjXq](http://pastebin.com/vTENEjXq)

it saved a rtl8187 html document in my home folder.

Then, I did modprobe and got this:

[http://pastebin.com/NHHjiAAA](http://pastebin.com/NHHjiAAA)

Did I download the driver incorrectly? I don't see a download link on their page.

---

### Post by nbound on 2011-06-18
try **sudo modprobe rtl8187**, u dont need to "get" the driver its already there, waiting to be unleashed :P (by the looks anyway).

---

### Post by Lelephant on 2011-06-18
Tried it, same result. Someone in IRC told me to use an aircrack live cd, which I'm attempting to do now.

---

