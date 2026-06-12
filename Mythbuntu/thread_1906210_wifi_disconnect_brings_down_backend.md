---
title: "wifi disconnect brings down backend"
date: 2012-01-08
forum: Mythbuntu
---

### Post by ZedThou on 2012-01-08
This is driving me nuts. A spotty wifi Internet connection on the backend keeps getting disconnected and every time it happens the mythtv-backend process is killed. Any clues as to what might be causing this?

Some details: the system is a combined FE/BE with an HDHomeRun connected by ethernet. The Internet connection is wifi. The distribution is 11.10 and the mythtv packages are 2:0.24.1+fixes.20120106.

There's nothing in the backend log that explains why it's being killed. Just the usual startup messages when it restarts. Here are typical syslog entries when this happens

```

Jan  8 16:21:06 mythtv kernel: [51928.063872] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan  8 16:21:06 mythtv kernel: [51928.063890] cfg80211: Restoring regulatory settings
Jan  8 16:21:06 mythtv kernel: [51928.063908] cfg80211: Calling CRDA to update world regulatory domain
Jan  8 16:21:06 mythtv kernel: [51928.543238] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jan  8 16:21:06 mythtv kernel: [51928.543249] cfg80211: World regulatory domain updated:
Jan  8 16:21:06 mythtv kernel: [51928.543253] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  8 16:21:06 mythtv kernel: [51928.543261] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 16:21:06 mythtv kernel: [51928.543267] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  8 16:21:06 mythtv kernel: [51928.543272] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  8 16:21:06 mythtv kernel: [51928.543278] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 16:21:06 mythtv kernel: [51928.543284] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 16:21:07 mythtv kernel: [51929.275306] wlan0: authenticate with e0:91:f5:02:62:20 (try 1)
Jan  8 16:21:07 mythtv kernel: [51929.277395] wlan0: authenticated
Jan  8 16:21:07 mythtv kernel: [51929.277488] wlan0: associate with e0:91:f5:02:62:20 (try 1)
Jan  8 16:21:07 mythtv kernel: [51929.283582] wlan0: RX AssocResp from e0:91:f5:02:62:20 (capab=0x431 status=0 aid=1)
Jan  8 16:21:07 mythtv kernel: [51929.283594] wlan0: associated
Jan  8 16:21:08 mythtv dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jan  8 16:21:08 mythtv dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jan  8 16:21:08 mythtv dhclient: All rights reserved.
Jan  8 16:21:08 mythtv dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  8 16:21:08 mythtv dhclient:
Jan  8 16:21:08 mythtv dhclient: Listening on LPF/wlan0/00:25:d3:3d:98:cb
Jan  8 16:21:08 mythtv dhclient: Sending on   LPF/wlan0/00:25:d3:3d:98:cb
Jan  8 16:21:08 mythtv dhclient: Sending on   Socket/fallback
Jan  8 16:21:08 mythtv dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Jan  8 16:21:08 mythtv kernel: [51930.743199] wlan0: deauthenticating from e0:91:f5:02:62:20 by local choice (reason=3)
Jan  8 16:21:09 mythtv kernel: [51930.899501] cfg80211: All devices are disconnected, going to restore regulatory settings
Jan  8 16:21:09 mythtv kernel: [51930.899535] cfg80211: Restoring regulatory settings
Jan  8 16:21:09 mythtv kernel: [51930.899563] cfg80211: Calling CRDA to update world regulatory domain
Jan  8 16:21:09 mythtv kernel: [51930.917945] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jan  8 16:21:09 mythtv kernel: [51930.917958] cfg80211: World regulatory domain updated:
Jan  8 16:21:09 mythtv kernel: [51930.917964] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jan  8 16:21:09 mythtv kernel: [51930.917973] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 16:21:09 mythtv kernel: [51930.917982] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  8 16:21:09 mythtv kernel: [51930.917990] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jan  8 16:21:09 mythtv kernel: [51930.917998] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 16:21:09 mythtv kernel: [51930.918006] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jan  8 16:21:09 mythtv kernel: [51931.014661] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  8 16:21:11 mythtv kernel: [51933.126662] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  8 16:21:14 mythtv dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jan  8 16:21:14 mythtv dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jan  8 16:21:14 mythtv dhclient: All rights reserved.
Jan  8 16:21:14 mythtv dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  8 16:21:14 mythtv dhclient:
Jan  8 16:21:14 mythtv dhclient: Listening on LPF/wlan0/00:25:d3:3d:98:cb
Jan  8 16:21:14 mythtv dhclient: Sending on   LPF/wlan0/00:25:d3:3d:98:cb
Jan  8 16:21:14 mythtv dhclient: Sending on   Socket/fallback
Jan  8 16:21:14 mythtv dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Jan  8 16:21:14 mythtv dhclient: send_packet: Network is unreachable
Jan  8 16:21:14 mythtv dhclient: send_packet: please consult README file regarding broadcast address.
Jan  8 16:21:14 mythtv kernel: [51936.241645] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  8 16:21:15 mythtv dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jan  8 16:21:15 mythtv dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jan  8 16:21:15 mythtv dhclient: All rights reserved.
Jan  8 16:21:15 mythtv dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  8 16:21:15 mythtv dhclient:
Jan  8 16:21:15 mythtv dhclient: Listening on LPF/wlan0/00:25:d3:3d:98:cb
Jan  8 16:21:15 mythtv dhclient: Sending on   LPF/wlan0/00:25:d3:3d:98:cb
Jan  8 16:21:15 mythtv dhclient: Sending on   Socket/fallback
Jan  8 16:21:15 mythtv dhclient: DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Jan  8 16:21:15 mythtv dhclient: send_packet: Network is unreachable
Jan  8 16:21:15 mythtv dhclient: send_packet: please consult README file regarding broadcast address.
Jan  8 16:21:16 mythtv kernel: [51937.906290] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  8 16:21:18 mythtv kernel: [51940.481708] wlan0: authenticate with e0:91:f5:02:62:20 (try 1)
Jan  8 16:21:18 mythtv kernel: [51940.483721] wlan0: authenticated
Jan  8 16:21:18 mythtv kernel: [51940.483817] wlan0: associate with e0:91:f5:02:62:20 (try 1)
Jan  8 16:21:18 mythtv kernel: [51940.487906] wlan0: RX AssocResp from e0:91:f5:02:62:20 (capab=0x431 status=0 aid=1)
Jan  8 16:21:18 mythtv kernel: [51940.487919] wlan0: associated
Jan  8 16:21:18 mythtv kernel: [51940.497905] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jan  8 16:21:19 mythtv dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Jan  8 16:21:19 mythtv dhclient: Copyright 2004-2010 Internet Systems Consortium.
Jan  8 16:21:19 mythtv dhclient: All rights reserved.
Jan  8 16:21:19 mythtv dhclient: For info, please visit https://www.isc.org/software/dhcp/
Jan  8 16:21:19 mythtv dhclient:
Jan  8 16:21:19 mythtv dhclient: Listening on LPF/wlan0/00:25:d3:3d:98:cb
Jan  8 16:21:19 mythtv dhclient: Sending on   LPF/wlan0/00:25:d3:3d:98:cb
Jan  8 16:21:19 mythtv dhclient: Sending on   Socket/fallback
Jan  8 16:21:19 mythtv dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jan  8 16:21:21 mythtv dhclient: DHCPOFFER of 192.168.1.37 from 192.168.1.1
Jan  8 16:21:21 mythtv dhclient: DHCPREQUEST of 192.168.1.37 on wlan0 to 255.255.255.255 port 67
Jan  8 16:21:21 mythtv dhclient: DHCPACK of 192.168.1.37 from 192.168.1.1
Jan  8 16:21:21 mythtv dhclient: bound to 192.168.1.37 -- renewal in 41135 seconds.
Jan  8 16:21:21 mythtv kernel: [51942.995484] init: mythtv-backend main process (30673) killed by TERM signal
Jan  8 16:21:22 mythtv ntpd[30796]: ntpd exiting on signal 15
Jan  8 16:21:29 mythtv kernel: [51951.088028] wlan0: no IPv6 routers present
Jan  8 16:21:33 mythtv ntpdate[31454]: adjust time server 173.203.122.111 offset 0.005606 sec
Jan  8 16:21:34 mythtv ntpd[31535]: ntpd 4.2.6p2@1.2194 Fri Sep  2 18:42:25 UTC 2011 (1)
Jan  8 16:21:34 mythtv ntpd[31536]: proto: precision = 0.207 usec
Jan  8 16:21:34 mythtv ntpd[31536]: ntp_io: estimated max descriptors: 1024, initial socket boundary: 16
Jan  8 16:21:34 mythtv ntpd[31536]: Listen and drop on 0 v4wildcard 0.0.0.0 UDP 123
Jan  8 16:21:34 mythtv ntpd[31536]: Listen and drop on 1 v6wildcard :: UDP 123
Jan  8 16:21:34 mythtv ntpd[31536]: Listen normally on 2 lo 127.0.0.1 UDP 123
Jan  8 16:21:34 mythtv ntpd[31536]: Listen normally on 3 eth0 169.254.1.1 UDP 123
Jan  8 16:21:34 mythtv ntpd[31536]: Listen normally on 4 wlan0 192.168.1.37 UDP 123
Jan  8 16:21:34 mythtv ntpd[31536]: Listen normally on 5 wlan0 fe80::225:d3ff:fe3d:98cb UDP 123
Jan  8 16:21:34 mythtv ntpd[31536]: Listen normally on 6 eth0 fe80::201:2eff:fe27:5335 UDP 123
Jan  8 16:21:34 mythtv ntpd[31536]: Listen normally on 7 lo ::1 UDP 123

```

