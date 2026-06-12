---
title: "low internet speed"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by vangop on 2011-01-28
Hi,
dualboot win7 and ubuntu 10.10 x64.
All was fine. Suddenly I noticed that download speed on ubuntu is 100-500Kb/s, while it has to be 100Mbps. Same resources download 9Mb/s on dualboot win, so it is not hardware/isp problem. This problem occurs when connecting by eth cable. The connection is over ppp0 vpn tunnel.
The ping is very slow - around 300ms even to my ISP.
The only soft I was installing recently is tor/vidalia/privoxy, but I removed them all.
I also noticed that avahi-daemon is running, can it be causing the delays?
Can you plz suggest the ways to diagnose and solve the problem.
Thanks!

---

### Post by bd83862 on 2011-01-29
Try and disable IPV6. If the ifconfig -a shows both IPV6 and IPV4 address then IPV6 may be disabled. If grub is installed then edit /etc/default/grub. Change  GRUB_CMDLINE_LINUX_DEFAULT=&quot;quiet splash&quot;  to GRUB_CMDLINE_LINUX_DEFAULT=&quot;ipv6.disable=1 quiet splash&quot; and then run   "update-grub" . After re-boot the speed should be fine.

---

### Post by vangop on 2011-02-01
Hi,
I've disabled the ip6, but this didn't seem to help. The speed is the same. :(
I suspect this is related to MTU or routing.
```
$ tracepath google.com -n
 1:  X.X.X.X                                           0.135ms pmtu 1400
 1:  94.27.127.24                                        319.884ms 
 1:  94.27.127.24                                        319.874ms 
 2:  94.27.127.209                                       319.975ms 
 3:  94.27.24.182                                        349.948ms asymm  6 
 4:  94.27.24.153                                        350.089ms asymm  6 
 5:  94.27.25.5                                          350.040ms asymm  6 
 6:  94.27.25.18                                         349.452ms 
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply

```

```
$ ping google.com
PING google.com (209.85.149.104) 56(84) bytes of data.
64 bytes from ber01s02-in-f104.1e100.net (209.85.149.104): icmp_req=1 ttl=55 time=351 ms
64 bytes from ber01s02-in-f104.1e100.net (209.85.149.104): icmp_req=2 ttl=55 time=370 ms
64 bytes from ber01s02-in-f104.1e100.net (209.85.149.104): icmp_req=3 ttl=55 time=70.7 ms
64 bytes from ber01s02-in-f104.1e100.net (209.85.149.104): icmp_req=4 ttl=55 time=129 ms
64 bytes from ber01s02-in-f104.1e100.net (209.85.149.104): icmp_req=5 ttl=55 time=198 ms
64 bytes from ber01s02-in-f104.1e100.net (209.85.149.104): icmp_req=6 ttl=55 time=268 ms
64 bytes from ber01s02-in-f104.1e100.net (209.85.149.104): icmp_req=7 ttl=55 time=327 ms
64 bytes from ber01s02-in-f104.1e100.net (209.85.149.104): icmp_req=8 ttl=55 time=367 ms
64 bytes from ber01s02-in-f104.1e100.net (209.85.149.104): icmp_req=9 ttl=55 time=68.5 ms

```
but the next ping is
```
$ ping google.com
PING google.com (209.85.149.147) 56(84) bytes of data.
64 bytes from ber01s02-in-f147.1e100.net (209.85.149.147): icmp_req=1 ttl=55 time=68.9 ms
64 bytes from ber01s02-in-f147.1e100.net (209.85.149.147): icmp_req=2 ttl=55 time=67.0 ms
64 bytes from ber01s02-in-f147.1e100.net (209.85.149.147): icmp_req=3 ttl=55 time=65.9 ms
64 bytes from ber01s02-in-f147.1e100.net (209.85.149.147): icmp_req=4 ttl=55 time=65.9 ms
64 bytes from ber01s02-in-f147.1e100.net (209.85.149.147): icmp_req=5 ttl=55 time=64.6 ms
64 bytes from ber01s02-in-f147.1e100.net (209.85.149.147): icmp_req=6 ttl=55 time=63.0 ms
64 bytes from ber01s02-in-f147.1e100.net (209.85.149.147): icmp_req=7 ttl=55 time=60.9 ms
64 bytes from ber01s02-in-f147.1e100.net (209.85.149.147): icmp_req=8 ttl=55 time=69.8 ms

```

```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 88:ae:1d:b3:34:bb  
          inet addr:10.22.X.X  Bcast:10.22.213.255  Mask:255.255.254.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:57714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78259077 (78.2 MB)  TX bytes:4753387 (4.7 MB)
          Interrupt:20 Memory:d7400000-d7420000 

eth1      Link encap:Ethernet  HWaddr 5c:ac:4c:1a:6a:91  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:99 errors:0 dropped:0 overruns:0 frame:0
          TX packets:99 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9676 (9.6 KB)  TX bytes:9676 (9.6 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:94.27.X.X  P-t-P:94.27.127.24  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:57169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:75135215 (75.1 MB)  TX bytes:2774687 (2.7 MB)

```

---

### Post by mips on 2011-02-01
What happens if you change your DNS settings and statically configure the DNS addresses for say OpenDNS or any of these [http://theos.in/windows-xp/free-fast-public-dns-server-list/](http://theos.in/windows-xp/free-fast-public-dns-server-list/) ?

Try an MTU of 1492 and 1478

---

### Post by vangop on 2011-02-02
Hi Mips,
you mean MTU for ppp0 or eth0?
If I change dns the speed is the same.

---

### Post by mips on 2011-02-02
Eth0

Also try making it smaller than 1400.

Did you disable IPv6?

---

### Post by vangop on 2011-02-02
Yes, ipv6 is disabled as bd83862 suggested.
The speed is the same with whatever I set to eth0 mtu :(
I setup the vpn via NM, also use resolveconf if that matters.

I just tried the old way of connection by sudo pon provider, and the speed went to 2mb/s on direct, and upto 4Mb/s on torrents. 
syslog when connecting via pon is
```
Feb  2 11:46:18 illidan pppd[13113]: Connect: ppp0 <--> /dev/pts/1
Feb  2 11:46:18 illidan NetworkManager[1559]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb  2 11:46:18 illidan NetworkManager[1559]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Feb  2 11:46:18 illidan modem-manager: (net/ppp0): could not get port's parent device
Feb  2 11:46:18 illidan pptp[13346]: anon log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Feb  2 11:46:18 illidan pptp[13354]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Feb  2 11:46:18 illidan pptp[13354]: anon log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Feb  2 11:46:18 illidan pptp[13354]: anon log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Feb  2 11:46:19 illidan pptp[13354]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Feb  2 11:46:19 illidan pptp[13354]: anon log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Feb  2 11:46:19 illidan pptp[13354]: anon log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 51321).
Feb  2 11:46:22 illidan pppd[13113]: CHAP authentication succeeded
Feb  2 11:46:22 illidan pppd[13113]: CHAP authentication succeeded
Feb  2 11:46:22 illidan pppd[13113]: replacing old default route to eth0 [10.22.212.1]
Feb  2 11:46:22 illidan pppd[13113]: Cannot determine ethernet address for proxy ARP
Feb  2 11:46:22 illidan pppd[13113]: local  IP address 94.27.98.83
Feb  2 11:46:22 illidan pppd[13113]: remote IP address 94.27.127.24
Feb  2 11:47:19 illidan pptp[13354]: anon log[logecho:pptp_ctrl.c:677]: Echo Reply received.
Feb  2 11:48:19 illidan pptp[13354]: anon log[logecho:pptp_ctrl.c:677]: Echo Request received.
Feb  2 11:48:19 illidan pptp[13354]: anon log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 6 'Echo-Reply'

```

syslog when connecting via NM
```

Feb  2 11:53:02 illidan NetworkManager[1559]: <info> Starting VPN service 'org.freedesktop.NetworkManager.pptp'...
Feb  2 11:53:02 illidan NetworkManager[1559]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' started (org.freedesktop.NetworkManager.pptp), PID 13808
Feb  2 11:53:02 illidan NetworkManager[1559]: <info> VPN service 'org.freedesktop.NetworkManager.pptp' appeared, activating connections
Feb  2 11:53:02 illidan NetworkManager[1559]: <info> VPN plugin state changed: 1
Feb  2 11:53:02 illidan NetworkManager[1559]: <info> VPN plugin state changed: 3
Feb  2 11:53:02 illidan NetworkManager[1559]: <info> VPN connection 'beeline' (Connect) reply received.
Feb  2 11:53:02 illidan pppd[13810]: Plugin /usr/lib/pppd/2.4.5//nm-pptp-pppd-plugin.so loaded.
Feb  2 11:53:02 illidan pppd[13810]: pppd 2.4.5 started by root, uid 0
Feb  2 11:53:02 illidan pppd[13810]: Using interface ppp0
Feb  2 11:53:02 illidan pppd[13810]: Connect: ppp0 <--> /dev/pts/1
Feb  2 11:53:02 illidan NetworkManager[1559]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb  2 11:53:02 illidan NetworkManager[1559]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Feb  2 11:53:02 illidan modem-manager: (net/ppp0): could not get port's parent device
Feb  2 11:53:02 illidan pptp[13815]: nm-pptp-service-13808 log[main:pptp.c:314]: The synchronous pptp option is NOT activated
Feb  2 11:53:02 illidan pptp[13823]: nm-pptp-service-13808 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 1 'Start-Control-Connection-Request'
Feb  2 11:53:02 illidan pptp[13823]: nm-pptp-service-13808 log[ctrlp_disp:pptp_ctrl.c:739]: Received Start Control Connection Reply
Feb  2 11:53:02 illidan pptp[13823]: nm-pptp-service-13808 log[ctrlp_disp:pptp_ctrl.c:773]: Client connection established.
Feb  2 11:53:03 illidan pptp[13823]: nm-pptp-service-13808 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 7 'Outgoing-Call-Request'
Feb  2 11:53:03 illidan pptp[13823]: nm-pptp-service-13808 log[ctrlp_disp:pptp_ctrl.c:858]: Received Outgoing Call Reply.
Feb  2 11:53:03 illidan pptp[13823]: nm-pptp-service-13808 log[ctrlp_disp:pptp_ctrl.c:897]: Outgoing call established (call ID 0, peer's call ID 12276).
Feb  2 11:53:06 illidan pppd[13810]: CHAP authentication succeeded
Feb  2 11:53:06 illidan pppd[13810]: CHAP authentication succeeded
Feb  2 11:53:06 illidan pppd[13810]: Cannot determine ethernet address for proxy ARP
Feb  2 11:53:06 illidan pppd[13810]: local  IP address 94.27.92.125
Feb  2 11:53:06 illidan pppd[13810]: remote IP address 94.27.127.29
Feb  2 11:53:06 illidan pppd[13810]: primary   DNS address 212.109.32.5
Feb  2 11:53:06 illidan pppd[13810]: secondary DNS address 212.109.32.9
Feb  2 11:53:06 illidan NetworkManager[1559]: <info> VPN connection 'beeline' (IP Config Get) reply received.
Feb  2 11:53:06 illidan NetworkManager[1559]: <info> VPN Gateway: 10.0.0.19
Feb  2 11:53:06 illidan NetworkManager[1559]: <info> Tunnel Device: ppp0
Feb  2 11:53:06 illidan NetworkManager[1559]: <info> Internal IP4 Address: 94.27.92.125
Feb  2 11:53:06 illidan NetworkManager[1559]: <info> Internal IP4 Prefix: 32
Feb  2 11:53:06 illidan NetworkManager[1559]: <info> Internal IP4 Point-to-Point Address: 94.27.127.29
Feb  2 11:53:06 illidan NetworkManager[1559]: <info> Maximum Segment Size (MSS): 0
Feb  2 11:53:06 illidan NetworkManager[1559]: <info> Internal IP4 DNS: 212.109.32.5
Feb  2 11:53:06 illidan NetworkManager[1559]: <info> Internal IP4 DNS: 212.109.32.9
Feb  2 11:53:06 illidan NetworkManager[1559]: <info> DNS Domain: '(none)'
Feb  2 11:53:07 illidan NetworkManager[1559]: <info> (ppp0): writing resolv.conf to /sbin/resolvconf
Feb  2 11:53:08 illidan NetworkManager[1559]: <info> VPN connection 'beeline' (IP Config Get) complete.
Feb  2 11:53:08 illidan NetworkManager[1559]: <info> (ppp0): writing resolv.conf to /sbin/resolvconf
Feb  2 11:53:08 illidan NetworkManager[1559]: <info> Policy set 'beeline' (ppp0) as default for IPv4 routing and DNS.
Feb  2 11:53:08 illidan NetworkManager[1559]: <info> VPN plugin state changed: 4
Feb  2 11:53:08 illidan nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.


```

Also, when I disconnect NM's vpn
```

Feb  2 11:55:24 illidan pppd[13810]: Terminating on signal 15
Feb  2 11:55:24 illidan pppd[13810]: Connect time 2.3 minutes.
Feb  2 11:55:24 illidan pppd[13810]: Sent 506426 bytes, received 12996497 bytes.
Feb  2 11:55:24 illidan NetworkManager[1559]: <info> (ppp0): writing resolv.conf to /sbin/resolvconf
Feb  2 11:55:24 illidan pppd[13810]: Child process /usr/sbin/pptp vpn2.beeline.ua --nolaunchpppd --loglevel 0 --logstring nm-pptp-service-13808 (pid 13814) terminated with signal 15
Feb  2 11:55:24 illidan pppd[13810]: Connection terminated.
Feb  2 11:55:24 illidan avahi-daemon[13622]: Withdrawing workstation service for ppp0.
Feb  2 11:55:24 illidan pptp[13815]: nm-pptp-service-13808 warn[decaps_hdlc:pptp_gre.c:204]: short read (-1): Input/output error
Feb  2 11:55:24 illidan pptp[13815]: nm-pptp-service-13808 warn[decaps_hdlc:pptp_gre.c:216]: pppd may have shutdown, see pppd log
Feb  2 11:55:24 illidan pptp[13823]: nm-pptp-service-13808 log[callmgr_main:pptp_callmgr.c:234]: Closing connection (unhandled)
Feb  2 11:55:24 illidan pptp[13823]: nm-pptp-service-13808 log[ctrlp_rep:pptp_ctrl.c:251]: Sent control packet type is 12 'Call-Clear-Request'
Feb  2 11:55:24 illidan pptp[13823]: nm-pptp-service-13808 log[call_callback:pptp_callmgr.c:79]: Closing connection (call state)
Feb  2 11:55:24 illidan pppd[13810]: Exit.
Feb  2 11:55:25 illidan NetworkManager[1559]: <error> [1296640525.609331] [nm-system.c:183] nm_system_device_set_ip4_route(): (eth0): failed to set IPv4 route: Netlink Error (errno = File exists)
Feb  2 11:55:25 illidan NetworkManager[1559]: <error> [1296640525.609464] [nm-system.c:183] nm_system_device_set_ip4_route(): (eth0): failed to set IPv4 route: Netlink Error (errno = File exists)
Feb  2 11:55:25 illidan NetworkManager[1559]: <error> [1296640525.609561] [nm-system.c:183] nm_system_device_set_ip4_route(): (eth0): failed to set IPv4 route: Netlink Error (errno = File exists)
Feb  2 11:55:25 illidan NetworkManager[1559]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Feb  2 11:55:25 illidan NetworkManager[1559]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Feb  2 11:55:25 illidan NetworkManager[1559]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb  2 11:55:25 illidan nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.

```
Although no errors when disconnecting CLI vpn.

---

### Post by mips on 2011-02-02
What's the VPN for?

Do a traceroute to google on the PON connection & then on the NM connection without the VPN, also do a netstat -r on both.
Next do the same thing but with the VPN running in both and post the output here.

Post the output of the tracroute & netstat -r here.

---

### Post by vangop on 2011-02-02
The VPN is to connect to the internet. I plug the cable to connect to ISP lan, and then dial a vpn.
With PON:
```
akm[16:07:01]:/mnt/wind/bt$ tracepath google.com -n
 1:  94.27.93.3                                            0.110ms pmtu 1460
 1:  94.27.127.29                                         29.119ms 
 1:  94.27.127.29                                         21.227ms 
 2:  94.27.127.209                                        18.689ms 
 3:  94.27.24.182                                         49.992ms asymm  6 
 4:  94.27.24.153                                         49.969ms asymm  6 
 5:  94.27.25.5                                           50.605ms asymm  6 
 6:  94.27.25.18                                          49.976ms 
 7:  no reply
 8:  no reply
 9:  no reply
...

```

```
akm[16:12:18]:/mnt/wind/bt$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
10.0.0.20       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.16       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.19       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.18       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.25       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.24       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.27       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.26       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
94.27.127.29    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.111.0   0.0.0.0         255.255.255.0   U     2      0        0 eth1
10.22.212.0     0.0.0.0         255.255.254.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
10.0.0.0        10.22.212.1     255.0.0.0       UG    0      0        0 eth0
224.0.0.0       0.0.0.0         252.0.0.0       U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

With NM
```
akm[16:13:18]:/mnt/wind/bt$ tracepath google.com -n
 1:  94.27.102.141                                         0.139ms pmtu 1400
 1:  94.27.127.24                                         20.024ms 
 1:  94.27.127.24                                         20.257ms 
 2:  94.27.127.209                                        18.638ms 
 3:  94.27.24.182                                         50.045ms asymm  6 
 4:  94.27.24.153                                         49.943ms asymm  6 
 5:  94.27.25.5                                           51.339ms asymm  6 
 6:  94.27.25.18                                          61.142ms 
 7:  no reply
 8:  no reply
 9:  no reply

```

```
akm[16:14:36]:/mnt/wind/bt$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.1     0.0.0.0         255.255.255.255 UH    0      0        0 eth0
10.0.0.20       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.16       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.19       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.18       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.25       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.24       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.27       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.27       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
10.0.0.26       10.22.212.1     255.255.255.255 UGH   0      0        0 eth0
94.27.127.24    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.111.0   0.0.0.0         255.255.255.0   U     2      0        0 eth1
10.22.212.0     0.0.0.0         255.255.254.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
10.0.0.0        10.22.212.1     255.0.0.0       UG    0      0        0 eth0
224.0.0.0       0.0.0.0         252.0.0.0       U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

---

### Post by mips on 2011-02-02
A VPN to get internet access? That's a new one for me.

Who is your ISP, got a link? Would like to check it out.

---

