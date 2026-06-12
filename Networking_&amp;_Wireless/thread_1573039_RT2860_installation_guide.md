---
title: "RT2860 installation guide"
date: 2010-09-12
forum: Networking &amp; Wireless
---

### Post by Darvenkry on 2010-09-12
Today I finally fixed my new Asus PCE-N13 wireless card which is a rt2860, so I thought I'd document what I did. At first I had problems with not using 802.11n and continuously dropping the signal.

So first off go to the ralink site and download the newest driver:

[http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpFMkwyUnZkMjVzYjJGa05qZ3hPRFUwTmpBd05DNWllakk5UFQweU1ERXdYekEzWHpFMlgxSlVNamcyTUY5TWFXNTFlRjlUVkVGZmRqSXVOQzR3TGpBdWRHRnlD](http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpFMkwyUnZkMjVzYjJGa05qZ3hPRFUwTmpBd05DNWllakk5UFQweU1ERXdYekEzWHpFMlgxSlVNamcyTUY5TWFXNTFlRjlUVkVGZmRqSXVOQzR3TGpBdWRHRnlD)


Follow the README to install. Note, edit os/linux/config.mk to 
    HAS_WPA_SUPPLICANT=y
    HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

Now "make install" doesn't work so just:
cd (_PATH TO_)/2010_07_16_RT2860_Linux_STA_v2.4.0.0/os/linux

sudo cp rt2860.ko /lib/modules/2.6.32-24-generic/kernel/drivers/staging/rt2860.ko
(where 2.6.32-24-generic is the name of your current kernel)

Now edit your rt2860sta.dat file so that:
WirelessMode=9  ( or 6 if you only want 802.11n)
Channel=5 ( this should match your Wide channel if your using 40Mhz)
HtBw=1

and do the rest of the settings for WEP or WPA security settings.

The above setting Channel=5 didnt quite work for me. So i added a script inside /etc/network/if-up.d/

#!/bin/sh
iwconfig ra0 channel 5

then just run: chmod 777 your_script_name

--------------------------------------------------------------------
Now thats the configurations done, time to use some updated firmware

download the rt2860 firmware from ralink site:

[http://www.ralinktech.com/license_us.php?n=2&p=1&t=U0wyRnpjMlYwY3k4eU1ERXdMekF6THpNeEwyUnZkMjVzYjJGa01UWTBNamsyTVRBNE1pNTZhWEE5UFQxU1ZESTROakJmUm1seWJYZGhjbVZmVmpJMkM%3D](http://www.ralinktech.com/license_us.php?n=2&p=1&t=U0wyRnpjMlYwY3k4eU1ERXdMekF6THpNeEwyUnZkMjVzYjJGa01UWTBNamsyTVRBNE1pNTZhWEE5UFQxU1ZESTROakJmUm1seWJYZGhjbVZmVmpJMkM%3D)

extract the file and:
cd (_PATH-TO_)/RT2860_Firmware_V26

backup old firmware
sudo mv /lib/firmware/rt2860.bin /lib/firmware/rt2860.bin.bak 

add new firmware
sudo mv ./rt2860.bin /lib/firmware/rt2860.bin

---------------------------------------------------------------------
Now to finalize

sudo ifconfig wlan0 down
sudo rmmod rt2860sta
sudo modprobe rt2860sta
sudo depmod -ae

Things that arent working (for my system at least) is file sharing. If any one finds anything on that, would love to hear it. Hope this helps :)

---

### Post by MaindotC on 2010-09-12
It's so nice to see another user having success and willing to share it with the community.  When you get time, would you place this information in the official community documentation?  You can edit or create a page using [these guidelines](https://help.ubuntu.com/community/WikiGuide).  I'd do it but I don't want to take credit for it and you have the device and I don't :(  Thanks!

---

### Post by jefdebruges on 2011-01-08
On my E1210 with UNE 10.10, blacklisting rt2800pci, rt2800lib, rt2x00usb, rt2x00pci & rt2x00lib, and updating the firmware as posted here (without updating the driver) and finalizing steps ofcourse, did the trick. Many thanks! Saved me a lot of time & effort!

---

