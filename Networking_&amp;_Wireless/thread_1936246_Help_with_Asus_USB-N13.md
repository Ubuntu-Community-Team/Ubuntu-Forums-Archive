---
title: "Help with Asus USB-N13"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by mattj150 on 2012-03-05
Hi, I am using the asus usb-n13 wireless adapter on a ubuntu VM (specifically backtrack 5 r2), but I cannot get the drivers to install. I have tried the drivers that i got from the asus website [http://www.asus.com/Networks/Wireless_Adapters/USBN13/](http://www.asus.com/Networks/Wireless_Adapters/USBN13/). After much monkeying around with those drivers, i was able to get them to compile and install without errors. However the device still fails to show up after a reboot. I tried this but i still got the same results [http://ubuntuforums.org/showthread.php?t=1444746&page=7](http://ubuntuforums.org/showthread.php?t=1444746&page=7). Any ideas? Thanks in advanced. 

```
lsusb:
Bus 002 Device 002: ID 80ee:0021 VirtualBox USB Tablet
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. **
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
 
``````
lsb_release -d
Description:    Ubuntu 10.04.3 LTS

``````

uname -mr
3.2.6 i686

```

---

### Post by chili555 on 2012-03-05
Good job, Asus. There are two different versions of the USB-N13; one is a Ralink rt2870/rt3070 chipset. The other is a Realtek 8192cu device. Apples and oranges.

If you created the files in the link you gave us, delete them. Then check here, especially post #2. Notice the usb.id is identical.

[http://ubuntuforums.org/showthread.php?p=11716409](http://ubuntuforums.org/showthread.php?p=11716409)

---

### Post by mattj150 on 2012-03-05
With a little help from google translate, i installed the driver you linked and it fixed the issue. Thanks for the help!

---

### Post by chili555 on 2012-03-05
Good job! Glad it's working.

---

