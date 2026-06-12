---
title: "ad-hoc network setup fails"
date: 2011-08-22
forum: Networking &amp; Wireless
---

### Post by NamiJason on 2011-08-22
I'm trying to share the internet connection from my Ubuntu 11.04 desktop to one of my laptops (Mac OS X) using an ad-hoc network.  Really I don't care what kind of AP the desktop broadcasts as long as I can share the internet connection.  According to the documentation on the hardware the adapter supports ad-hoc.  However I am getting the 8B06 error below.

The problem:  
iwconfig wlan0 mode ad-hoc yields -> 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.

I've been using this - [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

lsusb - Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B

my ifconfig and iwconfig here if you need them: [http://pastebin.com/T5Nq250W](http://pastebin.com/T5Nq250W)

help!? and preemptive thanks!

---

### Post by NamiJason on 2011-08-24
Somewhat of a bump here.  My continued google searches are coming up empty.  It sounds like the driver works out of the box for 11.04.  But I'm wondering if I should try installing another driver.  

I found this page that seems to not recommend doing so though.  I'm at a loss at this point. ([https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b))

lshw -C network:
```

       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:08:54:93:cb:e5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl8187 driverversion=2.6.38-11-generic-pae firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```

---

### Post by llDrWormll on 2011-08-27
I have the exact same problem ever since I updated to 11.04 Natty. Before I could easily create and connect to ad hoc networks, and now I can't do either. Very frustrating.

I have tried the following to no avail:
Update network manager to latest version
Create ad hoc from wicd manager
Millions of different configurations from the "Create New Wireless Network" and "Connect to Hidden Wireless Network" menu options

SOLUTIONS PLEASE!!

---

### Post by llDrWormll on 2011-09-13
shameless bump

---

### Post by llDrWormll on 2011-10-01
more bumps.. plz help! :(

---

### Post by llDrWormll on 2011-10-03
I have finally found a solution, after searching for hours.

My system:
Asus EEE with Broadcom BCM4313 wireless chip
Ubuntu Natty 11.04

1. Update Network Manager to latest version.
2. Reinstall STA drivers from command line using this guide (drivers may vary): [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

RELIEF!

---

