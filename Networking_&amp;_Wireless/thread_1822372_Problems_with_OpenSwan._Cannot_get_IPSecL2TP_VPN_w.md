---
title: "Problems with OpenSwan. Cannot get IPSec/L2TP VPN working"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by Lord C on 2011-08-10
Hey all,

I'm having trouble getting OpenSwan VPN to work over L2TP/IPSsec. The server appears to run, but I can't connect from Android or Windows 7.

I've tried a couple of nice tutorials ([Tut1]("http://riobard.com/blog/2010-04-30-l2tp-over-ipsec-ubuntu/") [Tut2]("http://rootmanager.com/ubuntu-ipsec-l2tp-windows-domain-auth/setting-up-openswan-xl2tpd-with-native-windows-clients.html")), but still can't get it working. 

First of, this is what I'm running:
openswan-2.6.35 on 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

These are my configs:
**/etc/ipsec.conf**
```
version 2.0
config setup
    nat_traversal=yes
    virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12,%v4:!192.168.1.0/24
    oe=off
    protostack=netkey

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
    left=192.168.1.101
    leftprotoport=17/1701
    right=%any
    rightprotoport=17/%any

include /etc/ipsec.d/l2tp-psk.conf

```

**/etc/xl2tpd/xl2tpd.conf**
```
[global]
ipsec saref = yes
listen-addr = 192.168.1.101

[lns default]
ip range = 192.168.2.10-192.168.2.200
local ip = 192.168.2.1
;require chap = yes
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes

```

**/etc/ppp/options.xl2tpd**
```
require-mschap-v2
ms-dns 8.8.8.8
ms-dns 8.8.4.4
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
mru 1280
mtu 1280

```

**/etc/ppp/chap-secrets**
```
# user      server      password            ip
test        l2tpd       testpassword        *

```

**/etc/ipsec.d/l2tp-psk.conf**
```
conn L2TP-PSK-NAT
        rightsubnet=vhost:%priv
        also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
        #
        # Configuration for one user with any type of IPsec/L2TP client
        # including the updated Windows 2000/XP (MS KB Q818043), but
        # excluding the non-updated Windows 2000/XP.
        #
        #
        # Use a Preshared Key. Disable Perfect Forward Secrecy.
        #
        # PreSharedSecret needs to be specified in /etc/ipsec.secrets as
        # YourIPAddress  %any: "sharedsecret"
        authby=secret
        pfs=no
        auto=add
        keyingtries=3
        # we cannot rekey for %any, let client rekey
        rekey=no
        # Set ikelifetime and keylife to same defaults windows has
        ikelifetime=8h
        keylife=1h
        # l2tp-over-ipsec is transport mode
        type=transport
        #
        left=192.168.1.101
        #
        # For updated Windows 2000/XP clients,
        # to support old clients as well, use leftprotoport=17/%any
        leftprotoport=17/1701
        #
        # The remote user.
        #
        right=%any
        # Using the magic port of "0" means "any one single port". This is
        # a work around required for Apple OSX clients that use a randomly
        # high port, but propose "0" instead of their port. If this does
        # not work, use 17/%any instead.
        rightprotoport=17/0

# Normally, KLIPS drops all plaintext traffic from IP's it has a crypted
# connection with. With L2TP clients behind NAT, that's not really what
# you want. The connection below allows both l2tp/ipsec and plaintext
# connections from behind the same NAT router.
# The l2tpd use a leftprotoport, so they are more specific and will be used
# first. Then, packets for the host on different ports and protocols (eg ssh)
# will match this passthrough conn.
conn passthrough-for-non-l2tp
        type=passthrough
        left=192.168.1.101
        leftnexthop=192.168.1.1
        right=0.0.0.0
        rightsubnet=0.0.0.0/0
        auto=route



```

**/etc/ipsec.secrets**
```
192.168.1.101   %any:   PSK     "testing"
```


**~$ sudo ipsec verify**
```
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.35/K2.6.38-8-generic (netkey)
Checking for IPsec support in kernel                            [OK]
 SAref kernel support                                           [N/A]
 NETKEY:  Testing XFRM related proc values                      [OK]
        [OK]
        [OK]
Checking that pluto is running                                  [OK]
 Pluto listening for IKE on udp 500                             [OK]
 Pluto listening for NAT-T on udp 4500                          [OK]
Checking for 'ip' command                                       [OK]
Checking /bin/sh is not /bin/dash                               [WARNING]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]

```

Tailing /var/log/auth.log I can see the below errors...

When I try and connect from a Windows 7 PC with Shrew Soft VPN (IP: 192.168.1.70):
```
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: received Vendor ID payload [XAUTH]
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: ignoring unknown Vendor ID payload [16f6ca16e4a4066d83821a0f0aeaa862]
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] method set to=106
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] method set to=108
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: received Vendor ID payload [RFC 3947] method set to=109
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: received Vendor ID payload [Dead Peer Detection]
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: ignoring unknown Vendor ID payload [f14b94b7bff1fef02773b8c49feded26]
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: ignoring unknown Vendor ID payload [166f932d55eb64d8e4df4fd37e2313f0d0fd8451]
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: ignoring unknown Vendor ID payload [8404adf9cda05760b2ca292e4bff537b]
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: received Vendor ID payload [Cisco-Unity]
Aug 10 19:10:25 OptiPlex-GX270 pluto[23897]: packet from 192.168.1.70:500: initial Aggressive Mode message from 192.168.1.70 but no (wildcard) connection has been configured with policy=PSK+AGGRESSIVE
```
Until negotiation times out.


When I try and connect from an Android phone (IP 192.168.1.103):
```
Aug 10 19:12:20 OptiPlex-GX270 pluto[23897]: | payload malformed after IV
Aug 10 19:12:20 OptiPlex-GX270 pluto[23897]: |   90 14 67 8d  35 be 43 9e  9f 92 73 7e  89 4e 63 13
Aug 10 19:12:20 OptiPlex-GX270 pluto[23897]: |   c2 12 27 4c
Aug 10 19:12:20 OptiPlex-GX270 pluto[23897]: "L2TP-PSK-noNAT"[1] 192.168.1.103 #3: sending notification PAYLOAD_MALFORMED to 192.168.1.103:500
Aug 10 19:12:20 OptiPlex-GX270 pluto[23897]: "L2TP-PSK-noNAT"[1] 192.168.1.103 #3: next payload type of ISAKMP Identification Payload has an unknown value: 111
Aug 10 19:12:20 OptiPlex-GX270 pluto[23897]: "L2TP-PSK-noNAT"[1] 192.168.1.103 #3: probable authentication failure (mismatch of preshared secrets?): malformed payload in packet

```

It appears to be two different problems, but I wouldn't be surprised if they were related.

Thanks in advance for any help or advice you can offer.

Cheers

---

