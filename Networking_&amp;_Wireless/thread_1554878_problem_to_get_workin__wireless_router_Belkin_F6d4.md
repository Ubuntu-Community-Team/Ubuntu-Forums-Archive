---
title: "problem to get workin  wireless router Belkin F6d4230-4 v1"
date: 2010-08-17
forum: Networking &amp; Wireless
---

### Post by All.coholic on 2010-08-17
I have a lots of problems to set my wireless router. It is Model Belkin F6D423-4 v1. After turning it on and puting usb in. It wasn't recognized. Only reply i had after typing lsusb: 

Bus 002 Device 002: ID 093a:262a Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 050d:935a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and iwconfig gave me this:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 After googling around i tryed this: [http://ubuntuforums.org/showthread.php?t=1509403](http://ubuntuforums.org/showthread.php?t=1509403). It been recognized by Wicd network manager, but still wasn't able to connect to internet wireless. Even by trying Windows Network Drivers and putting in file rt280.inf what i got from cd. It is showing that rt2870 hardware is present but pressing Configure Network give me "Could not find a network configuration tool." Hoping that updating my ubuntu from 9.10 to  10.4 would fix it, resulted that Wicd network manager is not regnizing it at all... I am out of advices and tips what i could get from internet or I just didn't had a luck with right help?

---

