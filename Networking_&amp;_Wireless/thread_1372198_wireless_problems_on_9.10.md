---
title: "wireless problems on 9.10"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by Kayrosh on 2010-01-04
[SIZE="4"]Well.
My Laptop has inbuilt wireless as most modern laptops do.
I didn't know it had wireless until I switched to Ubuntu as the Operating System. If i had known i probably wouldn't have switched. I do admit that Ubuntu is much quicker at doing things and thought it would be simpler. Yet im only 14 and there is much i don't know about computer stuff. Of course i can use most computers but for Ubuntu that's not the case. I sort of don't like the many codes and stuff you have to input to do things and the way downloading stuff gets much harder to do as i have no idea to download most programs properly. Well i should cut to the chase. I need a way to use wireless on my computer without having to do much typing of codes. Just like a simple code:
sudo apt-get  install everything you need to make your computer able to make wireless connections.
That would be easy. If you got a few codes i could type that wont have spending more than five  to thirty minutes to get ready.
Anything that can help is appreciated.
   [/SIZE]

---

### Post by zaphod777 on 2010-01-04
What kind of laptop are you using and does it show any wireless connection at all?

---

### Post by Kayrosh on 2010-01-04
Compaq presario cq60 
and no i dont see any connections.

---

### Post by zaphod777 on 2010-01-04
try checking under system -> administration -> hardware drivers

do you see an option to enable the wireless driver for your wireless?

you can also try running these two commands

```
sudo apt-get install ubuntu-restricted-extras
```
```
sudo apt-get install linux-backports-modules-karmic

```

I found this thread on your model
[http://ubuntuforums.org/showthread.php?t=1075868](http://ubuntuforums.org/showthread.php?t=1075868)

[http://www.linlap.com/wiki/hp-compaq+presario+cq60](http://www.linlap.com/wiki/hp-compaq+presario+cq60)

---

### Post by tommawat on 2010-01-04
Hello.  I have been searching all day for some way to connect my wifi on my Dell Inspiron Mini using 9.10 (not netbook remix as it crashes too often).

The original dell came with ubuntu factory installed, but was 8.04, and could not be upgraded, so I have installed a fresh version of 9.10.

This is my second install of 9.10.  The first version had problems with wifi, but somehow, I installed the drivers as recommended and somehow it worked.

Now, I have this fresh install, installed the driver, but no wifi appears in the network icon in the panel.  I uninstalled network-manager and installed wicd since it was reported to be more helpful but nothing here. I will now take it off and put back network-manager.

Is there something to do so that 'wireless' appears when i click the network icon in the panel?  If i navigate to the tab for wireless, there are no networks listed, but my Vista computer notebook beside me connects fine.  I know it worked as I did it before, but cannot find how to do it again.  

Please help.

Thanks...

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

