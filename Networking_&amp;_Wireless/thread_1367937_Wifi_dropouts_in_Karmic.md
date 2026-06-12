---
title: "Wifi dropouts in Karmic"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by RobertSwipe on 2009-12-30
I have frequent wifi dropouts on my Dell XPS M1210 laptop at home when running 9.10.

In many cases when this happens, the wireless network is still listed in the Network Manager drop-down list, but the system refuses to connect to it. Sometimes it can be "cured" by disabling wireless networking then re-enabling it, but this is hit and miss.

I've taken a two dumps of portions of syslog when this happens - one when the wifi connects normally, and one where the system is refusing to connect. Hopefully, these may give someone a clue as to what's causing the problem.

Sitting in the same place in the house running Windows (spit) on the same laptop has no dropout problems, and the fact that NM can actually see the network leads me to believe that there is some other problem going on.

Any help and advice gratefully received!

Trevor

---

### Post by RobertSwipe on 2009-12-30
Some additional info on my dropout problem:

Output from lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)


Also, whenever I try to copy files (using Nautilus) from this laptop to the house server (also running 9.10), the copy process stops after only a few Kb have been copied and the wifi jams up.

The server is connected to the network via a wired connection and remains active, but the laptop has to be put through all the NM stops/starts/reboots until it connects again.

Trevor

---

### Post by zaphod777 on 2009-12-30
I have a Dell XPS 1530 and experience similar problems  using WICD over network manager seamed to help but I still get random disconnects a lot and often have to reboot my laptop to reconnect.

---

### Post by RobertSwipe on 2009-12-30
Thanks - I tried WICD but it made little difference so switched back to NM.

I think the key messages in my syslog are the ones that suddenly crop up which read "Failed to initiate AP scan". I can't understand why this can't be done.

---

### Post by zaphod777 on 2009-12-31
Where did you find those logs I want to check mine too.

---

### Post by ffej123 on 2009-12-31
I am also having a similar problem. I have an XPS M170 with Ubuntu 9.10 newly installed. I had the same problem when I had the 8.1 version installed. I wiped my drive and installed 9.10 from scratch. No upgrade.

I can browse the web but when I start to download something my netgear router looses its connection. My wifi shows that I still have a connection but it stops downloading. The only way to fix the issue is to cut power to my router and plug it back in. I haven't had this problem with my mac or any of my windows machines but when ubuntu causes my router to crash i lose wireless to everything until I restart the router. Earlier this evening I took this laptop to a friends who also has comcast and the same netgear wireless rangemax router as I and couldn't replicate this problem. Seems to be a problem with a router setting.

I originally had this same issue about a year ago with 8.1 which I never resolved. I would really like to continue using linux but I cant live with this issue. Any help would be appreciated.

---

### Post by RobertSwipe on 2009-12-31
> **zaphod777 said:**
> Where did you find those logs I want to check mine too.

System > Administration > Log File Viewer. Then select "syslog" in the lefthand list.

You need to scroll to the bottom of the list, and watch out for new messages which cause the list to be refreshed constantly!

Trevor

---

### Post by RobertSwipe on 2009-12-31
> **ffej123 said:**
> I am also having a similar problem. I have an XPS M170 with Ubuntu 9.10 newly installed. I had the same problem when I had the 8.1 version installed. I wiped my drive and installed 9.10 from scratch. No upgrade.

<snip>

 Any help would be appreciated.

I'm using a Belkin router (N+ wireless model) which is running some flavour of Linux (I can telnet into it quite happily) and so in theory at least, shouldn't have problems with my Ubuntu laptops and server - I would have expected more problems when I have to use Windows!

The syslog messages seem to suggest that one of the NM low level routines is failing somehow - the inability to initiate a scan, and some other messages which contain error numbers tell me that some routine is struggling to cope with a frequent condition as the wifi signal level fluctuate.

Why this stops me from copying files from my XPS to the server is a real mystery though! I'll see if I can get some better log messages when this happens.

Trevor

---

### Post by zaphod777 on 2010-01-01
I have been trying to get it to flip out on me but for some reason it has been very stable. 

It must know I want to find the problem.

---

### Post by zaphod777 on 2010-01-01
Okay it just bombed out on me this is what i see in the logs

