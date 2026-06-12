---
title: "How do you get Linksys WPC54gs Driver?"
date: 2012-01-25
forum: Networking &amp; Wireless
---

### Post by CC Inc on 2012-01-25
Hi, 
I am using the Lubuntu live usb from my laptop, and I cannot get the WPC54gs working. I have tried to use Windows Wireless Drivers, and it works, but I also get Firmware missing.

Can anyone help?
Thanks

---

### Post by kevdog on 2012-01-26
I think that is the bcm4306 chipset --- maybe?

Can you list the results of:
lshw -C network
lspci -nn

Thanks -- I think likely its going to be the b43 driver but we will see!

---

### Post by CC Inc on 2012-01-26
If it helps, it is the PCMCIA port.

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 20
       serial: 00:08:02:d1:5e:42
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139cp driverversion=1.3 duplex=full ip=192.168.20.104 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:11 ioport:8800(size=256) memory:e8017800-e80178ff
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:11 memory:30000000-30001fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:13:10:f2:e6:2f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
ubuntu@ubuntu:~$ sudo lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc AGP Bridge [IGP 320M] [1002:cab0] (rev 13)
00:01.0 PCI bridge [0604]: ATI Technologies Inc PCI Bridge [IGP 320M] [1002:700f] (rev 01)
00:02.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:07.0 ISA bridge [0601]: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+] [10b9:1533]
00:08.0 Multimedia audio controller [0401]: ALi Corporation M5451 PCI AC-Link Controller Audio Device [10b9:5451] (rev 02)
00:0a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
00:0b.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 20)
00:0c.0 Communication controller [0780]: Conexant Systems, Inc. HSF 56k HSFi Modem [14f1:2f00] (rev 01)
00:0f.0 USB Controller [0c03]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:10.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c4)
00:11.0 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
00:13.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] [104c:8023]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility U1 [1002:4336]
02:00.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 

```

---

### Post by CC Inc on 2012-03-21
Yes, I do think it is bcm4306. Now what do I do?

---

