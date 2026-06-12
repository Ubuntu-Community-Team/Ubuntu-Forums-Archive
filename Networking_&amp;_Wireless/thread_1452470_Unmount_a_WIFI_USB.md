---
title: "Unmount a WIFI USB"
date: 2010-04-12
forum: Networking &amp; Wireless
---

### Post by tjpren on 2010-04-12
Hello forum,

does anyone know how to unmount a wifi usb.

When I use lsusb, I get:

Bus 001 Device 004: ID 0846:4240 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

What would I use in the unmount command to reference Device 004

I've just been pulling the USB out, but thought there might be a code way of doing the same thing.

Thanks.

---

### Post by 2hot6ft2 on 2010-04-12
You could
Open a terminal
Applications > Accessories > Terminal
and run
```
ifconfig
```
find the adapters wlan number like wlan0 or wlan1
and run
```
sudo ifconfig wlan1 down
```
where wlan1 is the adapter

To reactivate the adapter you can either reboot or run
```
sudo ifconfig wlan1 up
```

---

### Post by tjpren on 2010-04-13
Thankyou 2hot6ft2,

I will try your suggestion when my WIFI drops out next.

In the meantime, I've made a little discovery in that when my WIFI drops out, I can 
1. Kill nm-applet from system monitor
2. Restart nm-applet from terminal

my WIFI reconnects - similar in effect to unplugging, and re-plugging my WIFI USB.

---

