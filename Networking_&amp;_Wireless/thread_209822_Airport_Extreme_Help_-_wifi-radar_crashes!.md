---
title: "Airport Extreme Help - wifi-radar crashes!"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by Greywhind on 2006-07-05
I freshly installed Ubuntu on my Intel iMac 17-inch. The network is good when plugged into the computer. I need to get wireless working so that I can move the computer to its final location, so I searched this forum for solutions. I tried the thread on Broadcom Networking ([http://www.ubuntuforums.org/showthread.php?t=185174)]("http://www.ubuntuforums.org/showthread.php?t=185174%29"), which seemed to work fine until I got to the point with using Wifi-Radar to set up the connection - it sees the network and says I can connect, then shows a dialog box asking for setup. I put in the password and set everything to auto as it says in another thread here, then click ok. Immediately, a small box shows saying "Configuring IP" or such, and the cursor freezes. Then nothing happens, and I have to restart.

PLEASE HELP!! I have looked everywhere - I tried the default drivers listed on that post, and the apple driver called AppleAirPort2. Neither works.

My iwconfig says:
```

greywhind@greywhind-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"PC Phish Net"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

``` 
And I really hope this doesn't involve reinstalling...

---

### Post by Bayleo on 2006-07-06
Wifi radar was acting up for me too (mouse cursor flying everywhere), and I could not discern the cause, so I just switched apps and found that network manager and wireless assistant (it's built for KDE, but it still works) functioned okay.

---

### Post by Greywhind on 2006-07-06
Update: I tried a few things since, and nothing has worked so far. I seem to have a similar problem to other people in that I can now find the network (see below):

```
greywhind@greywhind-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"PC Fish Net"  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.457 GHz  Access Point: 00:11:24:27:C0:78
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level=2/3  Noise level=184/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

But when I do an iwlist eth1 scan I get no scan results and when I sudo dhclient eth1 it fails as below:
```

greywhind@greywhind-desktop:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:16:cb:b1:97:22
Sending on   LPF/eth1/00:16:cb:b1:97:22
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Please tell me if anyone has solved this problem on Airport Extreme on Intel, or point me to a solution (hopefully specifically for Airport -- I am hesitant to try to adapt a non-Airport solution to my specific problem, since I'm not very familiar with Linux yet).

This is REALLY ruining my day... so I would be very happy to get some help.

---

### Post by Greywhind on 2006-07-06
Now I have found that when my internet cable is plugged into my router, not to the iMac, iwlist eth1 scan does return the correct information. It is supposedly seeing the Airport Extreme base station and getting signal. But still the same when I try to get an ip ](*,).

---

### Post by enkoan on 2008-02-27
Having the same problem in Debian Lenny with a 12" iBook G4

---

