---
title: "Problem with speed on PPTPD"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by MynameisQuo on 2010-06-29
Hey! I use Ubuntu Server 9.10 on my home server. Yesterday I have installed PPTP and PPTPD. But speed on my home computer, where I use connection to my server is so slow.

This is my PPTP and PPTPD configs:

*PPTP*

**/etc/ppp/peers/vpn**

```
unit 999
maxfail 0
lcp-echo-interval 60
lcp-echo-failure 4
defaultroute
pty "pptp vpn.onet --nolaunchpppd"
name sypa
remotename PPTP
+chap
file /etc/ppp/options.pptp
ipparam vpn
```

**/etc/ppp/options.pptp**

```
lock
noauth
refuse-eap
nobsdcomp
nodeflate
persist
defaultroute
replacedefaultroute
```

*PPTPD*

**/etc/ppp/pptpd-options**

```
name pptpd
refuse-pap
refuse-chap
require-mschap
require-mschap-v2
require-mppe-128
ms-dns 193.33.48.33
ms-dns 193.33.49.160
proxyarp
nodefaultroute
lock
nobsdcomp
#IPX (todo)
ipx
ipx-network 4
ipx-node 1:0
ipx-routing 2
ipx-router-name Linux_router
ipxcp-accept-remote
```

**/etc/pptpd.conf**

```
option /etc/ppp/pptpd-options
logwtmp
localip 172.20.0.1
remoteip 172.20.0.2-254
```

Firewall .sh file:

```
#!/bin/sh
echo 1 > /proc/sys/net/ipv4/ip_forward
echo 1 > /proc/sys/net/ipv4/ip_dynaddr
iptables --flush
iptables --delete-chain
iptables --table nat --flush
iptables --table nat --delete-chain
iptables -P FORWARD ACCEPT
modprobe iptable_nat
modprobe ip_conntrack_ftp
modprobe ip_nat_ftp
iptables --table nat --append POSTROUTING --out-interface ppp999 -j MASQUERADE
echo vpn firewall loaded OK.
```

Excuse for my written speech, I only learn English :)

Please help to resolve my problem. Thanks for your attention!

---

