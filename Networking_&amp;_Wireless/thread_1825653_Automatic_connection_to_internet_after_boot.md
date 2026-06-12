---
title: "Automatic connection to internet after boot"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by Kimse73 on 2011-08-15
Just recently I got some help to connect to the Internet through my newly bought USB adapter, and it works just fine now... But - after boot I can't connect to the Internet before i open a terminal and type

either:** sudo modprobe ndiswrapper** - from the ndiswrapper-1.56 folder

or: **sudo iwlist wlan0 scan** - from the root

Both commands are some I learned during installation of the USB device - I don't know if any other commands would work; I'm a Linux newbie

It would be nice if my device connected automatically - is this possible?

Best regards

/ Kim

---

### Post by Kimse73 on 2011-08-18
Also - it seems that my ASUS RT-N16 desides when to kick someone off the network - especially after I got on the network with this Ubuntu installation... You're on - untill the router decides to kick you off...

After upgrading firmware (to 7.0.2.34), the router started to make IP addresses in the hundreds for the windows and android clients (except the Vista-one I configured manually) - but the Ubuntu stays in the tens:

Ubuntu: 192.168.1.3
Vista: 192.168.1.10
Win 7: 192.168.1.100
Android: 192.168.1.109

Can anyone help

---

### Post by Actonix on 2011-08-18
Try loading up the Network Connections GUI which should hopefully present you with and enable you edit your connection settings

---

