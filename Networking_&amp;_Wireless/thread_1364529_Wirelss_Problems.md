---
title: "Wirelss Problems"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by WillScarlet on 2009-12-26
I have been working on my wireless for the last few days, and problems keep on coming up. I am relatively new to Linux, I've only used it for a few weeks now, and my family has never been able to get wireless working with Linux. I've been browsing the forums,  and I've found problems similar to mine, but most are on laptops or when i try the solutions, I can't get them to work. The "enable wireless" check box has been greyed out, and my drivers are correct and active.I am using a media pc with a broadcom 4303 card. Here are the results of a few commands that are relevant  

root@media-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0root@media-desktop:~# sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132
root@media-desktop:~#  lshw -C network
  *-network:0             
       description: Ethernet interface
       product: 190 Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 00
       serial: 00:16:ec:5b:c1:41
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis190 driverversion=1.3 duplex=full ip=192.168.0.198 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:19 memory:febfbc00-febfbc7f ioport:e000(size=128)
  *-network:1
       description: Network controller
       product: BCM4303 802.11b Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:febf8000-febf9fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:02:dd:34:33:6f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11b

If anyone has any suggestions, i would really appreciate it. If I can't get the wireless to work, then my dad will make me install windows :.(

---

### Post by steveneddy on 2009-12-26
Broadcom wireless cards require you to run specific software so you can use the Window's drivers, or simply purchase a supported card.

I believe you need ndiswrapper and a copy of the Windows driver for the wireless card.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by WillScarlet on 2009-12-26
I will try ndiswrapper, and tellyou as soon as I can. thanks for the suggestions

EDIT- It oo like he card that i have is not suported by ndiswrapper, and so i will have to find anoter solution

---

### Post by yelvington on 2009-12-26
That Broadcom card is supported by ndiswrapper, but you have to do a bunch of extra work to load firmware into the card to wake it up. It's really not worth it, as it's just an outdated 802.11b card, and you're much better off buying a Linux-compatible replacement that supports modern standards.

---

### Post by WillScarlet on 2009-12-26
Thank you for your answers, but I would like to not have to get another card, and I hope to find another solution, but again thank you for your answer, and I will use your advice as a last resort

---

