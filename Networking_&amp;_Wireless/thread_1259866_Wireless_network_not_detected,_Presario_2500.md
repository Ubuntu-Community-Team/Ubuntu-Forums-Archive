---
title: "Wireless network not detected, Presario 2500"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by dgpj on 2009-09-06
I am using wicd and only a wired connection can be detected. I have 2 other computers on my router so I know it is functional. WICD reports no wireless network found. I ran iwconfig and the mode shows ad-hoc. I try to change the mode but get an error. I am new to UBUNTU but enjoying the increased knowledge. Thanks for any guidance you have time to offer. Don

---

### Post by cariboo on 2009-09-07
It would help if we khew what wireless device you have. Open an Applications-->Accessories-->Terminal and type:

> sudl lshw -C network > network.txt

The above command will create a text file called network.txt. Can you copy it to your Windows partition or if your wired network connection works, paste it into your next post.

---

### Post by dgpj on 2009-09-07
Thanks for taking the time to reply to me! Here is the network.txt

  *-network:0
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0e:7f:7b:8c:ae
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=full ip=192.168.2.5 latency=90 link=yes maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair speed=100MB/s
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:4a:88:e6
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6e:15:1d:59:1c:35
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by dgpj on 2009-09-07
iwpriv shows no ioctls and when I enter ifconfig wlan0 up... I receive SIOCSIFFLAGS: Permission Denied

---

### Post by jward3010 on 2009-09-07
You'll need to run that "ifconfig wlan0 up" as root. So basically:
```
**sudo** ifconfig wlan0 up
```
Also try this command and tell us if any wireless networks appear:
```
iwlist scanning
```

**On another note:** I'm not completely sure about BCM4306's and their compatibility but have you checked "Hardware Drivers" in "System Menu" > "Administration" to see if there are any drivers for that card?

---

### Post by dgpj on 2009-09-07
Thanks for taking the time to reply to me!

sudo ifconfig wlan0 up -- response: SIOCSIFFLAGS: No such file or directory

iwlist scanning -- wlan0 No scan results

Thanks again!

---

### Post by jward3010 on 2009-09-07
> **dgpj said:**
> sudo ifconfig wlan0 up -- response: SIOCSIFFLAGS: No such file or directory
That's odd.

---

### Post by dgpj on 2009-09-07
Hey, your hints got me on track...I updated the firmware and then sudo ifconfig wlan0 up -- online now! thanks

---

### Post by jward3010 on 2009-09-07
Did this wireless card work with network-manager?

JUST READ ABOVE! WELL DONE, Enjoy the Internet.

---

