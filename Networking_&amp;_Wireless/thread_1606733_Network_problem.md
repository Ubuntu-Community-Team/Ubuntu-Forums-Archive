---
title: "Network problem"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by kossploss on 2010-10-26
Hello guys, today i have installed ubuntu 10.10 as a dual boot on my windows 7 laptop. My problem is on windows 7 i can connect internet and do anything and the internet ( wifi boutton f12 is active and everything is fine ) once i got on ubuntu the boutton turn off and i can get to turn it on.. so i am unable to connect to anything... If anyone has a solution tot his problem id be so gratful. Thanks!

overall windows 7 works internet on ubuntu its dosent work :mad:

Wifi card = broadcom 4313 802.11b/g/n

---

### Post by Marinozai on 2010-10-26
Simple solution - you need to install a wifi driver. Go to System>Administration>Additional Drivers and install all the drivers that say "Broadcom" in them (or it is a good idea just to install all of them, there are probably only one or two). 

The only thing about this is that you need an internet connection to install the drivers to get you internet (I know, it really does suck).

---

### Post by kossploss on 2010-10-26
i see haha but how i can get this to work if i dont even have an internet connection on ubuntu..? any other way to make this work ? gotta get this running for school..

---

### Post by Marinozai on 2010-10-26
Gee...that's a toughy. I mean, since you are downloading wifi drivers from the internet...it's not easy to get it without the internet and simply downloading the driver from the Broadcom website and trying to install it is Hell in Ubuntu. I don't know how to install it, but if you want to put this on a USB drive and try to install it on Ubuntu, here is the link: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Other than that, really the only way to get it working is to hook up to ethernet (get hard wired to your internet connection). Where is the ethernet cable in your house? Try hooking up there and installing.

If you can't, then the only thing I can say is to google: "install wifi drivers without internet connection ubuntu"

---

### Post by kossploss on 2010-10-26
alright well what i do once i got my computer plugged to ethernet?

---

### Post by johnnytm on 2010-10-26
[FONT=Arial][SIZE=1]try this ```
ls /var/lib/dkms/bcmwl
```if it shows anything sort of like bcmwl -v 5....... u can use these 2 codes to install the sta driver
```
sudo dkms build -m bcmwl -v 5........+bdcom
```[/SIZE][/FONT][SIZE=1]```
sudo dkms install -m bcmwl -v 5........+bdcom
``` fill in the ........ with whatever driver version shows up in the first command mine shows v 5.60.48.36+ if that doesn't work put in the live cd and add it to syanptic as a repository and search synaptic for bcmwl
[/SIZE]

---

### Post by johnnytm on 2010-10-26
if you are connected to internet either system-->administration-->additional drivers. ONLY install the sta driver DO NOT use b43. or from terminal ```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by kossploss on 2010-10-27
sweet =) its worked thanks guys!

---

