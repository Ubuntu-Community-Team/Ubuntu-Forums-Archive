---
title: "dhcpd + pdnsd"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by ilna on 2010-09-19
On PC with WiFi Access Point (hostapd) I'm runing pdnsd with such config (fragment):

```
global {
    perm_cache=2048;
    run_as="pdnsd";
    server_ip = any;
    interface = any;
    query_method=udp_tcp;
    neg_domain_pol=on;
    ...
}

... servers...

rr {
    name=localhost;
    reverse=on;
    a=127.0.0.1;
    owner=localhost;
    soa=localhost,root.localhost,42,86400,900,86400,86400;
} 
```

dhcpd.conf contains this fragment:

```
option domain-name-servers 208.67.222.222, 208.67.220.220;
#option domain-name-servers 10.8.0.1;
 
``` where, apparently, 10.8.0.1 is in routers list.
All does work as expected. But if replace name servers to "10.8.0.1" (comment/uncomment above lines), resolving doesn't work. I have tried with such netfilter records:
```
$IPTABLES -A FORWARD -p tcp -m tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmt
$IPTABLES -t nat -A POSTROUTING -s 10.8.0.0/24 -j MASQUERADE
# $IPTABLES -A INPUT -d 10.8.0.1 -j ACCEPT
 
``` - with and without commented out line.

**Where to dig in?**

---