> Jan  2 00:53:49 zaphod kernel: [51988.861701] wlan0: deauthenticated from 00:1d:73:8e:de:98 (Reason: 6)
Jan  2 00:53:51 zaphod kernel: [51990.843290] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:53:51 zaphod kernel: [51991.045484] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 2)
Jan  2 00:53:51 zaphod kernel: [51991.057015] wlan0: direct probe responded
Jan  2 00:53:51 zaphod kernel: [51991.057026] wlan0: authenticate with AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:53:51 zaphod kernel: [51991.128126] wlan0: authenticated
Jan  2 00:53:51 zaphod kernel: [51991.128185] wlan0: associate with AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:53:51 zaphod kernel: [51991.161978] wlan0: RX ReassocResp from 00:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan  2 00:53:51 zaphod kernel: [51991.161987] wlan0: associated
Jan  2 00:53:54 zaphod kernel: [51994.172671] wlan0: deauthenticated from 00:1d:73:8e:de:98 (Reason: 2)
Jan  2 00:53:54 zaphod kernel: [51994.349911] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:53:55 zaphod kernel: [51994.427173] wlan0: direct probe responded
Jan  2 00:53:55 zaphod kernel: [51994.427185] wlan0: authenticate with AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:53:55 zaphod kernel: [51994.469813] wlan0: authenticated
Jan  2 00:53:55 zaphod kernel: [51994.469867] wlan0: associate with AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:53:55 zaphod kernel: [51994.487290] wlan0: RX ReassocResp from 00:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan  2 00:53:55 zaphod kernel: [51994.487300] wlan0: associated
Jan  2 00:53:58 zaphod kernel: [51997.594034] iwlagn 0000:0b:00.0: iwl_tx_agg_start on ra = 00:1d:73:8e:de:98 tid = 0
Jan  2 00:55:53 zaphod kernel: [52112.576819] wlan0: deauthenticated from 00:1d:73:8e:de:98 (Reason: 6)
Jan  2 00:55:55 zaphod kernel: [52114.468044] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:55:55 zaphod kernel: [52114.542968] wlan0: direct probe responded
Jan  2 00:55:55 zaphod kernel: [52114.542979] wlan0: authenticate with AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:55:55 zaphod kernel: [52114.610508] wlan0: authenticated
Jan  2 00:55:55 zaphod kernel: [52114.610577] wlan0: associate with AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:55:55 zaphod kernel: [52114.618293] wlan0: RX ReassocResp from 00:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan  2 00:55:55 zaphod kernel: [52114.618302] wlan0: associated
Jan  2 00:55:58 zaphod kernel: [52117.632166] wlan0: deauthenticated from 00:1d:73:8e:de:98 (Reason: 2)
Jan  2 00:55:58 zaphod kernel: [52117.806273] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:55:58 zaphod kernel: [52117.841472] wlan0: direct probe responded
Jan  2 00:55:58 zaphod kernel: [52117.841483] wlan0: authenticate with AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:55:58 zaphod kernel: [52117.870337] wlan0: authenticated
Jan  2 00:55:58 zaphod kernel: [52117.870395] wlan0: associate with AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:55:58 zaphod kernel: [52117.874692] wlan0: RX ReassocResp from 00:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan  2 00:55:58 zaphod kernel: [52117.874701] wlan0: associated
Jan  2 00:56:08 zaphod kernel: [52128.382757] iwlagn 0000:0b:00.0: iwl_tx_agg_start on ra = 00:1d:73:8e:de:98 tid = 0
Jan  2 00:57:30 zaphod kernel: [52209.728716] wlan0: deauthenticated from 00:1d:73:8e:de:98 (Reason: 6)
Jan  2 00:57:32 zaphod kernel: [52211.626800] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:57:32 zaphod kernel: [52211.645198] wlan0: direct probe responded
Jan  2 00:57:32 zaphod kernel: [52211.645209] wlan0: authenticate with AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:57:32 zaphod kernel: [52211.647927] wlan0: authenticated
Jan  2 00:57:32 zaphod kernel: [52211.647975] wlan0: associate with AP 00:1d:73:8e:de:98 (try 1)
Jan  2 00:57:32 zaphod kernel: [52211.667272] wlan0: RX ReassocResp from 00:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan  2 00:57:32 zaphod kernel: [52211.667282] wlan0: associated
Jan  2 00:57:33 zaphod kernel: [52213.329083] iwlagn 0000:0b:00.0: iwl_tx_agg_start on ra = 00:1d:73:8e:de:98 tid = 0

