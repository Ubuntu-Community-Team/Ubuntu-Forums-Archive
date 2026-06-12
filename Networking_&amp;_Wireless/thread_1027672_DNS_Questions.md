---
title: "DNS Questions"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by OneMixDJ on 2009-01-01
Greetings from a certified newbie...

I've been working on my Ubuntu server for DNS that I'm setting up for my internal "domains" and I have a few questions.

1. Is having my own ".com" domain a requirement?

My Ubuntu server has a dual NIC for internal and DMZ networks.
I only want my DNS server to resolve two internal domains and let the DNS servers from my ISP handle all the external stuff (.com, .net, etc...).


Basically, my internal domain suffixes would be:

.homenet - for my internal network (172.26.75.0/24)
.dmz - for my internal dmz (192.168.26.0/24)


2. In /etc/bind/named.conf.local, am I only limited to one zone or can I set up a zone for each internal domain? Since they are both to be independent from each other, would both zone types be set to "master"?

3. Since these domains are internal only, do I still need to configure the DNS servers from my ISP as the forwarders since they are only for my internal networks?

Sorry for all the questions all at once, but I'm trying to get this right.

Thanks in advance!

---

### Post by Mintux on 2009-01-01
I can't answer all of your questions, just some. You would probably be better off asking in a BIND or other DNS oriented forum, than here in the network troubleshooting forum for Ubuntu users.

1. You do not have to register a domain in order to set up a local DNS
2. The local DNS must forward to an internet DNS, or those machines on your network who use the local DNS won't be able to resolve internet names (which means they won't be able to surf the 'net).

---

### Post by OneMixDJ on 2009-01-01
> **Mintux said:**
> I can't answer all of your questions, just some. You would probably be better off asking in a BIND or other DNS oriented forum, than here in the network troubleshooting forum for Ubuntu users.

1. You do not have to register a domain in order to set up a local DNS
2. The local DNS must forward to an internet DNS, or those machines on your network who use the local DNS won't be able to resolve internet names (which means they won't be able to surf the 'net).
Thanks Mintux!

What you provided does clear the fog some.

I'll try a BIND related area as you suggested.

Thanks again!

---

### Post by Iowan on 2009-01-01
I haven't set it up yet, but **dnsmasq** is reported to be a caching DNS server that can link DHCP addresses to machine names.

---