---

### Post by nickrout on 2012-01-08
probably because the backend needs to be bound to an IP address, and if the IP address disappears, the backend will miss it. Is the backend bound to your wireless IP?

Alternatively, but related, the backend needs to be connected to mysql, which happens over the network.

---

### Post by ZedThou on 2012-01-08
In backend setup the host address is 127.1, and the mysql connection is localhost as well. netstat output is pasted below, 192.168.1.37 is the wifi interface. I'm also using wicd instead of network-manager, I wonder if that has anything to do with the problem.

```

$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 *:6543                  *:*                     LISTEN
tcp        0      0 *:6544                  *:*                     LISTEN
tcp        0      0 *:www                   *:*                     LISTEN
tcp        0      0 *:6547                  *:*                     LISTEN
tcp        0      0 *:ssh                   *:*                     LISTEN
tcp        0      0 localhost.localdom:6010 *:*                     LISTEN
tcp        0      0 localhost.localdom:6011 *:*                     LISTEN
tcp        0      0 localhost.localdo:mysql *:*                     LISTEN
tcp        0      0 localhost.localdo:59114 localhost.localdom:6543 ESTABLISHED
tcp        0      0 localhost.localdo:59115 localhost.localdom:6543 ESTABLISHED
tcp        0      0 169.254.1.1:51815       169.254.254.207:65001   ESTABLISHED
tcp        0    224 192.168.1.37:ssh        192.168.1.38:46011      ESTABLISHED
tcp        1      0 localhost.localdo:57893 localhost.localdom:6543 CLOSE_WAIT
tcp        0      0 localhost.localdom:6543 localhost.localdo:59114 ESTABLISHED
tcp        0      0 169.254.1.1:51816       169.254.254.207:65001   ESTABLISHED
tcp        0      0 localhost.localdom:6543 localhost.localdo:59115 ESTABLISHED
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN
tcp6       0      0 mythtv:6010             [::]:*                  LISTEN
tcp6       0      0 mythtv:6011             [::]:*                  LISTEN
udp        0      0 255.255.255.255:1900    *:*
udp        0      0 239.255.255.250:1900    *:*
udp        0      0 *:bootpc                *:*
udp        0      0 192.168.1.37:ntp        *:*
udp        0      0 169.254.1.1:ntp         *:*
udp        0      0 localhost.localdoma:ntp *:*
udp        0      0 *:ntp                   *:*
udp        0      0 *:6549                  *:*
udp        0      0 *:47980                 *:*
udp6       0      0 mythtv:ntp              [::]:*
udp6       0      0 fe80::201:2eff:fe27:ntp [::]:*
udp6       0      0 fe80::225:d3ff:fe3d:ntp [::]:*
udp6       0      0 [::]:ntp                [::]:*

```

---

### Post by ZedThou on 2012-01-08
I moved back from wicd to network-manager and that fixed the problem. No more splitting football games into six different recordings!

---

### Post by JamesNorris on 2012-01-15
> **ZedThou said:**
> I moved back from wicd to network-manager and that fixed the problem. No more splitting football games into six different recordings!

I have also had this very same problem, but moving back to network manager isn't the best solution for me. wicd picks up our dropped connection much better and I'd rather not have to manually reconnect all the time. 

Any other ideas?

---

