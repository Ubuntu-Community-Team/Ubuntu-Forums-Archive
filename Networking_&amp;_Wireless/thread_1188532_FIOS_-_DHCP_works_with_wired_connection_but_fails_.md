---
title: "FIOS - DHCP works with wired connection but fails on wireless"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by jbrid on 2009-06-15
I am baffled...

I just got Verizon FIOS. It works fine on XP (wired or wireless) and a wired connection to my Kubuntu 9.04 intallation. When I try to use the wireless on Kubuntu the DHCP step fails. There is no DHCP offer. I am reading this from the wcid log:

Log showing failed wireless connection:

```


2009/06/15 19:55:18 :: Attempting to authenticate...
2009/06/15 19:55:18 :: ['wpa_supplicant', '-B', '-i', 'eth1', '-c', '/var/lib/wicd/configurations/001f90d4bc74', '-D', 'wext']
2009/06/15 19:55:18 :: Putting interface up...
2009/06/15 19:55:18 :: ifconfig eth1 up
2009/06/15 19:55:18 :: iwconfig eth1 mode managed
2009/06/15 19:55:18 :: ['iwconfig', 'eth1', 'essid', '??????', 'channel', '1', 'ap', '00:1F:90:D4:BC:74']
2009/06/15 19:55:18 :: WPA_CLI RESULT IS DISCONNECTED
2009/06/15 19:55:19 :: WPA_CLI RESULT IS COMPLETED
2009/06/15 19:55:19 :: Running DHCP
2009/06/15 19:55:19 :: /sbin/dhclient **eth1**
2009/06/15 19:49:42 :: Listening on LPF/eth1/00:13:ce:2b:0a:ce
2009/06/15 19:49:42 :: Sending on   LPF/eth1/00:13:ce:2b:0a:ce
2009/06/15 19:49:42 :: Sending on   Socket/fallback
2009/06/15 19:49:43 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
2009/06/15 19:49:47 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
2009/06/15 19:49:52 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
2009/06/15 19:50:04 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
2009/06/15 19:50:22 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
2009/06/15 19:50:38 :: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
2009/06/15 19:50:44 :: No DHCPOFFERS received.
2009/06/15 19:50:44 :: No working leases in persistent database - sleeping.
2009/06/15 19:50:49 :: iwconfig eth1
2009/06/15 19:50:51 :: returning automatically reconnect when connection drops True
2009/06/15 19:50:53 :: DHCP connection failed
2009/06/15 19:50:53 :: exiting connection thread



```


Log showing successful wired connection
```


2009/06/15 19:58:18 :: ifconfig eth0 up
2009/06/15 19:58:18 :: Running DHCP
2009/06/15 19:58:18 :: /sbin/dhclient **eth0**
2009/06/15 19:58:22 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
2009/06/15 19:58:23 :: DHCPOFFER of 192.168.1.2 from 192.168.1.1
2009/06/15 19:58:23 :: DHCPREQUEST of 192.168.1.2 on eth0 to 255.255.255.255 port 67
2009/06/15 19:58:23 :: DHCPACK of 192.168.1.2 from 192.168.1.1
2009/06/15 19:58:24 :: bound to 192.168.1.2 -- renewal in 34043 seconds.
2009/06/15 19:58:24 :: DHCP connection successful
2009/06/15 19:58:24 :: Connecting thread exiting.
2009/06/15 19:58:24 :: ifconfig eth0
2009/06/15 19:58:24 :: IP Address is: 192.168.1.2


``` 

Can anyone provide a guess as to why this is happening or a suggestion on what to look at to get more info?


Thanks for the help! :confused::confused:

---

### Post by Iowan on 2009-06-15
I doubt it'll help, but [this]("http://ubuntuforums.org/showthread.php?t=1156441") thread details disabling the rfc3442 option in dhclient.conf.

---

