---
title: "Can't get wifi wireless adapter to work now?"
date: 2010-07-11
forum: Networking &amp; Wireless
---

### Post by demonic_crow on 2010-07-11
This is the wifi wireless usb adapter I'm using:

[http://www.amazon.com/Wireless-802-11G-Network-Adapter-Noteook/dp/B00333AW72/ref=pd_cp_e_2](http://www.amazon.com/Wireless-802-11G-Network-Adapter-Noteook/dp/B00333AW72/ref=pd_cp_e_2)

When I first got it and plug it into my computer running Ubuntu 9.10 it worked just find and had no problem.  Well I decided to do a clean install of Ubuntu 10.04 and couldn't get it to work.  So I reinstall Ubuntu 9.10 and it isn't working on it either now. It show there a wireles adapter and it will even lt me manually enter stuff i but it won't connect.  Anyone have any idea how to get this to work again for me?  

```
lsusb
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0a5c:2148 Broadcom Corp. 
Bus 002 Device 004: ID 0a5c:4503 Broadcom Corp. 
Bus 002 Device 003: ID 0a5c:4502 Broadcom Corp. 
Bus 002 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=13 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by demonic_crow on 2010-07-11
What ralink driver do you think this needs or is there a way for me to figure that out?

---

### Post by demonic_crow on 2010-07-11
I click on connect to hidden wireless network and then I choose my SSID.  Everything seem to be faded out where I can't click on it.  I can enter my password or click connect.  What would be the cause of that.  Also the wireless usb doesn't any nearby router, it have once though and then it stop.

---

### Post by bkratz on 2010-07-11
> **demonic_crow said:**
> What ralink driver do you think this needs or is there a way for me to figure that out?

I think this thread will help you alot.

[http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070](http://ubuntuforums.org/showthread.php?t=1378782&highlight=148f:3070)

---

### Post by demonic_crow on 2010-07-11
thanks alot, it really did work.

For anyone that comes across this problem just go to termial type:

sudo gedit /etc/modprobe.d/blacklist.conf
then very bottom of the page type:

blacklist rt2800usb

save it

make sure your ethernet cord is unplug and usb adapter is plug in, restart your computer and connect!

---

### Post by bkratz on 2010-07-11
> **demonic_crow said:**
> thanks alot, it really did work.

For anyone that comes across this problem just go to termial type:

sudo gedit /etc/modprobe.d/blacklist.conf
then very bottom of the page type:

blacklist rt2800usb
make sure your ethernet cord is unplug and usb adapter is plug in, restart your computer and connect!

Please go to the thread tools and mark as [solved] to help others find it.

---

