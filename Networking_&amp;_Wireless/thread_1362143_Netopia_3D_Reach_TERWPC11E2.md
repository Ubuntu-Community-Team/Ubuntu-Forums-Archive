---
title: "Netopia 3D Reach TER/WPC11E2"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by jeremey on 2009-12-22
I am installing Ubuntu on a friends laptop who has a Netopia 3D Reach TER/WPC11E2 PCMCIA WLAN card.  I cannot find the .inf file out of the driver files that I can find at driverguide, [http://members.driverguide.com/driver/detail.php?driverid=640155](http://members.driverguide.com/driver/detail.php?driverid=640155), [http://members.driverguide.com/driver/detail.php?driverid=640156](http://members.driverguide.com/driver/detail.php?driverid=640156), or anything on the manufacturers website.

Should I continue working on getting this driver fixed, or just get one that works?

Jeremey

---

### Post by cariboo on 2009-12-23
You will probably have to run the setup on a Windows machine to get the files you need.

---

### Post by jeremey on 2009-12-23
Ok, what I did in case this helps somebody out.  Installed WINE, ran the program off the driver cd through wine, copied TIACXLNX.INF from windows/inf into a folder, (home/wireless driver), as well as copied all the TIA*.bin and TIACXLNX.SYS from the windows/system32/drivers folder into the home/wireless driver folder, then ran system->administration->Windows Wireless Drivers and pointed to the inf file in home/wireless driver and now it works great!

---

### Post by SherriLynnHart on 2010-01-24
I am VERY new to this operating system can you please explain in "Dummy" terms how to do this?
I have WINE Installed and dont have the CD I can download from the internet just dont know what version to use XP Vista or 2000

---

### Post by fagan on 2011-01-14
This sounds like exactly what I'm looking for to get my Netopia 3D Reach USB Card working. Mine is a TER/GUSB2-N but, I am the newest newbie and don't understand the lingo you used in the thread above. How do I find the files you speak off? Do I copy/ paste? Completely lost but, can't load Mint 10 until I have this figured out. Please elaborate. Thanks for your help in advance.

---

