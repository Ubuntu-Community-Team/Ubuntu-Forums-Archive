---
title: "nvidia 177 causes live tv to freeze"
date: 2008-12-17
forum: Mythbuntu
---

### Post by laffinet on 2008-12-17
Hi all !

I'm running Mythbuntu 8.10 which by default installs the 177 and 172 nvidia driver. 

My hardware is an onboard nvidia series7 (NVIDIA GeForce 7050PV/nForce 630a onboard an Asus M2N68-VM), connected via HDMI to my LCD TV.

Selecting the 177 driver causes live tv to crash after a few seconds, the 172 driver works fine.

I tried installing the 180 driver (following this [guide]("http://ubuntuforums.org/showthread.php?t=990978")), since it promises a good performance improvement, but it too causes live tv to freeze after a few seconds. 

Any ideas why ? Am I stuck with the 172 ?

One thing I noticed is that after installation of the 180 it does report it correctly in the nvidia configuration tool, however the Mythbuntu Proprietary driver tool only shows 172 and 177.

Thanks for any help !

---

### Post by managementboy on 2008-12-18
> **laffinet said:**
> Hi all !

I'm running Mythbuntu 8.10 which by default installs the 177 and 172 nvidia driver. 

My hardware is an onboard nvidia series7 (NVIDIA GeForce 7050PV/nForce 630a onboard an Asus M2N68-VM), connected via HDMI to my LCD TV.

Selecting the 177 driver causes live tv to crash after a few seconds, the 172 driver works fine.

I tried installing the 180 driver (following this [guide]("http://ubuntuforums.org/showthread.php?t=990978")), since it promises a good performance improvement, but it too causes live tv to freeze after a few seconds. 

Any ideas why ? Am I stuck with the 172 ?

One thing I noticed is that after installation of the 180 it does report it correctly in the nvidia configuration tool, however the Mythbuntu Proprietary driver tool only shows 172 and 177.

Thanks for any help !

did you deinstall the 172 driver first? then use the 180.16 driver, works for me. Then again, try the different playback profiles (CPU- and CPU++) and see if it works.

