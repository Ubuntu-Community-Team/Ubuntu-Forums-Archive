---
title: "Wired LAN eth0 not detecting link/not working"
date: 2012-01-12
forum: Networking &amp; Wireless
---

### Post by zillowzillow on 2012-01-12
Hi Everyone,

I am unable to make my eth0 work and thought you wise guys can guide me to solution.

Problem: Wired LAN eth0 not detecting link/not working
Hardware: Dell E1505 Laptop
OS: Ubuntu 11.10 Server 32 bit (3.0.0-12-generic-pae #20-Ubuntu SMP)
Note: wireless is working fine. ndiswrapper is not installed. sta module is not loaded

Troubleshooting steps already done:
1. Changed the cables and switch ports.
2. ifup/ifdown, laptop powercycle.
3. With ethtool setting eth0 parameters auto neg on/off, different speeds/duplex

Related information:
===============================
#ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:15:c5:20:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:a1:yx:yx  
          inet addr:192.168.100.51  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fea1:xxx/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:272444 (272.4 KB)  TX bytes:346431 (346.4 KB)
===============================

#cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto wlan0
iface wlan0 inet dhcp
wpa-ssid DontConnect
wpa-ap-scan 1
wpa-key-mgmt WPA-PSK
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxx
===============================

#lshw -C Network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:a1:yx:yx
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.0.0-12-generic-pae firmware=15.32.2.9 ip=192.168.100.51 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:42 memory:dfdff000-dfdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:20:yx:yx
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:17 memory:df9fe000-df9fffff
===============================

#lspci -v|egrep -A 7 -i net
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
        Subsystem: Dell Inspiron 6400
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at df9fe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: b44
        Kernel modules: b44

--
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Intel Corporation Device 1020
        Flags: bus master, fast devsel, latency 0, IRQ 42
        Memory at dfdff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945
===============================

#egrep -v "^$|^#" /etc/modprobe.d/blacklist.conf
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac
===============================

#lsmod |egrep "ss|b4|iw"
iwl3945                73370  0 
iwl_legacy             71499  1 iwl3945
mac80211              272785  2 iwl3945,iwl_legacy
cfg80211              172392  3 iwl3945,iwl_legacy,mac80211
b44                    31395  0 
ssb                    50682  1 b44
===============================

#modinfo b44
filename:       /lib/modules/3.0.0-12-generic-pae/kernel/drivers/net/b44.ko
version:        2.0
license:        GPL
description:    Broadcom 44xx/47xx 10/100 PCI ethernet driver
author:         Felix Fietkau, Florian Schirmer, Pekka Pietikainen, David S. Miller
srcversion:     8729399E9471704D13404C1
alias:          ssb:v4243id0806rev*
alias:          pci:v000014E4d0000170Csv*sd*bc*sc*i*
alias:          pci:v000014E4d00004402sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004401sv*sd*bc*sc*i*
depends:        ssb
vermagic:       3.0.0-12-generic-pae SMP mod_unload modversions 686 
parm:           b44_debug:B44 bitmapped debugging message enable value (int)
===============================

#modinfo ssb
filename:       /lib/modules/3.0.0-12-generic-pae/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     7E7E756F6D56DE7C6587290
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
vermagic:       3.0.0-12-generic-pae SMP mod_unload modversions 686 
===============================

#grep -i eth /var/log/syslog
Jan 12 12:58:51 whale kernel: [    1.236149] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
Jan 12 12:58:51 whale kernel: [    1.300660] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:20:90:57
Jan 12 12:58:51 whale kernel: [   14.656875] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 12 12:58:51 whale dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jan 12 12:58:54 whale dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7

===============================
#dmesg|egrep -i "eth|iw|b44|ssb"
[    1.200551] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.236149] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.236160] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.236168] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.277185] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.277233] b44: b44.c:v2.0
[    1.300660] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:15:c5:20:90:57
[   10.258394] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   10.258400] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   10.258490] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.258507] iwl3945 0000:0b:00.0: setting latency timer to 64
[   10.314272] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   10.314278] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   10.314435] iwl3945 0000:0b:00.0: irq 42 for MSI/MSI-X
[   10.831615] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   14.656875] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.999914] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
===============================

#ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  100baseT/Full 
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Speed: 10Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: g
        Wake-on: d
        Current message level: 0x000000ff (255)
                               drv probe link timer ifdown ifup rx_err tx_err
        Link detected: no
===============================

Thanks for help.

---

### Post by Buntumatic on 2012-01-12
Link detected: no

From all the information you've provided it's the most significant, regarding to your problem. This is a hardware issue, since you already swapped cables and changed switch ports I'd say odds are high the ethernet port of your laptop is dead.

---

### Post by zillowzillow on 2012-01-12
The laptop port is fine (at least it was good untill I installed ubuntu on it last night). It used to work with windows.

---

### Post by Buntumatic on 2012-01-12
Alright, then correct driver may be not loaded, did you check with [http://kmuto.jp/debian/hcl/](http://kmuto.jp/debian/hcl/)

---

### Post by zillowzillow on 2012-01-12
Thanks for the link to check drivers, it is very useful.
However the problem is still mystery as the link reports that my driver (b44) is good:

14e4170c    Yes    Broadcom Corporation    BCM4401-B0 100Base-TX    b44    v2.6.25-

---

### Post by Buntumatic on 2012-01-12
I've no further ideas, in my experience when lower network layer reports no connection then it has always been a hardware issue.

---

