---
title: "WiFi Link 5100 not properely working on 10.10"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by S7VEN on 2010-12-26
Typical "New User" story about a wireless card not working on Ubuntu 10.10. I've read numerous posts and I've tried to use the information given to solve the problem but I still can't figure it out.  

Here's a little information...

**s7ven@S7VEN:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
**s7ven@S7VEN:~$ ifconfig wlan0**
wlan0     Link encap:Ethernet  HWaddr 00:22:fb:78:d1:e0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

**s7ven@S7VEN:~$ dmesg | grep -i wireless**
[   10.716042] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
s7ven@S7VEN:~$ rfkill list all
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
[B]
s7ven@S7VEN:~$ dmesg | grep iwlagn[/B]
[   10.716042] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   10.716046] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   10.716586] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   10.716622] iwlagn 0000:03:00.0: setting latency timer to 64
[   10.716741] iwlagn 0000:03:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   10.745173] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   10.745418] iwlagn 0000:03:00.0: irq 46 for MSI/MSI-X
[   10.786320] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   35.906256] iwlagn 0000:03:00.0: RF_KILL bit toggled to enable radio.
s7ven@S7VEN:~$ dmesg | grep -i wireless
[   10.716042] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
s7ven@S7VEN:~$ cat /proc/net/wireless
Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
[B]
s7ven@S7VEN:~$ sudo lshw -C network[/B]
  *-network               
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:1d:ba:ec:a4:50
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.113 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:d3520000-d3523fff ioport:c000(size=256) memory:d3500000-d351ffff
  *-network
       description: Wireless interface
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:22:fb:78:d1:e0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.35-24-generic firmware=8.24.2.12 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:d2100000-d2101fff


P.S. I also forgot to mention that I did download the drivers and had them extracted in /lib/firmware

**Thank You For Your Time **:D

---

