---
title: "Help with L2TP &amp; IPsec"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by Metallinut on 2011-02-04
I'm hoping someone may be able to help me. First things first:
Ubuntu 10.04 -> VPN server
Various clients to connect, but currently testing with my Motorola Droid (L2TP/IPsec PSK VPN)

I started by following the guide located [here]("http://www.bybacon.com/2010/08/28/l2tp-ipsec-vpn-ubuntu-10-04-server-maciphone-clients/"):

/etc/ipsec.conf:
```
config setup
        # crlcheckinterval=600
        # strictcrlpolicy=yes
        # cachecrls=yes
        nat_traversal=yes
        charonstart=yes
        plutostart=yes


conn L2TP
        authby=psk
        pfs=no
        rekey=no
        type=tunnel
        esp=aes128-sha1
        ike=aes128-sha-modp1024
        left=192.168.1.153
        leftsubnet=192.168.1.0/24
        #left=96.252.123.128
        leftnexthop=%defaultroute
        leftprotoport=17/1701
        right=%any
        rightprotoport=17/%any
        rightsubnetwithin=0.0.0.0/0
        auto=add
```

/etc/xl2tpd/xl2tpd.conf:
```

[global]
        debug network = yes
        debug tunnel = yes

[lns default]
        ip range = 10.0.0.200-10.0.0.254
        local ip = 10.0.0.1
        require chap = yes
        refuse pap = yes
        require authentication = yes
        name = gob
        ppp debug = yes
        pppoptfile = /etc/ppp/options.xl2tpd
        length bit = yes

```

/etc/ppp/options.xl2tpd:
```

ipcp-accept-local
ipcp-accept-remote
ms-dns 4.2.2.2
noccp
auth
crtscts
idle 1800
mtu 1410
mru 1410
nodefaultroute
#defaultroute
debug
lock
proxyarp
connect-delay 5000

```

This setup works fine if I connect via WiFi on the same network (no NAT between). But anytime I connect, either on the cell data network or WiFi from outside my home network it does not work. The Android reports that it connects, then 5 seconds later disconnects. Nothing gets logged in /var/log/auth.log.

