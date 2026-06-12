---
title: "Please advise on setting up AP, installing drivers"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by vyath on 2010-06-01
Hi,
I'm running Ubuntu 10.04 and I'm trying to set it up as a wireless access point, but I'm completely stumped.

I have a USB dongle that is identified as 3Com 3CRUSB10075 802.11bg, which has a zydas ZD1211 chipset that should support master mode.

However when running

sudo iwconfig wlan0 mode master

I get 

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.


So I figured maybe this is because of a driver problem like this page mentions:
[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

And here lie my problmes:
First, I'm not sure how to install the VenderBasedDrivers that is linked there - there is simply no documentation I could find.

Second, running 
sudo echo zd1211rw >> /etc/modprobe.d/blacklist 

gives me
bash: /etc/modprobe.d/blacklist: Permission denied

Please advise!

---

