---
title: "unable to connect to sitecom wl-181, chipset ralink rt2800 802.11n pci"
date: 2010-08-20
forum: Networking &amp; Wireless
---

### Post by stijnblommerde on 2010-08-20
Dear community
 

 problem: Unable to connect to wireless network at home. The wireless network is visible. Password is requested. But no connection established.
 

 hardware:  
 desktop, ubuntu 10.04
 PCI card: sitecom wireless nework cardbus card 300N
 chipset: ralink RT2800 802.11n PCI
 iwconfig wlan0: RT2860 wireless, nickname: rt2860sta



 I tried using ndiswrapper. Conclusion: 'driver already installed'.  
 

 The wireless network does connect on my laptop with ubuntu 10.04 installed.
 Distance to modem: 3 feet. 



 Thanks


Stijn

---

### Post by JBAlaska on 2010-08-20
The fix is to blacklist the rt2800usb driver, In a terminal do:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

and add:

```
blacklist rt2800usb
```
Reboot your system.

Lucid (or karmic) will then use the RT2870STA driver and work perfectly.

---

### Post by stijnblommerde on 2010-08-20
dear jbalaska

i followed your lead: blacklisted rt2800usb. at first it worked. i got connected. after a few minutes the connection failed again and i was unable to restart it.

 greetings, stijn

---

