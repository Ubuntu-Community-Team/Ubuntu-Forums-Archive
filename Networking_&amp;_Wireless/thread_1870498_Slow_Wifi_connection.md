---
title: "Slow Wifi connection"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by prashant683 on 2011-10-27
I am a linux newbie and I have installed ubuntu 11.10 on my pc. Intially the wifi was working very slowly so I followed the following steps.
 First I removed network-manager and replaced it with wicd.


```

 sudo ifconfig wlan0 down
 sudo rmmod -f rt2500usb
 sudo modprobe rt2500usb nohwcrypt=1
 sudo ifconfig wlan0 up
 
``````

 sudo modprobe rt2500usb 11n_enable=1
 sudo modprobe rt2500usb 11n_disable=1
 
``````

 sudo iwconfig wlan0 power off
 
``` After following these steps the wifi works properly. I have to do this at every reboot.
 I tried reinstalling network-manager but the connection slows down. I tried to skip some commands but the connection slows down again. What do these commands mean?
 How can I make these changes permanent ?

---

