---
title: "Wireless Edimax EW-7711ln Problem"
date: 2011-02-18
forum: Networking &amp; Wireless
---

### Post by peterbro on 2011-02-18
Just installed Ubuntu 10.10 server and all working great except the wireless interface. The card is an edimax EW-7711ln.

I installed ndiswrapper using the driver rt2860.zip found here [http://ubuntuforums.org/showthread.php?t=1615304&highlight=ew-7711ln&page=4](http://ubuntuforums.org/showthread.php?t=1615304&highlight=ew-7711ln&page=4)

Then I followed this guide to configure /etc/network/interfaces [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

I think the driver is loading fine but I can't connect to the access point. Here is some debugging output...
```

peter@Peter-Server~$: route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```

```
peter@Peter-Server~$: iwconfig
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:72 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

```
peter@Peter-Server~$: sudo iwlist scan
 Cell 02 - Address: 78:1D:BA:12:6F:5F
                    ESSID:"alleycat"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:81/100  Signal level:-44 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```
```

peter@Peter-Server~$: sudo lshw -C network
  *-network DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:3f:00.0
       logical name: eth0
       version: 01
       serial: 00:15:60:52:07:38
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=half firmware=5752-v3.10 latency=0 link=yes multicast=yes port=twisted pair
       resources: irq:17 memory:e0400000-e040ffff
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 9
       bus info: pci@0000:05:09.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:a6:6b:ca
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2860 driverversion=1.56+Ralink Technology, Corp.,07 latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11g
       resources: irq:18 memory:e0500000-e050ffff
```

```
peter@Peter-Server~$: cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid alleycat
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

So I can scan and see the accesspoint with ssid alleycat but I can't connect. I tried disabling all security to see if it was a problem with my key or some encryption settings but even that didn't work. So frustrating because it seems close to working I must be doing something silly.

Oww and incase anyone is wondering why I am running a server off a wireless interface, its just a LAMP development server on my home network.

Any help would be greatly appreciated.

---

### Post by peterbro on 2011-02-18
Still no luck. Is there any other commands I should post output from?

---

