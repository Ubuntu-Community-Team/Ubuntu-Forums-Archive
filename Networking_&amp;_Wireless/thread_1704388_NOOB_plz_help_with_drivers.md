---
title: "NOOB plz help with drivers"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by jamiegrant01 on 2011-03-10
I've read the guide on the networking cards but i still dont understand the madwifi stuff. i have XP right now but i want to install ubuntu, and i need to know what i will have to download before i do so that i can put the files on a flashdrive, because if my wireless card doesnt work i wont have internet connection. It is a belkin g wireless desktop card f5d7000 v5000. Then what do i need to do to install the driver? Ubuntu is confusing...
thanks :D

---

### Post by Kreindhild on 2011-03-10
Hi,

I'm another noob in Linux, but I will try to help you out. I have yet to see a wired network card that doesn't install properly in Linux. If your wireless card needs a driver, you will be able to install it from the System > Admin > Additional Drivers. You may need to plug the ethernet in before the option will appear in additional drivers, but sometimes you can see it offline. I would recommend downloading a live cd of linux and putting that in your computer. Once you are booted into the OS, plug an ethernet cable in, and see if the additional drivers shows your wireless card. If it does, you are set and the OS will help you install the drivers once you have the base linux install on.

If you are still worried, I would use System > Admin > Gparted from the live cd to partition another spot on your hard drive. I would install Linux there, and do a dual boot, get all the drivers installed and everything running, then remove windows and then you will know for sure it will work... If it doesn't work, you don't lose your windows part, and it didn't take up your whole hard drive. I wouldn't recommend deleting the linux partition until the GRUB loader has been disabled.

---

### Post by chili555 on 2011-03-10
I believe your card uses the driver ath5k. I also believe it's installed by default. You can find out by running the live CD and opening Applications > Accessories > Terminal and typing:```
modinfo ath5k
```If it is present, you will get lots of data; if not, it will tell you the module is not found. Post back if we can help you further.

---

