---
title: "Wireless connection help"
date: 2009-12-12
forum: Networking &amp; Wireless
---

### Post by nitnat56 on 2009-12-12
Hi, I'm completely new to ubuntu, I just downloaded 9.10 today. I have it running alongside windows xp in a dual boot. 

My problem is that I cannot connect to wireless internet, though it works in windows. There aren't any networks listed under the Network Connections, though my network card seems to have been recognized.

Here is the sudo lshw -C network output:

```

 *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:73:73:ea
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.33 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:dfdfe000-dfdfffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:f7:8d:d0
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:17 memory:dfdfd000-dfdfdfff

```

I have also checked the settings in bios, the wireless is turned on, though the fn+F2 doesn't seem to work in ubuntu...

Please help! I would love not to have to use windows every time i need internet.

---

### Post by chili555 on 2009-12-12
Network Manager is not happy to connect wirelessly when you are already connected wired, which you are:> duplex=full ip=192.168.1.33 latency=64 link=yesPlease detach the wire, reboot and click the Network Manager icon and see if you can now connect.

---

### Post by nitnat56 on 2009-12-12
Unplugging the cable doesn't make a difference. I have rebooted several times, even booted windows and then booted ubuntu again, doesn't help.

---

### Post by nitnat56 on 2009-12-12
Ok, so I managed to fix this one on my own. After hours of going through other threads and attempting to troubleshoot, I decided to try manually setting up a new connection and entering the ESSID and WEP key. After a few seconds ubuntu notified me that I was connected, and I write this over wireless internet!

I haven't tried rebooting to see if it sticks though...

---

