---
title: "Help! No Wireless or Wired Connection and Have tried dif. methods"
date: 2010-08-14
forum: Networking &amp; Wireless
---

### Post by V13 Noob on 2010-08-14
I bought a Acer one 721 netbook and deleted Windows 7 and installed 10.04 UNR and haven't been able to connect to my connection, wired or wireless, which is working on my desktop and was working on the netbook when Windows 7 was installed. The network manager doesn't detect any signal, nor from the wired connection. The terminal says ''UNCLAIMED" which Ubuntu help tells me that the drivers are not installed. Ive been trying to work on the wireless connection and this is what I've done: I've installed ndiswrapper common, ndiswrapper and ndisgkt, from the live cd. I have the drivers for the netbook and they come in three folders but ndisgtk ask me to load the driver Im unsure which one to load, there is a Broadcom folder with one .inf file and the one loads and installs fine, the other two folders have two .inf files each but they're identical. When I install one it says OK but hardware not found, the other one doesn't install at all.  My wireless card is AR8151 v1.0 Gigabit Ethernet. I worried because I think I jumped ahead of myself by deleting Windows 7 and not making recovery disks. Though if Ubuntu UNR works I'll never need them. Please any help would be greatly appreciated. And any info you might need from me just ask. Thanks.

---

### Post by Grafens on 2010-08-14
Linux doesn't load drivers for certain cards, I think it's got to do with open software or something. Anyway you could google for the specific drivers you need from your laptops website, load them onto a usb stick or cd then goto System > Administration > Hardware Drivers and point it to the usb/cd folder.
Hope this helps

---

### Post by V13 Noob on 2010-08-14
yea i tried that at first but it doesnt have an option to choose where to select the drivers from. I have a Broadcom wireless card [14e4:4357] (rev 01). Ive also tried the mothods described here [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) but the first method it wont let me install bcmwl-kernel-source and the second method didnt do anything though everything seemed ok. Im going to try installing UNR again and try method 2 again since maybe some of the drivers i had but before messed it up or something but Im desperate for any aid. Thanks for any info.

---

### Post by V13 Noob on 2010-08-14
Can anybody help? Nothing has worked and i think im now going to get a copy of window 7 or sytem restore from acer. Id much rather have ubuntu though, can anyone help?

---

### Post by V13 Noob on 2010-08-14
Also I just discoverd my Broadcom card is BMC43225.

---

