---
title: "Ubuntu 8.10, Wireless Belkin F5D7000 Help"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by Rawgers on 2008-12-06
I currently have Belkin Wireless (F5D7000) and I am trying to make it work for Ubuntu. The wireless works when I am on Windows XP, but not on Ubuntu.

I tried a couple of things, including this guide over here [http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide]("http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide")

On Windows Wireless Driver it says this
```
driver-bcmwl5a "Hardware Present" Yes
```
But when I click "configure network" it responds with
```
Could not find a network configuration tool
```

On the application, Hardware Drivers-
It says "Broadcom B43legacy wireless driver"
But if I want to activate, it shows that it is downloading/installing but it does not do anything even if I restart computer.

When I put 
```
sudo ndiswrapper -l
```
It responds with
```
bcml5a: driver installed
device (14E4:4320) present (alternate driver :ssb)

```

Computer Brand
```
VGC-RB30
```

Wireless Brand, Model, and Wireless Chipset
```
Broadcom Corperation BCM4306 802.11b/g Wireless LAN
```

interface
```
wlan0 IEEE 802.11b/g Essid:""
```

Modules
Could not find

Kernel booot messages
```
Broadcom 43xx-legacy driver loaded
```

Network Configuration
```
Network Controller BCM4306 802.11b/g Wireless Lan Controller
```

Scan for Networks
```
wlan0 
No scan result
```

Ubuntu Version
8.10

Kernel/architecture
```
2.4.27-7-generic i686
```

Phew, that was a lot of info to put. Thanks for any help.

---

### Post by Rawgers on 2008-12-07
I tried this also [http://ubuntuforums.org/showthread.php?t=571188&highlight=wireless+command+line]("http://ubuntuforums.org/showthread.php?t=571188&highlight=wireless+command+line")

But it end up not working. I believe I may have a lot of missing files since I got an error saying that a file is missing quite frequently.

---

