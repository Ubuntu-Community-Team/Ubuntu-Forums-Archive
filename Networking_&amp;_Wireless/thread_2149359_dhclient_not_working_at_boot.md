---
title: "dhclient not working at boot"
date: 2013-05-28
forum: Networking &amp; Wireless
---

### Post by Poma on 2013-05-28
Here's the problem:

```
    root@home:~# ping 8.8.8.8
    connect: Network is unreachable

    root@home:~# dhclient eth0
    RTNETLINK answers: File exists

    root@home:~# ping 8.8.8.8
    PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
    64 bytes from 8.8.8.8: icmp_req=1 ttl=51 time=16.8 ms
    64 bytes from 8.8.8.8: icmp_req=2 ttl=51 time=16.6 ms
    ^C
    --- 8.8.8.8 ping statistics ---
    2 packets transmitted, 2 received, 0% packet loss, time 1002ms
    rtt min/avg/max/mdev = 16.654/16.737/16.820/0.083 ms
```

Network is working only after I manually invoke dhclient. I don't have NetworkManager (removed it). Here are relevant lines from `/etc/network/interfaces`:

```
    auto eth0
    iface eth0 inet dhcp
```

And here is startup log:

```
    root@home:~# cat /var/log/syslog | grep dhclient
    May 28 21:39:44 home kernel: [    7.237076] type=1400 audit(1369762781.497:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=405 comm="apparmor_parser"
    May 28 21:39:44 home kernel: [    7.238298] type=1400 audit(1369762781.497:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=405 comm="apparmor_parser"
    May 28 21:39:45 home dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8 (xid=0x79607e29)
    May 28 21:39:45 home dhclient: DHCPREQUEST of 192.168.0.103 on eth0 to 255.255.255.255 port 67 (xid=0x79607e29)
    May 28 21:39:45 home dhclient: DHCPOFFER of 192.168.0.103 from 192.168.0.1
    May 28 21:39:45 home dhclient: DHCPACK of 192.168.0.103 from 192.168.0.1
    May 28 21:39:45 home dhclient: bound to 192.168.0.103 -- renewal in 234779 seconds.
    May 28 21:39:45 home kernel: [   11.695666] type=1400 audit(1369762785.953:10): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1154 comm="apparmor_parser"
    May 28 21:40:11 home dhclient: DHCPREQUEST of 192.168.0.103 on eth0 to 255.255.255.255 port 67 (xid=0x2aa61c47)
    May 28 21:40:11 home dhclient: DHCPACK of 192.168.0.103 from 192.168.0.1
    May 28 21:40:11 home dhclient: bound to 192.168.0.103 -- renewal in 243414 seconds.
```

Any ideas what may cause such problem?

---

### Post by Poma on 2013-05-29
I found that default gateway is not added on boot, but it is added when I restart networking service or run dhclient manually. But i didn't found yet what causes such behavior.

---

