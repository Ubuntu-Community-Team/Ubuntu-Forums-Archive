---
title: "dnsmasq listens to itself"
date: 2009-10-14
forum: Networking &amp; Wireless
---

### Post by parsim on 2009-10-14
Every time I boot up, dnsmasq forwards all DNS queries to itself, on 127.0.0.1#53. So if I try to browse the web, Firefox will sit on "Looking up example.com..." until dnsmasq times out.

If I restart dnsmasq, it realizes that it shouldn't be forwarding DNS queries to itself, and works fine. But I need to do this after booting every single day.

Relevant bits from /var/log/daemon.log:
```
Oct 15 09:24:35 eve dnsmasq[2396]: started, version 2.47 cachesize 150
Oct 15 09:24:35 eve dnsmasq[2396]: compile time options: IPv6 GNU-getopt DBus I18N TFTP
Oct 15 09:24:35 eve dnsmasq[2396]: no servers found in /etc/resolv.conf, will retry
Oct 15 09:24:35 eve dnsmasq[2396]: read /etc/hosts - 16 addresses
Oct 15 09:24:41 eve NetworkManager: <info>  starting... 
...
Oct 15 09:24:44 eve dnsmasq[2396]: query[A] ntp.ubuntu.com from 127.0.0.1
Oct 15 09:24:44 eve last message repeated 3 times
...
Oct 15 09:24:46 eve dnsmasq[2396]: query[A] ntp.ubuntu.com from 127.0.0.1
Oct 15 09:24:46 eve last message repeated 3 times
Oct 15 09:24:46 eve ntpd_initres[3083]: host name not found: ntp.ubuntu.com
Oct 15 09:24:46 eve ntpd_initres[3083]: couldn't resolve `ntp.ubuntu.com', giving up on it
...
Oct 15 09:24:49 eve NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) started... 
Oct 15 09:24:49 eve dhclient: bound to 192.168.0.2 -- renewal in 97220 seconds.
Oct 15 09:24:49 eve NetworkManager: <info>    address 192.168.0.2 
Oct 15 09:24:49 eve NetworkManager: <info>    prefix 24 (255.255.255.0) 
Oct 15 09:24:49 eve NetworkManager: <info>    gateway 192.168.0.1 
Oct 15 09:24:49 eve NetworkManager: <info>    nameserver '127.0.0.1' 
Oct 15 09:24:49 eve NetworkManager: <info>    nameserver '61.9.134.49' 
Oct 15 09:24:49 eve NetworkManager: <info>    nameserver '61.9.133.193' 
Oct 15 09:24:49 eve NetworkManager: <info>    nameserver '208.67.222.222' 
Oct 15 09:24:49 eve NetworkManager: <info>    nameserver '208.67.220.220' 
Oct 15 09:24:49 eve NetworkManager: <info>    nameserver '192.168.0.1' 
Oct 15 09:24:49 eve NetworkManager: <info>    domain name 'vic.bigpond.net.au' 
Oct 15 09:24:49 eve NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) scheduled... 
Oct 15 09:24:49 eve NetworkManager: <info>  Activation (wlan1) Stage 4 of 5 (IP Configure Get) complete. 
Oct 15 09:24:49 eve NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP Configure Commit) started... 
Oct 15 09:24:51 eve NetworkManager: <info>  (wlan1): device state change: 7 -> 8 
Oct 15 09:24:51 eve dnsmasq[2396]: reading /etc/resolv.conf
Oct 15 09:24:51 eve dnsmasq[2396]: using nameserver 208.67.220.220#53
Oct 15 09:24:51 eve dnsmasq[2396]: using nameserver 208.67.222.222#53
Oct 15 09:24:51 eve dnsmasq[2396]: using nameserver 61.9.133.193#53
Oct 15 09:24:51 eve dnsmasq[2396]: using nameserver 61.9.134.49#53
Oct 15 09:24:51 eve dnsmasq[2396]: using nameserver 127.0.0.1#53
```
Note the last line above, which does **not** say that dnsmasq is ignoring 127.0.0.1, which [it should](http://lists.thekelleys.org.uk/pipermail/dnsmasq-discuss/2009q1/002789.html).

Continuing...
```
Oct 15 09:24:51 eve NetworkManager: <info>  Policy set 'Auto zephyr' (wlan1) as 
default for routing and DNS. 
Oct 15 09:24:51 eve NetworkManager: <info>  Activation (wlan1) successful, devic
e activated. 
Oct 15 09:24:51 eve NetworkManager: <info>  Activation (wlan1) Stage 5 of 5 (IP 
Configure Commit) complete. 
Oct 15 09:24:53 eve dnsmasq[2396]: reading /etc/resolv.conf
Oct 15 09:24:53 eve dnsmasq[2396]: using nameserver 208.67.220.220#53
Oct 15 09:24:53 eve dnsmasq[2396]: using nameserver 208.67.222.222#53
Oct 15 09:24:53 eve dnsmasq[2396]: using nameserver 61.9.133.193#53
Oct 15 09:24:53 eve dnsmasq[2396]: using nameserver 61.9.134.49#53
Oct 15 09:24:53 eve dnsmasq[2396]: using nameserver 127.0.0.1#53
Oct 15 09:24:56 eve dnsmasq[2396]: query[SOA] local from 127.0.0.1
Oct 15 09:24:56 eve dnsmasq[2396]: forwarded local to 127.0.0.1
Oct 15 09:24:56 eve dnsmasq[2396]: forwarded local to 61.9.134.49
Oct 15 09:24:56 eve dnsmasq[2396]: forwarded local to 61.9.133.193
Oct 15 09:24:56 eve dnsmasq[2396]: forwarded local to 208.67.222.222
Oct 15 09:24:56 eve dnsmasq[2396]: forwarded local to 208.67.220.220
Oct 15 09:24:56 eve dnsmasq[2396]: query[SOA] local from 127.0.0.1
Oct 15 09:24:56 eve dnsmasq[2396]: forwarded local to 127.0.0.1
Oct 15 09:24:56 eve dnsmasq[2396]: forwarded local to 61.9.134.49
Oct 15 09:24:56 eve dnsmasq[2396]: forwarded local to 61.9.133.193
Oct 15 09:24:56 eve dnsmasq[2396]: forwarded local to 208.67.222.222
Oct 15 09:24:56 eve dnsmasq[2396]: forwarded local to 208.67.220.220
... [ repeats about 100 times ] ... 
Oct 15 09:24:57 eve ntpd[2949]: ntpd exiting on signal 15
Oct 15 09:24:57 eve dnsmasq[2396]: query[A] ntp.ubuntu.com from 127.0.0.1
Oct 15 09:24:57 eve dnsmasq[2396]: forwarded ntp.ubuntu.com to 127.0.0.1
Oct 15 09:24:57 eve dnsmasq[2396]: query[A] ntp.ubuntu.com from 127.0.0.1
Oct 15 09:24:57 eve dnsmasq[2396]: forwarded ntp.ubuntu.com to 127.0.0.1
Oct 15 09:24:57 eve dnsmasq[2396]: query[A] ntp.ubuntu.com from 127.0.0.1
... [ repeats about 1,000 times ] ...
Oct 15 09:25:49 eve dnsmasq[2396]: query[A] www.bom.gov.au from 127.0.0.1
Oct 15 09:25:49 eve dnsmasq[2396]: forwarded www.bom.gov.au to 127.0.0.1
Oct 15 09:25:49 eve dnsmasq[2396]: query[A] weather.noaa.gov from 127.0.0.1
Oct 15 09:25:49 eve dnsmasq[2396]: forwarded weather.noaa.gov to 127.0.0.1
Oct 15 09:25:49 eve dnsmasq[2396]: query[A] ntp.ubuntu.com from 127.0.0.1
Oct 15 09:25:49 eve dnsmasq[2396]: forwarded ntp.ubuntu.com to 127.0.0.1
Oct 15 09:25:49 eve dnsmasq[2396]: query[A] imap.gmail.com from 127.0.0.1
Oct 15 09:25:49 eve dnsmasq[2396]: forwarded imap.gmail.com to 127.0.0.1
Oct 15 09:25:49 eve dnsmasq[2396]: query[A] ntp.ubuntu.com from 127.0.0.1
Oct 15 09:25:49 eve dnsmasq[2396]: forwarded ntp.ubuntu.com to 127.0.0.1
```
...etc

But when I get sick of slow DNS queries and do a **/etc/init.d/dnsmasq restart**, dnsmasq realizes it shouldn't forward to 127.0.0.1:
```
Oct 15 09:29:23 eve dnsmasq[2396]: exiting on receipt of SIGTERM
Oct 15 09:29:23 eve dnsmasq[3853]: started, version 2.47 cachesize 150
Oct 15 09:29:23 eve dnsmasq[3853]: compile time options: IPv6 GNU-getopt DBus I18N TFTP
Oct 15 09:29:23 eve dnsmasq[3853]: reading /etc/resolv.conf
Oct 15 09:29:23 eve dnsmasq[3853]: using nameserver 208.67.220.220#53
Oct 15 09:29:23 eve dnsmasq[3853]: using nameserver 208.67.222.222#53
Oct 15 09:29:23 eve dnsmasq[3853]: using nameserver 61.9.133.193#53
Oct 15 09:29:23 eve dnsmasq[3853]: using nameserver 61.9.134.49#53
Oct 15 09:29:23 eve dnsmasq[3853]: ignoring nameserver 127.0.0.1 - local interface
Oct 15 09:29:23 eve dnsmasq[3853]: read /etc/hosts - 16 addresses
Oct 15 09:29:23 eve dnsmasq[3853]: query[A] multiply.com from 127.0.0.1
Oct 15 09:29:23 eve dnsmasq[3853]: forwarded multiply.com to 61.9.134.49
Oct 15 09:29:23 eve dnsmasq[3853]: forwarded multiply.com to 61.9.133.193
Oct 15 09:29:23 eve dnsmasq[3853]: forwarded multiply.com to 208.67.222.222
Oct 15 09:29:23 eve dnsmasq[3853]: forwarded multiply.com to 208.67.220.220
Oct 15 09:29:23 eve dnsmasq[3853]: reply multiply.com is 66.246.179.201
Oct 15 09:29:23 eve dnsmasq[3853]: reply multiply.com is 66.246.179.202
Oct 15 09:29:23 eve dnsmasq[3853]: query[A] [www.newsvine.com](www.newsvine.com) from 127.0.0.1
Oct 15 09:29:23 eve dnsmasq[3853]: forwarded [www.newsvine.com](www.newsvine.com) to 61.9.134.49
Oct 15 09:29:23 eve dnsmasq[3853]: reply [www.newsvine.com](www.newsvine.com) is 207.46.141.138
Oct 15 09:29:23 eve dnsmasq[3853]: query[A] [www.technotizie.it](www.technotizie.it) from 127.0.0.1
Oct 15 09:29:23 eve dnsmasq[3853]: forwarded [www.technotizie.it](www.technotizie.it) to 61.9.134.49
Oct 15 09:29:23 eve dnsmasq[3853]: reply [www.technotizie.it](www.technotizie.it) is 62.149.140.88
```
My /etc/resolv.conf looks like this:
```
# Generated by NetworkManager
domain vic.bigpond.net.au
search vic.bigpond.net.au
nameserver 127.0.0.1
nameserver 61.9.134.49
nameserver 61.9.133.193
# NOTE: the libc resolver may not support more than 3 nameservers.
# The nameservers listed below may not be recognized.
nameserver 208.67.222.222
nameserver 208.67.220.220
```

---

### Post by parsim on 2009-11-10
Reported upstream, apparently fixed in v2.52.

[http://lists.thekelleys.org.uk/pipermail/dnsmasq-discuss/2009q4/003385.html](http://lists.thekelleys.org.uk/pipermail/dnsmasq-discuss/2009q4/003385.html)

---

