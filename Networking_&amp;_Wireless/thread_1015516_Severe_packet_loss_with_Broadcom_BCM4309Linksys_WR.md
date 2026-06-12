---
title: "Severe packet loss with Broadcom BCM4309/Linksys WRT110"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by smithkl42 on 2008-12-18
I'm running Intrepid on an old Dell Precision M60 (a fresh install), using the b43legacy driver/firmware.  After some tweaking, I was able to get wireless up and running at a (very) minimal level.  However, a ping to my local router (a Linksys WRT110 using version 1.0.0.2 of the firmware) consistently gives me something like 75% packet loss, and of course, that's pretty much unusable.  I don't *think* that it's an interference issue, as I'm sitting about five feet from the router, and I've got two other machines (running Vista) *much* further away, and they don't seem to have any trouble.

System information:
```

kens@kens-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:16:d4:ee
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.08 ip=192.168.1.103 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:71:cf:13
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.104 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: de:bb:f4:9c:18:ae
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

```
kens@kens-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Quadro FX Go700 [10de:031c] (rev a1)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:01.0 CardBus bridge [0607]: Texas Instruments PCI7510 PC card Cardbus Controller [104c:ac47] (rev 01)
02:01.1 CardBus bridge [0607]: Texas Instruments PCI7510,7610 PC card Cardbus Controller [104c:ac4a] (rev 01)
02:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller [104c:802b]
02:01.3 System peripheral [0880]: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function [104c:8204]
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 02)

```

```
kens@kens-laptop:~$ lsmod | grep -i -e b43 -e ssb -e bcm43xx -e ndiswrapper
b43legacy             128156  0 
rfkill                 17176  3 rfkill_input,b43legacy
mac80211              216820  1 b43legacy
led_class              12164  1 b43legacy
input_polldev          11912  1 b43legacy
ssb                    40580  1 b43legacy

```

I should note that I tried the ndiswrapper way of doing it on this same machine (with an copy of Intrepid that I'd upgraded from Hardy from Gutsy) and I got more-or-less the same results, i.e., severe packet loss.  

Any thoughts on what I should try next, other than a new laptop? :-)

Many thanks.

---

