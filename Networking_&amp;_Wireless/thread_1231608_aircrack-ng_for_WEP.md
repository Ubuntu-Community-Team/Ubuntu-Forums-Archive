---
title: "aircrack-ng for WEP?"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by walruspanzer on 2009-08-04
[SIZE=2]I somehow managed to lock myself out of my wifi network, and before you ask - no ethernet plugs on my Frankenstein router. I have installed aircrack-ng to attempt to recover my password since its WEP. But I am having issues starting monitor mode on my wireless device. For now I am using my neighbor's unsecured network. If it matters, I successfully completed this process last year but it doesn't seem to want to work this time. I recently did a clean install of  jaunty. 

-- Some background
[/SIZE]```

access@HelloComputer:~$ uname -r
2.6.28-14-generic

access@HelloComputer:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port [8086:27a1] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
...
**03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)**
...
**0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)**
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
...
**03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)**
...
**0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)**

``````

 access@HelloComputer:~$ iwconfig
lo        no wireless extensions.

**eth1 **     IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:201  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

``````
access@HelloComputer:~$ sudo airmon-ng

Interface    Chipset        Driver

eth1        Unknown         wl

pan0      no wireless extensions.

[B][SIZE=3]access@HelloComputer:~$ sudo airmon-ng start eth1 


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
3125    NetworkManager
3143    wpa_supplicant
3150    avahi-daemon
3151    avahi-daemon
3836    dhclient
Process with PID 3836 (dhclient) is running on interface eth1[/SIZE]   [/B]


Interface    Chipset        Driver

eth1        Unknown         wl (monitor mode enabled)

```Then after all that, 
```

access@HelloComputer:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:203  Noise level:163
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

pan0      no wireless extensions.


```[SIZE=2]

I'm a lamen but it seems there is some kind of conflict. Can anyone help? Thanks in advance!
[/SIZE]

---

