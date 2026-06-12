---
title: "Wireless refuses to connect on Start Up"
date: 2011-05-13
forum: Networking &amp; Wireless
---

### Post by linux_burner on 2011-05-13
I am having wireless connectivity issues since yesterday afternoon. I am running Ubuntu 10.10 32 bit on Acer Aspire 5002WLMI laptop. This is the first time I am facing this issue since March 2009.

My wireless connection refuses to connect on start up. It recognizes wireless connections and even tries to connect to my connection. After a while of unsuccessful attempts to connect, it prompts for password. The password I have entered is correct as my other laptop running Win 7 connects to the same network without problems.

The problem started while I was modifying some programs on my desktop. There was a sudden massive power outage and my desktop switched off. The lappies were still running on batteries. Anyways after this incident, I could not connect to my network from both laptops. I reseted the router and provided my network with a new SSID & Key (WPA encryption). I reinstalled wpasupplicant from Synaptic but it ain't helping. Strange thing is, if I reset the wireless by hardware button on laptop, it connects thereafter!

I would appreciate any help in troubleshooting.

Wireless hardware detail:

```
$ lspci
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

iwconfig log:

```
wlan0     IEEE 802.11bg  ESSID:"NagarajaK"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:22:B0:B8:2C:B3   
          Bit Rate=18 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Network Config

```
PCI (sysfs)  
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:a5:07:d7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:48000000-4801ffff
  *-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e2000000-e2001fff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0e:9b:cd:7f:6c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-28-generic firmware=N/A ip=192.168.0.199 link=yes multicast=yes wireless=IEEE 802.11bg
```

I do not have an option of starting up OS using an old kernel version since this is a fresh 10.10 install.

Thanks

---

### Post by linux_burner on 2011-05-13
I am not sure if this is a hardware issue (I don't think it is...'cause once connection is established, I can browse at prescribed speeds). And this is a noob question, if I go for a replacement adapter, will it come with its own antenna?

---

### Post by josephmills on 2011-05-13
please see post #44 [http://ubuntuforums.org/showthread.php?t=1748245&page=5](http://ubuntuforums.org/showthread.php?t=1748245&page=5) 
As far as a new card usb or pci all come with antennas now moding them that can be either fun or detrimental could ruin your card but it can be done with some flux and solder

---

### Post by linux_burner on 2011-05-14
Thank you for your reply. I am not sure if it worked...its connecting now but I think part of my problem might be due to old hardware, especially antenna. I am having it checked next week and if required have it replaced as well.

---

