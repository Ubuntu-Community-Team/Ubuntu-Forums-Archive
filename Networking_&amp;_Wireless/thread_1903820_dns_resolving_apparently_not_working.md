---
title: "dns resolving apparently not working"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by N-t-F on 2012-01-03
Hello,

I've just installed Xubuntu 11.10 on a new PC without any issue, then I have configured the network, but dns resolution apparently doesn't work. Here's what I did:

1) Uninstalled network-manager to prevent it from putting its nose into the manual configuration:
```
apt-get remove network-manager network-manager-pptp
```

2) edited /etc/network/interfaces to get:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.31.150
netmask 255.255.255.0
gateway cerbere
```

This seems to work so far because I can at this point ping both my file server and my gateway.

3) Edited /etc/environment to add:
```
http_proxy="http://{my.proxy.address}:8080/"
ftp_proxy="ftp://{my.proxy.address}:8080/"
https_proxy="https://{my.proxy.address}:8080/"
```

4) Edited /etc/resolv.conf to get:
```
nameserver 1.2.3.4 5.6.7.8
```
(with actual triple checked DNS IPs, obviously ;) )

Then, when I try to access Internet, I get an error message explaining the name of my proxy is unknown. Similarly, when trying to use:
```
apt-get update
```
it fails, saying that something unexpected happened while trying to find my proxy because no address was associated with it. Looks like a DNS issue to me (or a proxy one, but other computers on the same network do access Internet and repository).

I guess it may be a simple problem, but I just don't see it right now, so I would be grateful for any hint you could have. By the way, it's the configuration I've been using with (Gnome)Ubuntu 10.04. for more than a year now, so I wonder if something just changed between versions regarding basic network configuration. :confused:

Thank you. :)

(And happy new year! ):P )

---

### Post by sj1410 on 2012-01-03
> Edited /etc/resolv.conf to get:
Code:
nameserver 1.2.3.4 5.6.7.8

it should be

nameserver 1.2.3.4
nameserver 5.6.7.8

---

### Post by N-t-F on 2012-01-04
Thank you for answering.

I thought both syntax gave the same result. But I've edited out my file as you suggest, with no change, unfortunately.

---

### Post by sj1410 on 2012-01-04
looks like name resolution issue. try using ip address instead of proxy server name. to check if the name resolution is working properly try the dig command

```
dig www.google.com
```

---

### Post by N-t-F on 2012-01-04
Okay, this actually helped. The answer to the command said the name server could not be reached, so it was really a networking problem, not just a DNS one. The most obvious reason I could imagine was that I couldn't get out of my own network, so I tried to tweak my /etc/network/interfaces file a bit. What finally worked was to replace:
```
gateway cerbere
```
with
```
gateway 192.168.31.5
```

This looks a bit weird for two reasons:
1) pinging cerbere works (ie: the system can translate it to an IP address, taking it from /etc/hosts)
2) "gateway cerbere" in /etc/network/interfaces works just fine with my 10.04 systems (using the same /etc/hosts).

Anyway, it now appears to work.

Thank you again. :)

---

