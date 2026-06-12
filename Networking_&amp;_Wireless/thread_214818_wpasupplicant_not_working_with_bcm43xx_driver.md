---
title: "wpasupplicant not working with bcm43xx driver"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by finite9 on 2006-07-13
I have Ubuntu 6.06 amd64 with a Broadcom 4318 (AirForceOne 54g) controller.

I have successfully had this working with ndiswrapper and wpasupplicant from the repositories, but I wanted to get it working with the new in-built bcm43xx driver.

I got the bcm43xx driver working and I can scan for APs, but when trying to get wpasupplicant working with the driver, I realised that wpasupplicant has its own internal driver database (inc. broadcom, madwifi, ndiswrapper, etc), but specifying "-Dbroadcom" on the command line said that the driver was not supported.  It seems like there needs to be driver support within wpasupplicant for the new bcm43xx driver.  Is this assumption correct?  This is a real shame, because I was really hoping to be able to use the new bcm43xx driver.

--finite9

---

### Post by fabiand on 2006-07-13
Hey,

you will need at least wpa_supplicant v0.5.0, that means, you will have to compile it by yourself :)

In generall the quite new bcm43xx is not fully supported yet.

---

### Post by finite9 on 2006-07-13
Do you know which driver I need to specify when running wpasupplicant 0.5.0 if I compile it??

---

### Post by finite9 on 2006-07-17
Well, I got it working, and I didn't need wpasupplicant0.5.0...

I use the wpasupplicant and bcm43xx driver that exist in the main respositories, and the way to get wpasupplicant working is to specify the driver for general linux wireless extensions:

sudo wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf -Dwext -w

and then get an IP address:

sudo dhclient eth1

After getting the bcm43xx driver itseld working, those 2 lines were all that were required to get WPA working, but I havent figured out how to script it yet.

---

### Post by fabiand on 2006-07-20
hmm . good to know :)

---

