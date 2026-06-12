---
title: "Ubuntu does not recognize wireless adapter"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by n00b115 on 2009-07-11
Hi. i'm new on ubuntu. my wireless adapter edimax ew-7318usg(external) & ipw2200 (internal) but i use edimax..i installed rt73 driver but ubuntu doesnt recognized

**iwconfig ==>**
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.


```**eth1 = ipw2200**


**lsusb=>**
```

Bus 001 Device 003: ID 7392:7318  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0458:006a KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 1110:9021 Analog Devices Canada, Ltd (Allied Telesyn) ADSL WAN Adapter
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```ubuntu 9.04

[B]_Bus 001 Device 003: ID 7392:7318_   = I think , this is my wireless adapter because when i unplug usb , i cant see that..
[/B]


**lshw -C network ==> **
```

*-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial:
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1 DISABLED
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A 
 link=yes multicast=yes

```Help me pls.Thanks.

---

### Post by n00b115 on 2009-07-12
up up :(

---

### Post by n00b115 on 2009-07-12
i installed it but it seems disable.. how can enable it?

[http://i26.tinypic.com/33m0aqd.jpg](http://i26.tinypic.com/33m0aqd.jpg)

---

### Post by superprash2003 on 2009-07-12
laptops come with a wireless switch, which has an ON/OFF button or a keyboard shorcut.. make sure that the wifi switch is ON.. 

for reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by n00b115 on 2009-07-12
> **superprash2003 said:**
> laptops come with a wireless switch, which has an ON/OFF button or a keyboard shorcut.. make sure that the wifi switch is ON.. 

for reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

thnx but its external wireless. 
--------------
edimaxx changed usb root
```

/* EW-7318USg */\
{USB_DEVICE(0x7392,0x7318)},\

```

---

### Post by ugm6hr on 2009-08-01
[http://ubuntuforums.org/showthread.php?p=7716964#post7716964](http://ubuntuforums.org/showthread.php?p=7716964#post7716964)

---

