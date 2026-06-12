---
title: "Asus USB-N13 woes with Maverick"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by Rick P. on 2012-01-06
Trying to get my Asus USB-n13 adapter working at n speeds on my Acer Revo 3610 and think I've managed to muddle the works... 

The Revo has its own wireless network adapter (wlan0) that works at 54 mbps. I've also got the N13 working (wlan1) on the same network, also at 54 mbps, but only when the Revo adapter is enabled. Disconnecting the Revo adapter drops the N13 connection as well so I'm guessing I've tied them together somehow. A little knowledge is a dangerous thing.  Given that the N13 makes a solid 270 mbps connection to my router when plugged into a WD TV Live box I'm happy to disable the Revo adapter altogether if I can get the N13 working at full speed, but need help to undo what I've managed so far. 

Details:
uname -r
```

2.6.35-31-generic

```

lsmod | grep rt2
```

rt2870sta             446110  1 
rt2860sta             559618  1 
crc_ccitt               1699  2 rt2870sta,rt2860sta

```

modinfo rt2870sta | grep 1784
```
 
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*

```

modinfo rt2860sta
```
htpc@htpc:~$ modinfo rt2860sta
filename:       /lib/modules/2.6.35-31-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
version:        2.1.0.0
alias:          rt3090sta
license:        GPL
description:    RT2860/RT3090 Wireless Lan Linux Driver
author:         Jett Chen <jett_chen@ralinktech.com>
firmware:       rt3090.bin
firmware:       rt2860.bin
srcversion:     1CC5B0F527E33CC4AF73D2B
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        crc-ccitt
staging:        Y
vermagic:       2.6.35-31-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

```


Blacklisted
```
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
```


htpc@htpc:~$ iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:0 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

htpc@htpc:~$ lsusb
```

Bus 002 Device 002: ID 04f2:0963 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 002: ID 054c:0243 Sony Corp. MicroVault Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

htpc@htpc:~$ lspci
```

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b3)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 SATA controller: nVidia Corporation MCP79 AHCI Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
05:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

```


lshw -C network
```
 
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 90:fb:a6:8a:71:a4
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.199 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1GB/s
       resources: irq:20 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
  *-network
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 70:f1:a1:e7:e7:42
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:19 memory:febf0000-febfffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: bc:ae:c5:7d:a2:94
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=Ralink STA

```

I also built and installed the 3090 drivers for the Revo adapter somewhere along the way and network manager reported a 270 mbps connection, but I lost it as soon as I rebooted. :confused:

modinfo rt3090sta
```

filename:       /lib/modules/2.6.35-31-generic/updates/dkms/rt3090sta.ko
version:        2.3.1.7
license:        GPL
srcversion:     7AD3EDAB8F05EF152E92330
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        cfg80211
vermagic:       2.6.35-31-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)

```

Would appreciate assistance in getting this sorted. Thanks!

Rick

---