Here is the failed connection attempt from /etc/log/syslog:
```

Feb  4 09:16:13 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 69, tunnel = 0, call = 0 ref=0 refhim=0
Feb  4 09:16:13 gob xl2tpd[22660]: get_call: allocating new tunnel for host 174.252.xxx.xxx, port 8990.
Feb  4 09:16:15 gob xl2tpd[22660]: build_fdset: closing down tunnel 39805
Feb  4 09:16:15 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 69, tunnel = 0, call = 0 ref=0 refhim=0
Feb  4 09:16:15 gob xl2tpd[22660]: get_call: allocating new tunnel for host 174.252.xxx.xxx, port 8990.
Feb  4 09:16:15 gob xl2tpd[22660]: control_finish: Peer requested tunnel 35487 twice, ignoring second one.
Feb  4 09:16:15 gob xl2tpd[22660]: build_fdset: closing down tunnel 34534
Feb  4 09:16:15 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 20, tunnel = 29671, call = 0 ref=0 refhim=0
Feb  4 09:16:15 gob xl2tpd[22660]: Connection established to 174.252.xxx.xxx, 8990.  Local: 29671, Remote: 35487 (ref=0/0).  LNS session is 'default'
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 38, tunnel = 29671, call = 0 ref=0 refhim=0
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 40, tunnel = 29671, call = 32976 ref=0 refhim=0
Feb  4 09:16:16 gob xl2tpd[22660]: start_pppd: I'm running:
Feb  4 09:16:16 gob xl2tpd[22660]: "/usr/sbin/pppd"
Feb  4 09:16:16 gob xl2tpd[22660]: "passive"
Feb  4 09:16:16 gob xl2tpd[22660]: "nodetach"
Feb  4 09:16:16 gob xl2tpd[22660]: "10.0.0.1:10.0.0.200"
Feb  4 09:16:16 gob xl2tpd[22660]: "refuse-pap"
Feb  4 09:16:16 gob xl2tpd[22660]: "auth"
Feb  4 09:16:16 gob xl2tpd[22660]: "require-chap"
Feb  4 09:16:16 gob xl2tpd[22660]: "name"
Feb  4 09:16:16 gob xl2tpd[22660]: "gob"
Feb  4 09:16:16 gob xl2tpd[22660]: "debug"
Feb  4 09:16:16 gob xl2tpd[22660]: "file"
Feb  4 09:16:16 gob xl2tpd[22660]: "/etc/ppp/options.xl2tpd"
Feb  4 09:16:16 gob xl2tpd[22660]: "/dev/pts/1"
Feb  4 09:16:16 gob xl2tpd[22660]: Call established with 174.252.xxx.xxx, Local: 32976, Remote: 44115, Serial: -2035741686
Feb  4 09:16:16 gob pppd[11429]: pppd 2.4.5 started by root, uid 0
Feb  4 09:16:16 gob pppd[11429]: using channel 22
Feb  4 09:16:16 gob NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb  4 09:16:16 gob NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Feb  4 09:16:16 gob pppd[11429]: Using interface ppp0
Feb  4 09:16:16 gob pppd[11429]: Connect: ppp0 <--> /dev/pts/1
Feb  4 09:16:16 gob pppd[11429]: sent [LCP ConfReq id=0x1 <mru 1410> <asyncmap 0x0> <auth chap MD5> <magic 0xb302d054> <pcomp> <accomp>]
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 34, tunnel = 29671, call = 32976 ref=0 refhim=0
Feb  4 09:16:16 gob pppd[11429]: rcvd [LCP ConfReq id=0x1 <mru 1400> <asyncmap 0x0> <magic 0x9af08c2> <pcomp> <accomp>]
Feb  4 09:16:16 gob pppd[11429]: sent [LCP ConfAck id=0x1 <mru 1400> <asyncmap 0x0> <magic 0x9af08c2> <pcomp> <accomp>]
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 39, tunnel = 29671, call = 32976 ref=0 refhim=0
Feb  4 09:16:16 gob pppd[11429]: rcvd [LCP ConfAck id=0x1 <mru 1410> <asyncmap 0x0> <auth chap MD5> <magic 0xb302d054> <pcomp> <accomp>]
Feb  4 09:16:16 gob pppd[11429]: sent [LCP EchoReq id=0x0 magic=0xb302d054]
Feb  4 09:16:16 gob pppd[11429]: sent [CHAP Challenge id=0xed <a3e365767fa7d6c7afbe1e78150aaf91>, name = "gob"]
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 18, tunnel = 29671, call = 32976 ref=0 refhim=0
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 33, tunnel = 29671, call = 32976 ref=0 refhim=0
Feb  4 09:16:16 gob pppd[11429]: rcvd [LCP EchoRep id=0x0 magic=0x9af08c2]
Feb  4 09:16:16 gob pppd[11429]: rcvd [CHAP Response id=0xed <2ae04a4fadc50512e4ee057a40f1ca56>, name = "jp"]
Feb  4 09:16:16 gob pppd[11429]: sent [CHAP Success id=0xed "Access granted"]
Feb  4 09:16:16 gob pppd[11429]: sent [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 10.0.0.1>]
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 25, tunnel = 29671, call = 32976 ref=0 refhim=0
Feb  4 09:16:16 gob pppd[11429]: rcvd [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Feb  4 09:16:16 gob pppd[11429]: Unsupported protocol 'Compression Control Protocol' (0x80fd) received
Feb  4 09:16:16 gob pppd[11429]: sent [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 38, tunnel = 29671, call = 32976 ref=0 refhim=0
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 26, tunnel = 29671, call = 32976 ref=0 refhim=0
Feb  4 09:16:16 gob pppd[11429]: rcvd [IPCP ConfReq id=0x1 <compress VJ 0f 01> <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns2 0.0.0.0>]
Feb  4 09:16:16 gob pppd[11429]: sent [IPCP ConfNak id=0x1 <addr 10.0.0.200> <ms-dns1 4.2.2.2> <ms-dns2 4.2.2.2>]
Feb  4 09:16:16 gob pppd[11429]: rcvd [IPCP ConfAck id=0x1 <compress VJ 0f 01> <addr 10.0.0.1>]
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 38, tunnel = 29671, call = 32976 ref=0 refhim=0
Feb  4 09:16:16 gob pppd[11429]: rcvd [IPCP ConfReq id=0x2 <compress VJ 0f 01> <addr 10.0.0.200> <ms-dns1 4.2.2.2> <ms-dns2 4.2.2.2>]
Feb  4 09:16:16 gob pppd[11429]: sent [IPCP ConfAck id=0x2 <compress VJ 0f 01> <addr 10.0.0.200> <ms-dns1 4.2.2.2> <ms-dns2 4.2.2.2>]
Feb  4 09:16:16 gob charon: 05[KNL] 10.0.0.1 appeared on ppp0
Feb  4 09:16:16 gob charon: 05[KNL] 10.0.0.1 disappeared from ppp0
Feb  4 09:16:16 gob charon: 05[KNL] 10.0.0.1 appeared on ppp0
Feb  4 09:16:16 gob charon: 05[KNL] interface ppp0 activated
Feb  4 09:16:16 gob pppd[11429]: Cannot determine ethernet address for proxy ARP
Feb  4 09:16:16 gob pppd[11429]: local  IP address 10.0.0.1
Feb  4 09:16:16 gob pppd[11429]: remote IP address 10.0.0.200
Feb  4 09:16:16 gob pppd[11429]: Script /etc/ppp/ip-up started (pid 11439)
Feb  4 09:16:16 gob xl2tpd[22660]: network_thread: select timeout
Feb  4 09:16:17 gob xl2tpd[22660]: network_thread: select timeout
Feb  4 09:16:17 gob pppd[11429]: Script /etc/ppp/ip-up finished (pid 11439), status = 0x0
Feb  4 09:16:27 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 26, tunnel = 29671, call = 32976 ref=0 refhim=0
Feb  4 09:16:27 gob pppd[11429]: rcvd [LCP TermReq id=0x2 "User request"]
Feb  4 09:16:27 gob pppd[11429]: LCP terminated by peer (User request)
Feb  4 09:16:27 gob pppd[11429]: Connect time 0.2 minutes.
Feb  4 09:16:27 gob pppd[11429]: Sent 0 bytes, received 0 bytes.
Feb  4 09:16:27 gob charon: 05[KNL] interface ppp0 deactivated
Feb  4 09:16:27 gob charon: 05[KNL] 10.0.0.1 disappeared from ppp0
Feb  4 09:16:27 gob pppd[11429]: Script /etc/ppp/ip-down started (pid 11452)
Feb  4 09:16:27 gob pppd[11429]: sent [LCP TermAck id=0x2]
Feb  4 09:16:28 gob xl2tpd[22660]: network_thread: recv packet from 174.252.xxx.xxx, size = 36, tunnel = 29671, call = 0 ref=0 refhim=0
Feb  4 09:16:28 gob xl2tpd[22660]: result_code_avp: avp is incorrect size.  8 < 10
Feb  4 09:16:28 gob xl2tpd[22660]: handle_avps: Bad exit status handling attribute 1 (Result Code) on mandatory packet.
Feb  4 09:16:28 gob xl2tpd[22660]: handle_packet: bad AVP handling!
Feb  4 09:16:28 gob xl2tpd[22660]: network_thread: bad packet
Feb  4 09:16:28 gob xl2tpd[22660]: build_fdset: closing down tunnel 29671
Feb  4 09:16:28 gob pppd[11429]: Modem hangup
Feb  4 09:16:28 gob xl2tpd[22660]: Terminating pppd: sending TERM signal to pid 11429
Feb  4 09:16:28 gob pppd[11429]: Connection terminated.
Feb  4 09:16:28 gob NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb  4 09:16:28 gob pppd[11429]: Waiting for 1 child processes...
Feb  4 09:16:28 gob pppd[11429]:   script /etc/ppp/ip-down, pid 11452
Feb  4 09:16:28 gob pppd[11429]: Terminating on signal 15
Feb  4 09:16:28 gob pppd[11429]: sending SIGTERM to process 11452
Feb  4 09:16:28 gob pppd[11429]: Exit.
Feb  4 09:16:28 gob xl2tpd[22660]: pppd 11429 successfully terminated
Feb  4 09:16:28 gob xl2tpd[22660]: Connection 35487 closed to 174.252.xxx.xxx, port 8990 (Result Code: expected at least 10, got 8)
Feb  4 09:16:28 gob xl2tpd[22660]: network_thread: select returned error 9 (Bad file descriptor)
Feb  4 09:16:29 gob xl2tpd[22660]: network_thread: select timeout
Feb  4 09:16:33 gob xl2tpd[22660]: last message repeated 4 times
Feb  4 09:16:33 gob xl2tpd[22660]: Unable to deliver closing message for tunnel 29671. Destroying anyway.

```

