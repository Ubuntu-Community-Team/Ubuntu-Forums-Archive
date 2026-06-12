---
title: "Lookup weirness"
date: 2013-01-03
forum: Networking &amp; Wireless
---

### Post by kshatriyak on 2013-01-03
Hey,

Just installed 12.10. I have a dhcp server and a local bind server that dynamically updates it's records on this host. So far, so good, for example, a record from a client that gots is ip from dhcp and created a hostname:

$ host 192.168.100.24
24.100.168.192.in-addr.arpa domain name pointer laptop.myzone.local.

$ host laptop.myzone.local 
laptop.myzone.local has address 192.168.100.24

$ nslookup 192.168.100.24
Server:		127.0.0.1
Address:	127.0.0.1#53

24.100.168.192.in-addr.arpa	name = laptop.myzone.local.

resolv.conf has:

nameserver 127.0.0.1
search myzone.local

So I guess reverse lookup is working, however, when I ssh to my host, I see:

reverse mapping checking getaddrinfo for laptop.myzone.local [192.168.100.24] failed - POSSIBLE BREAK-IN ATTEMPT!

Also, when I log in and type "who" I see :

kshatriyak  pts/1        2013-01-03 23:37 (192.168.100.24)

So, the IP instead of the reverse lookup.

I also have another host in my network, that uses this DNS server. When I log in to this host, I see DNS records correctly resolved.

Anybody has a clue where to look ? I don't want to use "UseDNS no" in my sshdconfig ...

Thanks!

---

