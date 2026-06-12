---
title: "Broadcom wireless problems in Ubuntu 9.04 on Dell Latitude D800"
date: 2009-10-06
forum: Networking &amp; Wireless
---

### Post by haydens on 2009-10-06
**Dell Latitude D800 with Dell Wireless 1450 Dual Band WLAN Mini-PCI wireless gizmo.**

I've spent about 10 hours trying to get the wireless functioning in Ubuntu 9.04, which i installed using wubi, so it's a dual boot with XP.   I've downloaded ndiswrapper, i've stolen the exact drivers out of windows\system32\bcmlw5.sys and the related .inf and copied them to the same directory, and loaded them into ndiswrapper.  i've blacklisted ssb, b44, b43.   i've gone into the bios setup and made sure that the wireless card is set to be on.   I've tried the Fn-F2 to turn it on, but there's no visible light that indicates that the wireless card is on that i can see.

In my neighborhood, this machine under XP sees, at times, a half dozen wireless networks, including mine.  Under Ubuntu, it sees nothing.  I'm not skilled in linux, so I don't know if the card is turned off, if the drivers can't driver it, if the windows drivers don't work (the ubuntu drivers didn't work when i first installed ubuntu), but i'm learning the hard way.  I'm trying to get an aging machine to once again be productive, it runs great under Ubuntu, a hell of a lot better than under XP, but no wireless means no go.  

I need help.   I've dumped a bunch of data from the various command line items i've run and tried to eliminate anything that didn't seem to be related to wireless.  I really hope someone's seen this before with this machine and can get this damn thing working.



[B]ndiswrapper -l
[/B]WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4324) present (alternate driver: ssb)

[B]lshw - c network
[/B]*-network:1
       description: Wireless interface
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: wlan0
       version: 03
       serial: 00:0b:7d:1d:11:8b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,12/04/2006, 4.10.4 latency=32 module=ndiswrapper multicast=yes wireless=IEEE 802.11a


[B]lspci:
[/B]02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
==========
**lsusb:**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0416:551d Winbond Electronics Corp. Async Tenkey
Bus 003 Device 002: ID 0416:5519 Winbond Electronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==========
**ifconfig**
wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:1d:11:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Memory:fafec000-fafee000 
===============
**iwconfig**
wlan0     IEEE 802.11a  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
=========
**lsmod**
Module                  Size  Used by
ndiswrapper           193436  0 
============
**dmesg:**
[   27.254443] ndiswrapper: driver bcmwl5 (Broadcom,12/04/2006, 4.10.40.11) loaded
[   27.256139] ndiswrapper 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   27.262846] ndiswrapper: using IRQ 5
[   27.482798] wlan0: ethernet device 00:0b:7d:1d:11:8b using NDIS driver: bcmwl5, version: 0x40a280b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4324.5.conf
[   27.483087] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  230.400501] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  230.407990] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  342.000329] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  342.000338] tg3: eth0: Flow control is on for TX and on for RX.
[  342.000995] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  352.200075] eth0: no IPv6 routers present
====================
**iwlist scan**
jph@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     No scan results
pan0      Interface doesn't support scanning.

---

