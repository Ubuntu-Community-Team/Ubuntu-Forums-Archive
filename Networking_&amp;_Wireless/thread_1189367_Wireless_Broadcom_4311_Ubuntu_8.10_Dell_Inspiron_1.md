---
title: "Wireless: Broadcom 4311/ Ubuntu 8.10/ Dell Inspiron 1501"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by Dell Inspiron 1501 on 2009-06-16
Hello Ubuntu universe .  I'm just beginning with Ubuntu, and need some help making my wireless work (btw, if any of this would be easier on ubuntu 9.04 i will use that, the only reason im using 8.10 is that i'd thought there might be more support for it).  

I have: 
-A Dell Inspiron 1501 (dual booting XP and Ubuntu)
-AMD 64 processor 
-Network Controller: Broadcom Corporation BMC4311 802.11b/g WLAN (rev 01)
-Ethernet Controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
-kernel/ architecture: 2.6.27-7-generic x86_64

My ethernet doesn't work when i plug it in to the laptop.  I suspect it might be a hardware problem because it doesn't work in windows either.  I have cable.  I know the ethernet is connected because it works when i plug it into my desktop ( an iMac). 

Can you help me get the wireless working without a connection to the internet?  Could i somehow employ a flash-drive and my desktop computer to get the drivers/firmware working?
Is there any more information you that you would need to know?

BTW, I'm looking forward to being part of the Ubuntu Community : )

---

### Post by Ayuthia on 2009-06-16
Option 1:
Here is a link on how to install the files you need to make your wireless card work:
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

Option 2 (easiest):
You might try the following to see if your wired card will work:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe b44
sudo ifconfig eth0 up
```If this works, you can then go into System->Administration->Hardware Drivers and activate the b43 option.

Option 3:
You can also activate the Broadcom STA module from System->Administration->Hardware Drivers.  Once it is activated, instead of rebooting you can do the following:
```
sudo modprobe -r b43 b44 ssb wl
sudo modprobe wl
sudo modprobe b44
sudo ifconfig eth0 up
sudo ifconfig eth1 up
```
If this works, then do the following:
```
gksu gedit /etc/rc.local
```This will open up an editor.  You will need to add the following information before the **exit 0** line:
```
modprobe -r b43 b44 ssb wl
modprobe wl
modprobe b44
```Save the file and you should be set.  This file is run once you are logged in so that it will load the wired and wireless modules in the proper way.

Hope this helps.

---

### Post by Dell Inspiron 1501 on 2009-06-17
Thank you so much, Ayuthia : ) Option 1 works great.  This whole Ubuntu community thing is awesome. 

Would this same procedure by any chance work for Ubuntu 9.04?

---

### Post by Ayuthia on 2009-06-17
It should be the same.  Glad to see it working!

---

### Post by mihai.stancu on 2009-08-24
I have the same configuration "Dell Inspiron 1501 AMD64 Broadcom Wireless 4311", and it worked well with the b43 driver.

My problem is that once the driver was installed i didn't seam to find any preinstalled tool with which to search for and connect to wireless networks.

I tried using Panel > System > Administration > Network Tools, but it didn't work after i unlocked the item and configured the wireless connection nothing happend.

I have succesfully used "RutilT WLAN Manager" i can scan for networks (which i can't do in Network Tools), i can create separate profiles (which again can't be done in Network Tools), only downside is that it has no configuration for wpa encrypted networks, (same as the Network Tools).

Is WPA proprietary how come it's nowhere in sight?

Thanks in advance!

---

### Post by 94_Z28 on 2010-03-13
I used the option 1 method in 9.10 with success. after a re-boot I could see all the wireless networks in my neighborhood and connect to my WPA encrypted network.

Thanks Ayuthia..

---

