---
title: "[howto] get Ralink r73 usb wireless card to work under hardy heron"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by 'ntoni on 2009-01-16
First of all let me suggest you to use the opensource r2x00 driver. You can easily download and configure it by using the wonderful python script made by Kiefer Rodriguez.
Here you get it:
[http://ubuntuforums.org/showthread.php?p=4732883](http://ubuntuforums.org/showthread.php?p=4732883)
Next, you'll have to fix a little bug which prevents you from bringing up wlan1 (wlan0) interface. If you get something like:
```
SIOCSIFFLAGS: Invalid argument
```
then you should specify a valid mac address for the card to work. To do this,just type:
```
 sudo ifconfig wlanXX hw ether 00:00:AA:BB:CC:DD
```
where XX is the number of your own card
the type:
```
 sudo ifconfig wlanXX uo
```
and you're through.
To make the solution permanent, add 
# rt73 wireless network device using DHCP
```
auto wlanXX
hwaddress ether 00:00:AA:BB:CC:DD
```
where XX is the number of your own card to the file ```
/etc/network/interfaces
``` (you'll need sudo access for doing that)
Okay, then let me suggest you to do an:
```
sudo apt-get install rutilt
```
Rutilt is a graphical configuration tool for your r73 driver, which enables basic and advanced functionality of the chipset. You'll find it under```

applications -> Internet -> rutilt

```
that's all. Good luck folks!

---

