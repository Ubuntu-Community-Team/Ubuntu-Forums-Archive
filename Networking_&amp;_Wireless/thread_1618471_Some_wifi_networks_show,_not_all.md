---
title: "Some wifi networks show, not all"
date: 2010-11-10
forum: Networking &amp; Wireless
---

### Post by Ninja duck on 2010-11-10
I'm using a Belkin router that is broadcasting SSID correctly and I have another ubuntu laptop which will find and connect to it with no problem. I just installed ubuntu 10.04.1 on a different computer (a desktop) with a usb belkin wifi thing plugged in. The light turns on, it works. I can see some wifi networks (neighbors) but i cannot see my own network. I have tried "connect to hidden network" and i have even taken off the security on the router and tried again, but the desktop computer won't connect or find my router.

---

### Post by uncaspi on 2010-11-10
Please post the result of sudo /sbin/iwlist scan

---

### Post by Ninja duck on 2010-11-13
Sorry for the delay.

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy

```

I've installed the driver using ndiswrapper also, and still have the same problem. I've tried the same usb wifi adapter on two computers (both with ubuntu 10.04.1) and had the same problem.

---

