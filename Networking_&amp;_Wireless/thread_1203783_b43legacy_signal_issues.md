---
title: "b43legacy signal issues"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by Vengeful Cynic on 2009-07-03
I've got an old Dell Inspiron 1000 with a PCMCIA Dell-Branded b/g wireless card in it with a Broadcom BCM4306 chipset. I can get wireless 100% of the time when the laptop is near the router, but even with the laptop right next to the router, it reports 66% signal at best.

Move the laptop into another room and I'm lucky if I can raise the router long enough to ping google.  The hardware works fine throughout the house in Windows with the same network on the same channel, so I'm guessing I have a configuration issue or perhaps a driver issue.

This is a clean Ubuntu install with minor changes, only using the B43legacy wireless driver for wireless (I haven't touched ndiswrapper.)

Some pre-emptive information dumping from what I've read on the forums follows:

from iwconfig:
```

wlan0     IEEE 802.11bg  ESSID:"scholl"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:16:B6:EB:54:AF   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=66/100  Signal level:-51 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

from lspci:
```

02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)

```

from lspci -n:
```

02:00.0 0280: 14e4:4320 (rev 02)

```

from lshw -C network
```

WARNING: you should run this program as super-user.
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:10:c6:44:13:16
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.104 multicast=yes wireless=IEEE

```

Suggestions would be much obliged.

Thanks.

---

### Post by Vengeful Cynic on 2009-07-07
I know it's usually in poor form to respond to one's own post but I really would like someone to have a look at this.

---

