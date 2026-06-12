---
title: "android + openswan + xl2tpd = not working(bad avp size)"
date: 2011-05-19
forum: Networking &amp; Wireless
---

### Post by dEnnA on 2011-05-19
Hi, I'm trying to get my android 2.3 phone to connect to my vpn server and I followed this guide ([http://ubuntuforums.org/showthread.php?t=1645473&highlight=xl2tpd](http://ubuntuforums.org/showthread.php?t=1645473&highlight=xl2tpd)) but it isn't working..
I've tried compiling both xl2tpd and openswan myself but it resulted with the same error
I can connect to my vpn from windows 7 but when I try to connect with my phone I get this in the log file (jumped to the interesting part & highlighted the line that's bothering me most)
```

May 19 19:06:44 ubuntu pppd[12718]: found interface eth0 for proxy arp
May 19 19:06:44 ubuntu pppd[12718]: local  IP address 192.168.0.196
May 19 19:06:44 ubuntu pppd[12718]: remote IP address 192.168.0.200
May 19 19:06:44 ubuntu pppd[12718]: Script /etc/ppp/ip-up started (pid 12721)
May 19 19:06:44 ubuntu pppd[12718]: Script /etc/ppp/ip-up finished (pid 12721), status = 0x0
May 19 19:06:54 ubuntu pppd[12718]: rcvd [LCP TermReq id=0x2 "User request"]
May 19 19:06:54 ubuntu pppd[12718]: LCP terminated by peer (User request)
May 19 19:06:54 ubuntu pppd[12718]: Connect time 0.2 minutes.
May 19 19:06:54 ubuntu pppd[12718]: Sent 696 bytes, received 1447 bytes.
May 19 19:06:54 ubuntu pppd[12718]: Script /etc/ppp/ip-down started (pid 12739)
May 19 19:06:54 ubuntu pppd[12718]: sent [LCP TermAck id=0x2]
May 19 19:06:54 ubuntu pppd[12718]: Script /etc/ppp/ip-down finished (pid 12739), status = 0x0
[COLOR="Red"]May 19 19:06:54 ubuntu xl2tpd[12459]: result_code_avp: avp is incorrect size.  8 < 10[/COLOR]
May 19 19:06:54 ubuntu xl2tpd[12459]: handle_avps: Bad exit status handling attribute 1 (Result Code) on mandatory packet.
May 19 19:06:54 ubuntu pppd[12718]: Modem hangup
May 19 19:06:54 ubuntu pppd[12718]: Connection terminated.
May 19 19:06:54 ubuntu xl2tpd[12459]: Terminating pppd: sending TERM signal to pid 12718
May 19 19:06:54 ubuntu xl2tpd[12459]: Connection 43506 closed to 77.218.96.182, port 48823 (Result Code: expected at least 10, got 8)
May 19 19:06:54 ubuntu pppd[12718]: Exit.
```

My config files are as follows:
/etc/ipsec.conf
```

config setup
        nat_traversal=yes
        virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
        oe=off
        protostack=netkey

include /etc/ipsec.d/l2tp-psk.conf
```
/etc/ipsec.d/l2tp-psk.conf
```

conn L2TP-PSK-NAT
        rightsubnet=vhost:%priv
        also=L2TP-PSK-noNAT
conn L2TP-PSK-noNAT
        authby=secret
        pfs=no
        auto=add
        keyingtries=3
        rekey=no
        ikelifetime=8h
        keylife=1h
        type=transport
        left=192.168.0.196
        leftnexthop=192.168.0.1
        leftprotoport=17/1701
        right=%any
        rightprotoport=17/%any
```
/etc/xl2tpd/xl2tpd.conf
```

[global]
ipsec saref = yes
[lns default]
ip range = 192.168.0.200-192.168.0.254
local ip = 192.168.0.196
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options
length bit = yes
```
/etc/ppp/options
```

require-mschap-v2
ms-dns 192.168.0.1
asyncmap 0
auth
crtscts
lock
hide-password
modem
debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
idle 1800
connect-delay 5000

```
And finally, the output from ipsec verify
```

Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.28/K2.6.38-8-generic-pae (netkey)
Checking for IPsec support in kernel                            [OK]
NETKEY detected, testing for disabled ICMP send_redirects       [OK]
NETKEY detected, testing for disabled ICMP accept_redirects     [OK]
Checking that pluto is running                                  [OK]
Pluto listening for IKE on udp 500                              [OK]
Pluto listening for NAT-T on udp 4500                           [OK]
Checking for 'ip' command                                       [OK]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]
```

---

### Post by atca on 2011-08-07
[is this any help? IPSec, XL2TP, PPP and Android]("http://confoundedtech.blogspot.com/2011/08/android-nexus-one-ipsec-psk-vpn-with.html")

---