From /var/log/messages:
```

Feb  4 10:01:20 gob pppd[13463]: pppd 2.4.5 started by root, uid 0
Feb  4 10:01:20 gob pppd[13463]: Using interface ppp0
Feb  4 10:01:20 gob pppd[13463]: Connect: ppp0 <--> /dev/pts/1
Feb  4 10:01:21 gob pppd[13463]: Unsupported protocol 'Compression Control Protocol' (0x80fd) received
Feb  4 10:01:21 gob pppd[13463]: local  IP address 10.0.0.1
Feb  4 10:01:21 gob pppd[13463]: remote IP address 10.0.0.200
Feb  4 10:01:32 gob pppd[13463]: LCP terminated by peer (User request)
Feb  4 10:01:32 gob pppd[13463]: Connect time 0.2 minutes.
Feb  4 10:01:32 gob pppd[13463]: Sent 0 bytes, received 0 bytes.
Feb  4 10:01:32 gob pppd[13463]: Modem hangup
Feb  4 10:01:32 gob pppd[13463]: Connection terminated.
Feb  4 10:01:32 gob pppd[13463]: Terminating on signal 15
Feb  4 10:01:32 gob pppd[13463]: Exit.

```
I'm afraid I don't know how else to diagnose and fix this problem.

Thanks!

---

### Post by atca on 2011-08-07
[is this any help? IPSec, XL2TP, PPP and Android]("http://confoundedtech.blogspot.com/2011/08/android-nexus-one-ipsec-psk-vpn-with.html")

---

