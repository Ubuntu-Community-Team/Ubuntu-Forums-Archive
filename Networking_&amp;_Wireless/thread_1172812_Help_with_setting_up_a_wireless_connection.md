---
title: "Help with setting up a wireless connection?"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by disaosa on 2009-05-29
I just installed 9.04 on an old laptop via clean install. Everything is working fine except the wireless connection. I tried a few solutions that were proposed on these forums but haven't had any luck.

Wireless card: Linksys WPC54G ver 2
Router: Linksys WRT54G
Laptop model: Compaq Presario 2100

Also the chipset is ACX 111. 

As far as I can tell, the card has been detected. The power light is on, and some info showed up in the terminal when I was trying things that had been posted.

The wireless network is working fine on my other laptops (vista and xp). Thanks for any help you can provide.

EDIT: The link provided by PietreWitobi contains the solution to this problem. It seems like a lot to do, but it's really not bad at all. I am writing this from the laptop that was giving me so much trouble. Thanks to PietreWitobi for providing the link and to dmizer for writing an excellent guide.

---

### Post by PietreWitobi on 2009-05-29
Your card and chipset are listed [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCMCIA") as working out of the box.  You can follow that link next to it for an Ndiswrapper workaround.  It seems rater intensive, and I do not envy you the work to extrapolate it to Jaunty.

For more help, try posting the results of one or more of the following diagnostics:
```

$ iwconfig
$ lshw -C network
$ lspci -nn

```

---

### Post by disaosa on 2009-05-29
Thanks, I will try the solution you recommended. In the meantime, here's the information you requested.
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  Nickname:"acx v0.3.36"
          Mode:Managed  Frequency:2.437 GHz  Access Point:  00:1C:10:0A:E6:F2
          Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=50/100   Signal level=30/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon:0

pan0      no wireless extensions.
```

```

$lshw -C network
  *-network
       description: Ethernet interface
       product: DP83815 (MacPhyter) Ethernet Controller
       vendor: National Semiconductor Corporation
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 00
       serial: 00:0d:9d:85:4d:b3
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii fibre 10bt 10bt-fd 100bt  100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=natsemi driverversion=2.1 duplex=half latency=90 link=no maxlatency=52 mingnt=11 module=natsemi multicast=yes port=twisted pair  speed=10MB/s
  *-network
       description: Wireless Interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:12:17:bc:32:60
       width: 32 bits
       clock: 33 MHz
       capabilities: pm bus_master cap_list ethernet physical wireless configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+
  *-network DISABLED
       description: Ethernet Interface
       physical id: 1
       logical name: pan0
       serial:  16:d5:7e:eb:de:60
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

```

$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] [1002:cab2] (rev 02)
00:01.0 PCI bridge [0604]: ATI Technologies Inc PCI Bridge [IGP 340M] [1002:7010]
00:02.0 USB Controller [0c0c]: ALi Corporation USB 1.1 Controller [10b9:5237] (rev 03)
00:06.0 Multimedia audio controller [0401]: ALi Corporation M5451 PCI AC-Link Controller audio device [10bl:5451] (rev 02)
00:07.0 ISA bridge [0601]: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+] [10bl:1533]
00:08.0 Modem [0703]: ALi Corporation M5457 AC'97 Modem Controller [10b9:5457]
00:0a.0 Cardbus bridge [0607]: 02 Micro, Inc OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
00:10.0 IDE interface [0101]: ALi Corporation M5229 IDE [10b9:5229] (rev c4)
00:11.0 Bridge [0680]: ALi Corporation M7101 Power Management Controller [PMU] [10b9:7101]
00:12.0 Ethernet controller [0200]: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller [100b:0020]
01:05.0 VGA Compatible controller [0300]: ATI Technologies Inc Radeon IGP 330M/340M/350M [1002:4337]
02:00.0 Network controller [0280]: Texas Instruments ACX 111 54 Mbps Wireless Interface [104c:9066]

```

---

