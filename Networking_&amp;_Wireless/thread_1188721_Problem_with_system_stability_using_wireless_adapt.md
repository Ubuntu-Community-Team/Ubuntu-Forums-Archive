---
title: "Problem with system stability using wireless adapter and ndiswrapper"
date: 2009-06-16
forum: Networking &amp; Wireless
---

### Post by martez81 on 2009-06-16
I'm working on ubuntu 9.04. My wireless usb adapter is Zonet ZEW2502. Wireless didn't work out of the box so I used ndiswrapper to solve the problem and it seemed to work well. 
Unfortunatelly I noticed that after some time when browsing pages OS starts to behave weird - some applications beconme unstable (ussualy firefox browser); when you want to open system monitor to kill bad behaving processes it freezes; killing firefox from terminal doesn't do anything and even sudo shutdown won't shut off the system. When I was playing around without wireless plugged in, everything seemed to work flawlessly. 
I started using Opera browser as I thought Firefox may be a culprit, but the same thing happend after leaving computer on for about 2 hours. The wireless connection turned off and couldn't connect to visible network and Opera was not responsive. Still it seems like this happens much more often when using Firefox than Opera browser.

Does anybody have or had similar problem?

Thanks

---

### Post by dmizer on 2009-06-16
Please post the output of:
```
lshw -C network
```

---

### Post by martez81 on 2009-06-16
*-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:16:17:5e:25:2f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 08:10:74:04:e5:3d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrvw225 driverversion=1.54+Customer,12/21/2005,2.1.0.1 ip=192.168.1.2 link=yes multicast=yes wireless=IEEE 802.11g
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:2 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: be:58:6b:ae:27:b6
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by superprash2003 on 2009-06-16
i guess you mean frequent disconnections in wifi , could be related to this [http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367) ?

---

### Post by martez81 on 2009-06-16
Yes frequent disconnections too, but it does the same under WinXP so I thought it's the faulty router (or settings) to which I have no access :)

BTW this problem seems to be different than from the link you posted. 1. My wireless reconnects after several seconds 2. Problem was the same with ubuntu 8.10.

---

### Post by dmizer on 2009-06-16
I suggest testing with a different card. That will show you if the problem is the router or the wireless card.

---

### Post by martez81 on 2009-06-17
Thanks. I think that's the only think I can do for know.

---

