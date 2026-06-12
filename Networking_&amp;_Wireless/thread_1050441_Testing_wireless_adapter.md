---
title: "Testing wireless adapter"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by ztrange on 2009-01-25
Im trying to find some way to deep test my wireless adapter... Im not sure it is working fine... Ive looked in google but nothing this far. Maybe some script or log to see the performance??

Thanks in advance.

---

### Post by Sam Lars on 2009-01-25
```
iwconfig
```
This will show you info about the wireless connection.
```
sudo iwlist scanning
```
This will list all available networks.
If you install iftop
```
sudo aptitude install iftop
```
And then
sudo iftop eth0
Assuming eth0 is your network card name (from iwconfig).
It will show you the rate that it's sending data and where it's going or coming from.
Lastly
```
ifconfig
```
This is the generic info for all network interfaces.

---

### Post by ztrange on 2009-01-25
Thanks for your quick reply.

The problem is that weeks ago my wlan0 stopped working to connect to my wlan or got connected at very low speed (tested with good speed with ethernet).

I bought a nwe wireless card for usb. But now, my old wireless is "working" But Im not sure if it is fine.

I uses iwlist and iftop and everything looked fine for me. I was hoping to see if there is some exahustive testing tool specifically to diagnostic hardware.

Well, anyway, if you know something, thanks in advance.

---