seams to be related to 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200500](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/200500)

[http://www.mikegerwitz.com/2008/10/15/ralink-wireless-random-disconnects-no-proberesp/](http://www.mikegerwitz.com/2008/10/15/ralink-wireless-random-disconnects-no-proberesp/)

This bug is for Karmic here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483322](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/483322)

please everyone post in this bug and maybe we will get a fix.
no fix that I have found yet.

Hopefully this will point some smarter than me in the right direction.

---

### Post by zaphod777 on 2010-01-08
I just downloaded and installed the latest updates and it looks like many deal with wireless I am downloading a lot of torrents now and so far so good. I am hoping for the best.

---

### Post by zaphod777 on 2010-01-08
no good I have had it drop twice in the last hour

logs below

Jan  8 14:38:36 zaphod kernel: [ 3272.095728] wlan0: deauthenticated from 00:1d:73:8e:de:98 (Reason: 6)
Jan  8 14:38:38 zaphod kernel: [ 3273.945859] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:38:38 zaphod kernel: [ 3273.953790] wlan0: direct probe responded
Jan  8 14:38:38 zaphod kernel: [ 3273.953801] wlan0: authenticate with AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:38:38 zaphod kernel: [ 3273.965871] wlan0: authenticated
Jan  8 14:38:38 zaphod kernel: [ 3273.965920] wlan0: associate with AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:38:38 zaphod kernel: [ 3274.017230] wlan0: RX ReassocResp from 00:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan  8 14:38:38 zaphod kernel: [ 3274.017239] wlan0: associated
Jan  8 14:38:41 zaphod kernel: [ 3277.032640] wlan0: deauthenticated from 00:1d:73:8e:de:98 (Reason: 2)
Jan  8 14:38:41 zaphod kernel: [ 3277.171662] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:38:41 zaphod kernel: [ 3277.176531] wlan0: direct probe responded
Jan  8 14:38:41 zaphod kernel: [ 3277.176543] wlan0: authenticate with AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:38:41 zaphod kernel: [ 3277.179256] wlan0: authenticated
Jan  8 14:38:41 zaphod kernel: [ 3277.179309] wlan0: associate with AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:38:41 zaphod kernel: [ 3277.183303] wlan0: RX ReassocResp from 00:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan  8 14:38:41 zaphod kernel: [ 3277.183311] wlan0: associated
Jan  8 14:38:43 zaphod kernel: [ 3278.658011] iwlagn 0000:0b:00.0: iwl_tx_agg_start on ra = 00:1d:73:8e:de:98 tid = 0
Jan  8 14:41:22 zaphod kernel: [ 3438.199490] wlan0: deauthenticated from 00:1d:73:8e:de:98 (Reason: 6)
Jan  8 14:41:36 zaphod kernel: [ 3452.287427] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:41:37 zaphod kernel: [ 3452.480060] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 2)
Jan  8 14:41:37 zaphod dhclient: There is already a pid file /var/run/dhclient.pid with pid 9873
Jan  8 14:41:37 zaphod dhclient: killed old client process, removed PID file
Jan  8 14:41:37 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  8 14:41:37 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  8 14:41:37 zaphod dhclient: All rights reserved.
Jan  8 14:41:37 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  8 14:41:37 zaphod dhclient: 
Jan  8 14:41:37 zaphod dhclient: Listening on LPF/eth0/00:15:c5:82:50:cc
Jan  8 14:41:37 zaphod dhclient: Sending on   LPF/eth0/00:15:c5:82:50:cc
Jan  8 14:41:37 zaphod dhclient: Sending on   Socket/fallback
Jan  8 14:41:37 zaphod kernel: [ 3452.682695] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 3)
Jan  8 14:41:37 zaphod dhclient: DHCPRELEASE on eth0 to 192.168.11.1 port 67
Jan  8 14:41:37 zaphod kernel: [ 3452.882599] wlan0: direct probe to AP 00:1d:73:8e:de:98 timed out
Jan  8 14:41:37 zaphod kernel: [ 3453.260198] sky2 eth0: disabling interface
Jan  8 14:41:37 zaphod kernel: [ 3453.272442] sky2 eth0: enabling interface
Jan  8 14:41:37 zaphod kernel: [ 3453.273516] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan  8 14:41:38 zaphod avahi-daemon[946]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  8 14:41:38 zaphod avahi-daemon[946]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.11.100.
Jan  8 14:41:38 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  8 14:41:38 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  8 14:41:38 zaphod dhclient: All rights reserved.
Jan  8 14:41:38 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  8 14:41:38 zaphod dhclient: 
Jan  8 14:41:38 zaphod avahi-daemon[946]: Withdrawing address record for fe80::21d:e0ff:fe35:481d on wlan0.
Jan  8 14:41:38 zaphod avahi-daemon[946]: Withdrawing address record for 192.168.11.100 on wlan0.
Jan  8 14:41:38 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  8 14:41:38 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  8 14:41:38 zaphod dhclient: Sending on   Socket/fallback
Jan  8 14:41:38 zaphod dhclient: DHCPRELEASE on wlan0 to 192.168.11.1 port 67
Jan  8 14:41:38 zaphod dhclient: send_packet: Network is unreachable
Jan  8 14:41:38 zaphod dhclient: send_packet: please consult README file regarding broadcast address.
Jan  8 14:41:38 zaphod kernel: [ 3453.920075] Registered led device: iwl-phy0::radio
Jan  8 14:41:38 zaphod kernel: [ 3453.920122] Registered led device: iwl-phy0::assoc
Jan  8 14:41:38 zaphod kernel: [ 3453.920162] Registered led device: iwl-phy0::RX
Jan  8 14:41:38 zaphod kernel: [ 3453.920203] Registered led device: iwl-phy0::TX
Jan  8 14:41:38 zaphod kernel: [ 3454.115633] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  8 14:41:38 zaphod kernel: [ 3454.170657] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:41:38 zaphod kernel: [ 3454.300930] wlan0: deauthenticating from 00:1d:73:8e:de:98 by local choice (reason=3)
Jan  8 14:41:38 zaphod kernel: [ 3454.301042] wlan0: deauthenticating from 00:1d:73:8e:de:98 by local choice (reason=3)
Jan  8 14:41:50 zaphod INADYN[1358]: INADYN:IP: Error '0x6e' resolving host name 'checkip.dyndns.org'
Jan  8 14:41:50 zaphod INADYN[1358]: W: DYNDNS: Error 'RC_IP_INVALID_REMOTE_ADDR' (0x12) when talking to IP server
Jan  8 14:41:50 zaphod INADYN[1358]: W:'RC_IP_INVALID_REMOTE_ADDR' (0x12) updating the IPs. (it 57)
Jan  8 14:42:14 zaphod dhclient: Internet Systems Consortium DHCP Client V3.1.2
Jan  8 14:42:14 zaphod dhclient: Copyright 2004-2008 Internet Systems Consortium.
Jan  8 14:42:14 zaphod dhclient: All rights reserved.
Jan  8 14:42:14 zaphod dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jan  8 14:42:14 zaphod dhclient: 
Jan  8 14:42:14 zaphod kernel: [ 3490.150877] Registered led device: iwl-phy0::radio
Jan  8 14:42:14 zaphod kernel: [ 3490.150907] Registered led device: iwl-phy0::assoc
Jan  8 14:42:14 zaphod kernel: [ 3490.150934] Registered led device: iwl-phy0::RX
Jan  8 14:42:14 zaphod kernel: [ 3490.150962] Registered led device: iwl-phy0::TX
Jan  8 14:42:14 zaphod kernel: [ 3490.212351] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  8 14:42:14 zaphod kernel: [ 3490.213270] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:42:14 zaphod kernel: [ 3490.218168] wlan0: direct probe responded
Jan  8 14:42:14 zaphod kernel: [ 3490.218178] wlan0: authenticate with AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:42:14 zaphod kernel: [ 3490.222859] wlan0: authenticated
Jan  8 14:42:14 zaphod kernel: [ 3490.222906] wlan0: associate with AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:42:14 zaphod kernel: [ 3490.226616] wlan0: RX AssocResp from 00:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan  8 14:42:14 zaphod kernel: [ 3490.226625] wlan0: associated
Jan  8 14:42:14 zaphod kernel: [ 3490.256032] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan  8 14:42:15 zaphod dhclient: Listening on LPF/wlan0/00:1d:e0:35:48:1d
Jan  8 14:42:15 zaphod dhclient: Sending on   LPF/wlan0/00:1d:e0:35:48:1d
Jan  8 14:42:15 zaphod dhclient: Sending on   Socket/fallback
Jan  8 14:42:16 zaphod avahi-daemon[946]: Registering new address record for fe80::21d:e0ff:fe35:481d on wlan0.*.
Jan  8 14:42:19 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  8 14:42:22 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Jan  8 14:42:24 zaphod kernel: [ 3500.292523] wlan0: deauthenticating from 00:1d:73:8e:de:98 by local choice (reason=3)
Jan  8 14:42:24 zaphod kernel: [ 3500.292591] wlan0: deauthenticating from 00:1d:73:8e:de:98 by local choice (reason=3)
Jan  8 14:42:24 zaphod kernel: [ 3500.360666] wlan0: deauthenticating from 00:1d:73:8e:de:98 by local choice (reason=3)
Jan  8 14:42:24 zaphod kernel: [ 3500.404244] wlan0: direct probe to AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:42:24 zaphod kernel: [ 3500.409176] wlan0: direct probe responded
Jan  8 14:42:24 zaphod kernel: [ 3500.409186] wlan0: authenticate with AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:42:24 zaphod kernel: [ 3500.411734] wlan0: authenticated
Jan  8 14:42:24 zaphod kernel: [ 3500.411784] wlan0: associate with AP 00:1d:73:8e:de:98 (try 1)
Jan  8 14:42:25 zaphod kernel: [ 3500.415692] wlan0: RX AssocResp from 00:1d:73:8e:de:98 (capab=0x431 status=0 aid=1)
Jan  8 14:42:25 zaphod kernel: [ 3500.415700] wlan0: associated
Jan  8 14:42:25 zaphod kernel: [ 3500.782725] wlan0: no IPv6 routers present
Jan  8 14:42:27 zaphod dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Jan  8 14:42:27 zaphod dhclient: DHCPOFFER of 192.168.11.100 from 192.168.11.1
Jan  8 14:42:27 zaphod dhclient: DHCPREQUEST of 192.168.11.100 on wlan0 to 255.255.255.255 port 67
Jan  8 14:42:27 zaphod dhclient: DHCPACK of 192.168.11.100 from 192.168.11.1
Jan  8 14:42:27 zaphod avahi-daemon[946]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.11.100.
Jan  8 14:42:27 zaphod avahi-daemon[946]: New relevant interface wlan0.IPv4 for mDNS.
Jan  8 14:42:27 zaphod avahi-daemon[946]: Registering new address record for 192.168.11.100 on wlan0.IPv4.
Jan  8 14:42:27 zaphod dhclient: bound to 192.168.11.100 -- renewal in 83708 seconds.
Jan  8 14:42:28 zaphod kernel: [ 3504.333306] iwlagn 0000:0b:00.0: iwl_tx_agg_start on ra = 00:1d:73:8e:de:98 tid = 0

---

### Post by do0b on 2010-01-24
i have the same issue with my wifi. i'm using a x1530. had 9.04 installed and recently updated to 9.10. wifi was working fine on 9.04 but it keeps dropping and reconnecting every 3-5mins with 9.10.

tried this solution:  [http://ubuntuforums.org/showthread.php?t=1288865](http://ubuntuforums.org/showthread.php?t=1288865) but didnt work

anyone?

---

### Post by zaphod777 on 2010-01-24
I have found no solution so far but it seams to happen more often when downloading torrents I have noticed.

Please check the bug report linked in this thread and mark that it effects you to. Maybe we can get more attention the more people we get to comment on it.

---

### Post by do0b on 2010-01-24
oh mine cant even hold a stable connection. no torrents no nothing. cant even check for updates.

---

### Post by zaphod777 on 2010-01-24
try installing the backports driver packages and maybe switching to wicd instead of network manger. 

That got me to be able to connect but torrents cause my wireless to drop very frequently.

Also the other thread was for broadcom cards not intel.

---