I use the OpenGL pachtes from here to make it more stable (subjective): [http://www.nvnews.net/vbulletin/showthread.php?t=111308]("http://www.nvnews.net/vbulletin/showthread.php?t=111308")

---

### Post by laffinet on 2009-01-13
Okay, so I deactivated the 172 and the 177 driver in "Hardware Drivers" and manually installed the 180.18 driver. 

=> same issue, live tv freezes after a few seconds (only on some channels though).

Used the same Xorg.conf and the same playback profiles as with the 172. 

Hm. Didn't see any performance improvement on the channels that did work, so don't see a need to update at the moment, but am still wondering if I'm stuck with the 172.

Any ideas ?

---

### Post by laffinet on 2009-03-25
Bump.

Anyone any ideas why any driver above 172 causes livetv to freeze ? And what to do about it ?

---

### Post by nickrout on 2009-03-25
> **laffinet said:**
> Bump.

Anyone any ideas why any driver above 172 causes livetv to freeze ? And what to do about it ?


No but your frontend logs might give someone an idea.

---

### Post by laffinet on 2009-03-26
I can't see anything in the frontend log, so I'm posting everything from the log grabber.

What is actually happening is that after some time (a few minutes) mythfrontend freezes. I checked in terminal and from that moment onwards it uses pretty much 100% CPU.

```
==> /var/log/mythtv/mtd.log <==
mtd started at Thu Mar 26 18:32:36 2009
mtd is running on a host called laffi-mythbox
18:32:36: Waiting for connections/jobs
18:32:36: mtd is listening on port 2442

==> /var/log/mythtv/mythbackend.log <==
2009-03-26 18:35:45.864 AFD: Opened codec 0x86ae7a0, id(MPEG2VIDEO) type(Video)
2009-03-26 18:35:45.866 AFD: codec AC3 has 2 channels
2009-03-26 18:35:45.868 AFD: Opened codec 0x86af380, id(AC3) type(Audio)
2009-03-26 18:35:46.061 Preview: Grabbed preview '/var/lib/mythtv/drive2/recordings2/1020_20090326183450.mpg' 1280x720@64s
2009-03-26 18:35:54.506 TVRec(1): HW Tuner: 1->1
2009-03-26 18:35:55.756 Finished recording Countdown to ONE: channel 1001
2009-03-26 18:35:55.843 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-03-26 18:35:56.018 DTVSM(0) Error: Wrong PMT; pmt->pn(1623) desired(1621)
2009-03-26 18:35:56.039 Using runtime prefix = /usr
2009-03-26 18:35:56.044 Empty LocalHostName.
2009-03-26 18:35:56.045 Using localhost value of laffi-mythbox
2009-03-26 18:35:56.058 New DB connection, total: 1
2009-03-26 18:35:56.072 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:35:56.074 Closing DB connection named 'DBManager0'
2009-03-26 18:35:56.074 DTVSM(0) Error: Wrong PMT; pmt->pn(1624) desired(1621)
2009-03-26 18:35:56.076 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:35:56.083 DTVSM(0) Error: Wrong PMT; pmt->pn(1617) desired(1621)
2009-03-26 18:35:56.098 New DB connection, total: 2
2009-03-26 18:35:56.116 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:35:56.132 Current Schema Version: 1214
2009-03-26 18:35:56.428 Finished recording Neighbours: channel 1010
2009-03-26 18:35:57.486 Finished recording Neighbours: channel 1010
2009-03-26 18:35:57.521 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-03-26 18:35:57.771 Using runtime prefix = /usr
2009-03-26 18:35:57.775 Empty LocalHostName.
2009-03-26 18:35:57.776 Using localhost value of laffi-mythbox
2009-03-26 18:35:57.792 New DB connection, total: 1
2009-03-26 18:35:57.804 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:35:57.807 Closing DB connection named 'DBManager0'
2009-03-26 18:35:57.809 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:35:57.817 New DB connection, total: 2
2009-03-26 18:35:57.823 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:35:57.841 Current Schema Version: 1214
2009-03-26 18:35:57.867 Preview Error: Previewer file '/var/lib/mythtv/drive2/recordings2/1010_20090326183554.mpg' is not valid.
2009-03-26 18:35:57.873 Preview Error: Run() file not local: '/var/lib/mythtv/drive2/recordings2/1010_20090326183554.mpg'
2009-03-26 18:35:57.888 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/drive2/recordings2/1010_20090326183554.mpg.png) exists: 0 readable: 0 size: 0
2009-03-26 18:35:58.656 AFD: Opened codec 0x945c7c0, id(MPEG2VIDEO) type(Video)
2009-03-26 18:35:58.660 AFD: codec AC3 has 2 channels
2009-03-26 18:35:58.662 AFD: Opened codec 0x945cdb0, id(AC3) type(Audio)
2009-03-26 18:35:59.124 Preview: Grabbed preview '/var/lib/mythtv/drive2/recordings2/1001_20090326183543.mpg' 1440x1088@64s
2009-03-26 18:36:44.567 TVRec(1): HW Tuner: 1->1
2009-03-26 18:36:45.899 Finished recording Neighbours: channel 1010
2009-03-26 18:36:46.031 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-03-26 18:36:46.107 DTVSM(0) Error: Wrong PMT; pmt->pn(593) desired(592)
2009-03-26 18:36:46.130 DTVSM(0) Error: Wrong PMT; pmt->pn(594) desired(592)
2009-03-26 18:36:46.151 DTVSM(0) Error: Wrong PMT; pmt->pn(595) desired(592)
2009-03-26 18:36:46.164 Using runtime prefix = /usr
2009-03-26 18:36:46.171 Empty LocalHostName.
2009-03-26 18:36:46.172 Using localhost value of laffi-mythbox
2009-03-26 18:36:46.184 New DB connection, total: 1
2009-03-26 18:36:46.198 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:36:46.213 Closing DB connection named 'DBManager0'
2009-03-26 18:36:46.215 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:36:46.217 New DB connection, total: 2
2009-03-26 18:36:46.223 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:36:46.234 Current Schema Version: 1214
2009-03-26 18:36:46.442 Finished recording Grand Designs "London": channel 1020
2009-03-26 18:36:47.504 Finished recording Grand Designs "London": channel 1020
2009-03-26 18:36:47.570 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-03-26 18:36:47.750 Using runtime prefix = /usr
2009-03-26 18:36:47.755 Empty LocalHostName.
2009-03-26 18:36:47.756 Using localhost value of laffi-mythbox
2009-03-26 18:36:47.770 New DB connection, total: 1
2009-03-26 18:36:47.791 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:36:47.793 Closing DB connection named 'DBManager0'
2009-03-26 18:36:47.795 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:36:47.804 New DB connection, total: 2
2009-03-26 18:36:47.822 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:36:47.825 Current Schema Version: 1214
2009-03-26 18:36:47.843 Preview Error: Previewer file '/var/lib/mythtv/drive2/recordings2/1020_20090326183644.mpg' is not valid.
2009-03-26 18:36:47.845 Preview Error: Run() file not local: '/var/lib/mythtv/drive2/recordings2/1020_20090326183644.mpg'
2009-03-26 18:36:47.877 Preview Error: Preview process not ok.
			fileinfo(/var/lib/mythtv/drive2/recordings2/1020_20090326183644.mpg.png) exists: 0 readable: 0 size: 0
2009-03-26 18:36:48.769 AFD: Opened codec 0x8615890, id(MPEG2VIDEO) type(Video)
2009-03-26 18:36:48.774 AFD: codec MP3 has 2 channels
2009-03-26 18:36:48.780 AFD: Opened codec 0x8615e80, id(MP3) type(Audio)
2009-03-26 18:36:49.008 Preview: Grabbed preview '/var/lib/mythtv/drive2/recordings2/1010_20090326183556.mpg' 720x576@64s
2009-03-26 18:36:50.923 Expiring 19 MBytes for 1001 @ Mon Dec 8 21:30:00 2008 => The Ex List "Climb Every Mountain Biker"
2009-03-26 18:36:50.927 Expiring 14 MBytes for 1020 @ Mon Dec 8 21:35:00 2008 => Enough Rope with Andrew Denton
2009-03-26 18:36:50.930 Expiring 14 MBytes for 1020 @ Mon Dec 8 21:35:00 2008 => Enough Rope with Andrew Denton
2009-03-26 18:36:50.937 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/laffi-mythbox/1001_20081208222717.mpg. File doesn't exist.  Database metadata will not be removed.
2009-03-26 18:36:50.939 Expiring 5 MBytes for 1002 @ Thu Mar 26 18:09:00 2009 => Grand Designs "London"
2009-03-26 18:36:50.960 Expiring 0 MBytes for 1030 @ Thu Mar 26 18:30:00 2009 => World News Australia
2009-03-26 18:36:50.964 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/laffi-mythbox/1020_20081208222736.mpg. File doesn't exist.  Database metadata will not be removed.
2009-03-26 18:36:50.967 Expiring 65 MBytes for 1030 @ Thu Mar 26 18:30:00 2009 => World News Australia
2009-03-26 18:36:50.990 Expiring 0 MBytes for 1020 @ Thu Mar 26 18:09:00 2009 => Grand Designs "London"
2009-03-26 18:36:50.985 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/laffi-mythbox/1020_20081208222811.mpg. File doesn't exist.  Database metadata will not be removed.
2009-03-26 18:38:50.995 Expiring 19 MBytes for 1001 @ Mon Dec 8 21:30:00 2008 => The Ex List "Climb Every Mountain Biker"
2009-03-26 18:38:51.003 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/laffi-mythbox/1001_20081208222717.mpg. File doesn't exist.  Database metadata will not be removed.
2009-03-26 18:38:51.003 Expiring 14 MBytes for 1020 @ Mon Dec 8 21:35:00 2008 => Enough Rope with Andrew Denton
2009-03-26 18:38:51.038 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/laffi-mythbox/1020_20081208222736.mpg. File doesn't exist.  Database metadata will not be removed.
2009-03-26 18:38:51.038 Expiring 14 MBytes for 1020 @ Mon Dec 8 21:35:00 2008 => Enough Rope with Andrew Denton
2009-03-26 18:38:51.046 ERROR when trying to delete file: /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/laffi-mythbox/1020_20081208222811.mpg. File doesn't exist.  Database metadata will not be removed.
2009-03-26 18:38:51.046 Expiring 45 MBytes for 1020 @ Thu Mar 26 18:09:00 2009 => Grand Designs "London"
2009-03-26 18:38:51.059 Expiring 0 MBytes for 1001 @ Thu Mar 26 12:00:00 2009 => Countdown to ONE
2009-03-26 18:38:51.062 Expiring 3 MBytes for 1001 @ Thu Mar 26 12:00:00 2009 => Countdown to ONE
2009-03-26 18:38:51.067 Expiring 0 MBytes for 1010 @ Thu Mar 26 18:30:00 2009 => Neighbours
2009-03-26 18:38:51.075 Expiring 34 MBytes for 1010 @ Thu Mar 26 18:30:00 2009 => Neighbours
2009-03-26 18:38:51.083 Expiring 0 MBytes for 1020 @ Thu Mar 26 18:09:00 2009 => Grand Designs "London"

==> /var/log/mythtv/mythfrontend.log <==
Stopping mythfrontend, remote power OFF
Starting mythfrontend, remote power ON
Starting mythfrontend, remote power ON
Stopping mythfrontend, remote power OFF
Starting mythfrontend, remote power ON
Starting mythfrontend, remote power ON
Stopping mythfrontend, remote power OFF
Starting mythfrontend, remote power ON
Starting mythfrontend, remote power ON
Starting mythfrontend, remote power ON
Stopping mythfrontend, remote power OFF
Starting mythfrontend, remote power ON

==> /var/log/mythtv/mythwelcome.log <==

==> /var/log/syslog <==
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 2 of 5 (Device Configure) starting... 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  (wlan3): device state change: 4 -> 5 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Activation (wlan3/wireless): access point 'Wireless connection 1' has security, but secrets are required. 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  (wlan3): device state change: 5 -> 6 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 2 of 5 (Device Configure) complete. 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 1 of 5 (Device Prepare) started... 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  (wlan3): device state change: 6 -> 4 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 2 of 5 (Device Configure) scheduled... 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 1 of 5 (Device Prepare) complete. 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 2 of 5 (Device Configure) starting... 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  (wlan3): device state change: 4 -> 5 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Activation (wlan3/wireless): connection 'Wireless connection 1' has security, and secrets exist.  No new secrets needed. 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Config: added 'ssid' value 'wireless' 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 2 of 5 (Device Configure) complete. 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 26 18:32:36 laffi-mythbox NetworkManager: <info>  (wlan3): supplicant connection state change: 2 -> 0 
Mar 26 18:32:37 laffi-mythbox kernel: [   29.500016] Clocksource tsc unstable (delta = -76970935 ns)
Mar 26 18:32:41 laffi-mythbox NetworkManager: <info>  (wlan3): supplicant connection state change: 0 -> 2 
Mar 26 18:32:42 laffi-mythbox NetworkManager: <info>  (wlan3): supplicant connection state change: 2 -> 3 
Mar 26 18:32:42 laffi-mythbox kernel: [   34.899723] wlan3: authenticate with AP 00:13:d3:7e:0e:81
Mar 26 18:32:42 laffi-mythbox kernel: [   34.901977] wlan3: authenticated
Mar 26 18:32:42 laffi-mythbox kernel: [   34.901984] wlan3: associate with AP 00:13:d3:7e:0e:81
Mar 26 18:32:42 laffi-mythbox kernel: [   34.904469] wlan3: RX AssocResp from 00:13:d3:7e:0e:81 (capab=0x411 status=0 aid=1)
Mar 26 18:32:42 laffi-mythbox NetworkManager: <info>  (wlan3): supplicant connection state change: 3 -> 4 
Mar 26 18:32:42 laffi-mythbox kernel: [   34.904474] wlan3: associated
Mar 26 18:32:42 laffi-mythbox kernel: [   34.905557] ADDRCONF(NETDEV_CHANGE): wlan3: link becomes ready
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  (wlan3): supplicant connection state change: 4 -> 5 
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  (wlan3): supplicant connection state change: 5 -> 6 
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  (wlan3): supplicant connection state change: 6 -> 7 
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  Activation (wlan3/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'wireless'. 
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 3 of 5 (IP Configure Start) scheduled. 
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 3 of 5 (IP Configure Start) started... 
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  (wlan3): device state change: 5 -> 7 
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Beginning DHCP transaction. 
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  dhclient started with pid 6390 
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 3 of 5 (IP Configure Start) complete. 
Mar 26 18:32:44 laffi-mythbox avahi-daemon[5183]: Registering new address record for fe80::21e:58ff:fe4c:704e on wlan3.*.
Mar 26 18:32:44 laffi-mythbox dhclient: Internet Systems Consortium DHCP Client V3.1.1
Mar 26 18:32:44 laffi-mythbox dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 26 18:32:44 laffi-mythbox dhclient: All rights reserved.
Mar 26 18:32:44 laffi-mythbox dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Mar 26 18:32:44 laffi-mythbox dhclient: 
Mar 26 18:32:44 laffi-mythbox dhclient: wmaster0: unknown hardware address type 801
Mar 26 18:32:44 laffi-mythbox dhclient: wmaster0: unknown hardware address type 801
Mar 26 18:32:44 laffi-mythbox NetworkManager: <info>  DHCP: device wlan3 state changed (null) -> preinit 
Mar 26 18:32:44 laffi-mythbox dhclient: Listening on LPF/wlan3/00:1e:58:4c:70:4e
Mar 26 18:32:44 laffi-mythbox dhclient: Sending on   LPF/wlan3/00:1e:58:4c:70:4e
Mar 26 18:32:44 laffi-mythbox dhclient: Sending on   Socket/fallback
Mar 26 18:32:45 laffi-mythbox dhclient: DHCPDISCOVER on wlan3 to 255.255.255.255 port 67 interval 6
Mar 26 18:32:45 laffi-mythbox dhclient: DHCPOFFER of 192.168.1.104 from 192.168.1.254
Mar 26 18:32:45 laffi-mythbox dhclient: DHCPREQUEST of 192.168.1.104 on wlan3 to 255.255.255.255 port 67
Mar 26 18:32:45 laffi-mythbox dhclient: DHCPACK of 192.168.1.104 from 192.168.1.254
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>  DHCP: device wlan3 state changed preinit -> bound 
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 4 of 5 (IP Configure Get) scheduled... 
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 4 of 5 (IP Configure Get) started... 
Mar 26 18:32:45 laffi-mythbox dhclient: bound to 192.168.1.104 -- renewal in 17964 seconds.
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>    address 192.168.1.104 
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>    prefix 24 (255.255.255.0) 
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>    gateway 192.168.1.254 
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>    hostname 'laffi-mythbox' 
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>    nameserver '192.168.1.254' 
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 5 of 5 (IP Configure Commit) scheduled... 
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 4 of 5 (IP Configure Get) complete. 
Mar 26 18:32:45 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 5 of 5 (IP Configure Commit) started... 
Mar 26 18:32:45 laffi-mythbox avahi-daemon[5183]: Joining mDNS multicast group on interface wlan3.IPv4 with address 192.168.1.104.
Mar 26 18:32:45 laffi-mythbox avahi-daemon[5183]: New relevant interface wlan3.IPv4 for mDNS.
Mar 26 18:32:45 laffi-mythbox avahi-daemon[5183]: Registering new address record for 192.168.1.104 on wlan3.IPv4.
Mar 26 18:32:46 laffi-mythbox NetworkManager: <info>  (wlan3): device state change: 7 -> 8 
Mar 26 18:32:46 laffi-mythbox NetworkManager: <info>  Policy set 'Wireless connection 1' (wlan3) as default for routing and DNS. 
Mar 26 18:32:46 laffi-mythbox NetworkManager: <info>  Activation (wlan3) successful, device activated. 
Mar 26 18:32:46 laffi-mythbox NetworkManager: <info>  Activation (wlan3) Stage 5 of 5 (IP Configure Commit) complete. 
Mar 26 18:32:46 laffi-mythbox nm-dispatcher.action: nm_dispatcher_action: Invalid connection: 'NMSettingWirelessSecurity' / 'wep-key0' invalid: 1
Mar 26 18:32:46 laffi-mythbox ntpd[5686]: ntpd exiting on signal 15
Mar 26 18:32:48 laffi-mythbox ntpdate[6471]: adjust time server 91.189.94.4 offset 0.131662 sec
Mar 26 18:32:48 laffi-mythbox ntpd[6500]: ntpd 4.2.4p4@1.1520-o Tue Jan  6 15:54:48 UTC 2009 (1)
Mar 26 18:32:48 laffi-mythbox ntpd[6501]: precision = 1.000 usec
Mar 26 18:32:48 laffi-mythbox ntpd[6501]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Mar 26 18:32:48 laffi-mythbox ntpd[6501]: Listening on interface #1 wildcard, ::#123 Disabled
Mar 26 18:32:48 laffi-mythbox ntpd[6501]: Listening on interface #2 lo, ::1#123 Enabled
Mar 26 18:32:48 laffi-mythbox ntpd[6501]: Listening on interface #3 wlan3, fe80::21e:58ff:fe4c:704e#123 Enabled
Mar 26 18:32:48 laffi-mythbox ntpd[6501]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Mar 26 18:32:48 laffi-mythbox ntpd[6501]: Listening on interface #5 wlan3, 192.168.1.104#123 Enabled
Mar 26 18:32:48 laffi-mythbox ntpd[6501]: kernel time sync status 0040
Mar 26 18:32:48 laffi-mythbox ntpd[6501]: frequency initialized -33.456 PPM from /var/lib/ntp/ntp.drift
Mar 26 18:32:53 laffi-mythbox kernel: [   45.772019] wlan3: no IPv6 routers present
Mar 26 18:33:15 laffi-mythbox lircd-0.8.4a[4082]: accepted new client on /dev/lircd
Mar 26 18:34:02 laffi-mythbox kernel: [  114.087266] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Mar 26 18:34:02 laffi-mythbox /USR/SBIN/CRON[6677]: (laffi) CMD (nice /usr/bin/mythfilldatabase --graboptions '--daily')
Mar 26 18:37:07 laffi-mythbox ntpd[6501]: synchronized to 91.189.94.4, stratum 2
Mar 26 18:37:07 laffi-mythbox ntpd[6501]: kernel time sync status change 0001
Mar 26 18:37:36 laffi-mythbox NetworkManager: <debug> [1238054856.382606] periodic_update(): Roamed from BSSID 00:13:D3:7E:0E:81 (wireless) to (none) ((none)) 
Mar 26 18:37:42 laffi-mythbox NetworkManager: <debug> [1238054862.386646] periodic_update(): Roamed from BSSID (none) ((none)) to 00:13:D3:7E:0E:81 (wireless) 
Mar 26 18:39:01 laffi-mythbox /USR/SBIN/CRON[7069]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)

==> /var/log/Xorg.0.log <==
	[6] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[7] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[8] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[9] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[10] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[11] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[12] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[13] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[14] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[15] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
	[22] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[23] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "1360x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(II) config/hal: Adding input device Macintosh mouse button emulation
(II) LoadModule: "evdev"

(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.5.2, module version = 2.0.99
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.1
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event0"
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Configuring as mouse
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event1"
(II) Logitech USB Receiver: Found x and y relative axes
(II) Logitech USB Receiver: Found 5 mouse buttons
(II) Logitech USB Receiver: Configuring as mouse
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: MOUSE)
(**) Logitech USB Receiver: YAxisMapping: buttons 4 and 5
(**) Logitech USB Receiver: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event3"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) Logitech USB Receiver: xkb_layout: "de"
(II) config/hal: Adding input device Logitech USB Receiver
(**) Logitech USB Receiver: always reports core events
(**) Logitech USB Receiver: Device: "/dev/input/event2"
(II) Logitech USB Receiver: Found keys
(II) Logitech USB Receiver: Configuring as keyboard
(II) XINPUT: Adding extended input device "Logitech USB Receiver" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Logitech USB Receiver: xkb_rules: "evdev"
(**) Option "xkb_model" "pc105"
(**) Logitech USB Receiver: xkb_model: "pc105"
(**) Option "xkb_layout" "de"
(**) Logitech USB Receiver: xkb_layout: "de"
nvLock: client timed out, taking the lock
nvLock: client timed out, taking the lock
nvLock: client timed out, taking the lock
nvLock: client timed out, taking the lock
nvLock: client timed out, taking the lock
nvLock: client timed out, taking the lock
nvLock: client timed out, taking the lock

==> /home/laffi/.xsession-errors <==

2009-03-26 18:32:36.769 Using runtime prefix = /usr
2009-03-26 18:32:36.781 Empty LocalHostName.
2009-03-26 18:32:36.782 Using localhost value of laffi-mythbox
2009-03-26 18:32:36.822 New DB connection, total: 1
2009-03-26 18:32:36.827 Connected to database 'mythconverg' at host: localhost
2009-03-26 18:32:36.827 Closing DB connection named 'DBManager0'
2009-03-26 18:32:36.828 Connected to database 'mythconverg' at host: localhost
irexec: no process killed
26/03/2009 18:32:36 passing arg to libvncserver: -rfbauth
26/03/2009 18:32:36 passing arg to libvncserver: /root/.vnc/passwd
26/03/2009 18:32:36 passing arg to libvncserver: -rfbport
26/03/2009 18:32:36 passing arg to libvncserver: 5900
26/03/2009 18:32:36 x11vnc version: 0.9.3 lastmod: 2007-09-30
26/03/2009 18:32:36 Using X display :0
26/03/2009 18:32:36 
26/03/2009 18:32:36 ------------------ USEFUL INFORMATION ------------------
26/03/2009 18:32:37 X DAMAGE available on display, using it for polling hints.
26/03/2009 18:32:37   To disable this behavior use: '-noxdamage'
26/03/2009 18:32:37 
26/03/2009 18:32:37 XFIXES available on display, resetting cursor mode
26/03/2009 18:32:37   to: '-cursor most'.
26/03/2009 18:32:37   to disable this behavior use: '-cursor arrow'
26/03/2009 18:32:37   or '-noxfixes'.
26/03/2009 18:32:37 using XFIXES for cursor drawing.
26/03/2009 18:32:37 GrabServer control via XTEST.
26/03/2009 18:32:37 
26/03/2009 18:32:37 Scroll Detection: -scrollcopyrect mode is in effect to
26/03/2009 18:32:37   use RECORD extension to try to detect scrolling windows
26/03/2009 18:32:37   (induced by either user keystroke or mouse input).
26/03/2009 18:32:37   If this yields undesired behavior (poor response, painting
26/03/2009 18:32:37   errors, etc) it may be disabled via: '-noscr'
26/03/2009 18:32:37   Also see the -help entry for tuning parameters.
26/03/2009 18:32:37   You can press 3 Alt_L's (Left "Alt" key) in a row to 
26/03/2009 18:32:37   repaint the screen, also see the -fixscreen option for
26/03/2009 18:32:37   periodic repaints.
26/03/2009 18:32:37 
26/03/2009 18:32:37 XKEYBOARD:
26/03/2009 18:32:37 Switching to -xkb mode to recover these keysyms:
26/03/2009 18:32:37    xkb  noxkb   Keysym  ("X" means present)
26/03/2009 18:32:37    ---  -----   -----------------------------
26/03/2009 18:32:37     X           0x40  at
26/03/2009 18:32:37     X           0x5b  bracketleft
26/03/2009 18:32:37     X           0x5d  bracketright
26/03/2009 18:32:37     X           0x7b  braceleft
26/03/2009 18:32:37     X           0x7d  braceright
26/03/2009 18:32:37     X           0x7c  bar
26/03/2009 18:32:37     X           0x5c  backslash
26/03/2009 18:32:37 
26/03/2009 18:32:37   If this makes the key mapping worse you can
26/03/2009 18:32:37   disable it with the "-noxkb" option.
26/03/2009 18:32:37 
26/03/2009 18:32:37 X FBPM extension not supported.
26/03/2009 18:32:37 X display is capable of DPMS.
26/03/2009 18:32:37 --------------------------------------------------------
26/03/2009 18:32:37 
26/03/2009 18:32:37 Default visual ID: 0x21
26/03/2009 18:32:37 Read initial data from X display into framebuffer.
26/03/2009 18:32:37 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/5440
26/03/2009 18:32:37 
26/03/2009 18:32:37 X display :0.0 is 32bpp depth=24 true color
26/03/2009 18:32:37 
26/03/2009 18:32:37 Listening for VNC connections on TCP port 5900
26/03/2009 18:32:37 
26/03/2009 18:32:37 Xinerama is present and active (e.g. multi-head).
26/03/2009 18:32:37 Xinerama: enabling -xwarppointer mode to try to correct
26/03/2009 18:32:37 Xinerama: mouse pointer motion. XTEST+XINERAMA bug.
26/03/2009 18:32:37 Xinerama: Use -noxwarppointer to force XTEST.
26/03/2009 18:32:37 fb read rate: 257 MB/sec
26/03/2009 18:32:37 screen setup finished.
26/03/2009 18:32:37 

The VNC desktop is:      laffi-mythbox:0
PORT=5900

******************************************************************************
Have you tried the x11vnc '-ncache' VNC client-side pixel caching feature yet?

The scheme stores pixel data offscreen on the VNC viewer side for faster
retrieval.  It should work with any VNC viewer.  Try it by running:

    x11vnc -ncache 10 ...

more info: http://www.karlrunge.com/x11vnc/#faq-client-caching

/usr/bin/startxfce4: X server already running on display :0
** Message: Querying XINPUT extension
** Message: XINPUT extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: Querying XF86Misc extension
** Message: XF86Misc extension found
** Message: Querying Xkb extension
** Message: Xkb extension found
** Message: another SSH agent is running at: /tmp/ssh-fKbYdz6238/agent.6238

** (xfce4-session:6323): WARNING **: Unable to launch "wicd-client" (specified by autostart/wicd-tray.desktop): Failed to execute child process "wicd-client" (No such file or directory)

** (update-notifier:6362): WARNING **: already running?


==> df -h <==
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  5.5G  5.0G  53% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  136K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.9M  1.5G   1% /dev
tmpfs                 1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda6             286G  256G   31G  90% /var/lib
/dev/sdb1             597G  361G  236G  61% /var/lib/mythtv/drive2

==> uname -a <==
Linux laffi-mythbox 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux

==> lspci <==
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7050 PV / nForce 630a (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

==> lsusb <==
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 07d1:3c07 D-Link System Wireless G DWA-110 Adapter
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 002: ID 1784:0008 TopSeed Technology Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:c503 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
==> /proc/driver/nvidia/cards <==

==> /proc/driver/nvidia/registry <==
EnableVia4x: 0
EnableALiAGP: 0
NvAGP: 3
ReqAGPRate: 15
EnableAGPSBA: 0
EnableAGPFW: 0
Mobile: 4294967295
ResmanDebugLevel: 4294967295
RmLogonRC: 1
ModifyDeviceFiles: 1
DeviceFileUID: 0
DeviceFileGID: 0
DeviceFileMode: 438
RemapLimit: 0
UpdateMemoryTypes: 4294967295
UseVBios: 1
RMEdgeIntrCheck: 1
UsePageAttributeTable: 4294967295
EnableMSI: 0
MapRegistersEarly: 0

==> /proc/driver/nvidia/version <==
NVRM version: NVIDIA UNIX x86 Kernel Module  177.82  Tue Nov  4 13:35:57 PST 2008
GCC version:  gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 

==> /proc/driver/nvidia/warnings <==
Model: 		 GeForce 7050 PV / NVIDIA nForce 630a
IRQ:   		 20
Video BIOS: 	 05.67.32.25.00
Card Type: 	 PCI
DMA Size: 	 39 bits
DMA Mask: 	 0x7fffffffff
Bus Location: 	 00.12.0

==> lshw <==
computer
    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.5 dmi-2.5 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2 uuid=40019F7A-8DFE-D511-B389-002215D4B9C6
  *-core
       description: Motherboard
       product: M2N68-VM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: [REMOVED]
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0308 (07/18/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu:0
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
          vendor: Advanced Micro Devices [AMD]
          physical id: 3
          bus info: cpu@0
          version: 15.11.2
          serial: [REMOVED]
          slot: AM2
          size: 2600MHz
          capacity: 2600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 128KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 512KiB
             capacity: 1MiB
             capabilities: pipeline-burst internal varies unified
        *-cache:2 DISABLED
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal
     *-memory:0
          description: System Memory
          physical id: 3a
          slot: System board or motherboard
          size: 3GiB
        *-bank:0
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: [REMOVED]
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: DIMM Synchronous 667 MHz (1.5 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: [REMOVED]
             slot: DIMM1
             size: 1GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: [REMOVED]
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: [REMOVED]
             slot: DIMM3
     *-cpu:1
          physical id: 4
          bus info: cpu@1
          version: 15.11.2
          size: 2600MHz
          capacity: 2600MHz
          capabilities: cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: ht bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP67 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
     *-serial UNCLAIMED
          description: SMBus
          product: MCP67 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm cap_list
          configuration: latency=0
     *-usb:0
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:1
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-usb:2
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 13
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3 module=ohci_hcd
     *-usb:3
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: debug pm bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3 module=ehci_hcd
     *-ide:0
          description: IDE interface
          product: MCP67 IDE Controller
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3 module=pata_amd
     *-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel
     *-pci:0
          description: PCI bridge
          product: MCP67 PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
        *-multimedia:0
             description: Multimedia video controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder
             vendor: Conexant Systems, Inc.
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm bus_master cap_list
             configuration: driver=cx8800 latency=64 maxlatency=55 mingnt=20 module=cx8800
        *-multimedia:1
             description: Multimedia controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
             vendor: Conexant Systems, Inc.
             physical id: 6.1
             bus info: pci@0000:01:06.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=cx88_audio latency=64 maxlatency=255 mingnt=4 module=cx88_alsa
        *-multimedia:2
             description: Multimedia controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
             vendor: Conexant Systems, Inc.
             physical id: 6.2
             bus info: pci@0000:01:06.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=cx88-mpeg driver manager latency=64 maxlatency=88 mingnt=6 module=cx8802
        *-multimedia:3
             description: Multimedia video controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder
             vendor: Conexant Systems, Inc.
             physical id: 7
             bus info: pci@0000:01:07.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: vpd pm bus_master cap_list
             configuration: driver=cx8800 latency=64 maxlatency=55 mingnt=20 module=cx8800
        *-multimedia:4
             description: Multimedia controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port]
             vendor: Conexant Systems, Inc.
             physical id: 7.1
             bus info: pci@0000:01:07.1
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=cx88_audio latency=64 maxlatency=255 mingnt=4 module=cx88_alsa
        *-multimedia:5
             description: Multimedia controller
             product: CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port]
             vendor: Conexant Systems, Inc.
             physical id: 7.2
             bus info: pci@0000:01:07.2
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=cx88-mpeg driver manager latency=64 maxlatency=88 mingnt=6 module=cx8802
     *-ide:1
          description: IDE interface
          product: MCP67 AHCI Controller
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          logical name: scsi1
          logical name: scsi2
          logical name: scsi3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide pm bus_master cap_list emulated
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3 module=ahci
        *-cdrom
             description: DVD-RAM writer
             product: CDDVDW SH-S223F
             vendor: TSSTcorp
             physical id: 0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: SB00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
        *-disk:0
             description: ATA Disk
             product: WDC WD3200AAKS-0
             vendor: Western Digital
             physical id: 1
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: [REMOVED]
             size: 298GiB (320GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=000ef831
           *-volume:0
                description: EXT3 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                logical name: /dev/.static/dev
                version: 1.0
                serial: [REMOVED]
                size: 11GiB
                capacity: 11GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                configuration: created=2008-11-12 16:52:14 filesystem=ext3 modified=2009-03-26 18:31:44 mount.fstype=ext3 mount.options=ro,errors=remount-ro,commit=60,data=ordered mounted=2009-03-26 17:42:01 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 286GiB
                capacity: 286GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume:0
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 972MiB
                   capabilities: nofs
              *-logicalvolume:1 UNCLAIMED
                   description: Linux filesystem partition
                   physical id: 6
                   capacity: 285GiB
        *-disk:1
             description: ATA Disk
             product: WDC WD6400AAKS-2
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@3:0.0.0
             logical name: /dev/sdb
             version: 01.0
             serial: [REMOVED]
             size: 596GiB (640GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 signature=0004d2b5
           *-volume UNCLAIMED
                description: Linux filesystem partition
                physical id: 1
                bus info: scsi@3:0.0.0,1
                capacity: 596GiB
                capabilities: primary
     *-network
          description: Ethernet interface
          product: MCP67 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: [REMOVED]
          capacity: 1GB/s
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII
     *-pci:1
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: b
          bus info: pci@0000:00:0b.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:2
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:3
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:4
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: e
          bus info: pci@0000:00:0e.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:5
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: f
          bus info: pci@0000:00:0f.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:6
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-pci:7
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: 11
          bus info: pci@0000:00:11.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci pm msi ht pciexpress bus_master cap_list
          configuration: driver=pcieport-driver
     *-display
          description: VGA compatible controller
          product: GeForce 7050 PV / nForce 630a
          vendor: nVidia Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: pm msi bus_master cap_list
          configuration: driver=nvidia latency=0 module=nvidia
     *-pci:8
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:9
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:10
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:11
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan3
       serial: [REMOVED]
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=[REMOVED] multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: [REMOVED]
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

