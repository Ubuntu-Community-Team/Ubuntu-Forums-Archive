---
title: "Horribly slow Internet (DNS Problem?)"
date: 2010-02-15
forum: Networking &amp; Wireless
---

### Post by louieaw on 2010-02-15
I'm not completely new to Ubuntu or Linux, but I know my way around.

I've been running Ubuntu 9.10 Desktop for about a month or two now. I had some initial internet connection problems, but ironed those out. 

Yesterday, I started having a problem that popped up when I first started running Karmic. In Google Chrome, pages would take MINUTES to load, and they would always seem to be stuck on "Resolving Host". The same problem with Firefox, except stuck on "Looking up ___" 

Originally, when this problem started occurring a month ago, I switched to the Google OpenDNS Servers, and that seemed to solve the problem. 

My Ipv6 is off. DNS Servers: 8.8.8.8 and 8.8.4.4. [COLOR=Red]Those are the servers listed in /etc/resolv.conf AND my connection information. [/COLOR]

I've been searching both the forums and Google to find whatever, but nothing seems to change this problem. I would appreciate any help.
I have already modified these with no luck:
- /etc/resolv.conf
- /etc/dhcp3/dhclient.conf
- /etc/nsswitch.conf

Nothing seems to change this problem. I feel as though I'm on a dial up connection, and I really don't want to go back to Windows Vista...

Any help would be GREATLY appreciated. Thank you!

---

### Post by ant2ne on 2010-02-15
8.8.8.8 is interesting```
ant2ne@lenobuntu:~$ nslookup 8.8.8.8
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
8.8.8.8.in-addr.arpa	name = google-public-dns-a.google.com.

Authoritative answers can be found from:
8.8.8.in-addr.arpa	nameserver = ns3.google.com.
8.8.8.in-addr.arpa	nameserver = ns4.google.com.
8.8.8.in-addr.arpa	nameserver = ns1.google.com.
8.8.8.in-addr.arpa	nameserver = ns2.google.com.
ns1.google.com	internet address = 216.239.32.10
ns2.google.com	internet address = 216.239.34.10
ns3.google.com	internet address = 216.239.36.10
ns4.google.com	internet address = 216.239.38.10

```I'd never thought of using googles dns servers. (or am I reading that wrong) Try using the DNS server supplied by your local ISP?

---

### Post by arvevans on 2010-02-15
Check for packet loss by continuous pinging of some remote site (DNS works for me) and then CRTL-C to stop the ping and look to see how many packets were lost.  There should be zero packet loss.

---

### Post by tgalati4 on 2010-02-15
Has it been slow since this weekend?

There's some kind of international thing going on in North America.

---

