---
title: "can't ping hostname in .local domain"
date: 2010-05-14
forum: Networking &amp; Wireless
---

### Post by csp122 on 2010-05-14
sorry if this is already discussed elsewhere, but my searches have proven unfruitful thus far...

ever since upgrading from karmic to lucid, i cannot ping fqdn hosts in .local tlds. nslookup & dig work, but most other utilities fail (ping, traceroute, etc...). i know .local is an invalid tld, but apple seems to have made it a defacto standard on private networks, so i'd imagine somebody else has seen this issue before... is there a simple fix that doesn't require managing hosts file entries on a bunch of systems?

---

### Post by Iowan on 2010-05-14
**avahi** uses the .local suffix. My experience with **avahi** has not been good so far - maybe I just don't understand it...

---

### Post by csp122 on 2010-05-14
seems that most current versions of linux with mdns are forcing the issue of dotlocal domain names are invalid, and really shouldn't be used. in any case, the following change to the 'nsswitch.conf' file remedies the situation:

user@ubuntu:~$ ping -c 1 host.domain.local
ping: unknown host host.domain.local

user@ubuntu:~$ nslookup host.domain.local
Server:        192.168.1.1
Address:    192.168.1.254#53

Name:    host.domain.local
Address: 192.168.1.1

user@ubuntu:~$ grep hosts /etc/nsswitch.conf
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

user@ubuntu:~$ sudo vi /etc/nsswitch.conf

user@ubuntu:~$ grep hosts /etc/nsswitch.conf
hosts:          files dns

user@ubuntu:~$ ping -c 1 host.domain.local
PING host.domain.local (192.168.1.1) 56(84) bytes of data.
64 bytes from host.domain.local (192.168.1.1): icmp_seq=1 ttl=127 time=0.576 ms

--- host.domain.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.576/0.576/0.576/0.000 ms

---

### Post by redmk2 on 2010-05-14
> **csp122 said:**
> seems that most current versions of linux with mdns are forcing the issue of dotlocal domain names are invalid, and really shouldn't be used. in any case, the following change to the 'nsswitch.conf' file remedies the situation:

user@ubuntu:~$ ping -c 1 host.domain.local
ping: unknown host host.domain.local

user@ubuntu:~$ nslookup host.domain.local
Server:        192.168.1.1
Address:    192.168.1.254#53

Name:    host.domain.local
Address: 192.168.1.1

user@ubuntu:~$ grep hosts /etc/nsswitch.conf
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

user@ubuntu:~$ sudo vi /etc/nsswitch.conf

user@ubuntu:~$ grep hosts /etc/nsswitch.conf
hosts:          files dns

user@ubuntu:~$ ping -c 1 host.domain.local
PING host.domain.local (192.168.1.1) 56(84) bytes of data.
64 bytes from host.domain.local (192.168.1.1): icmp_seq=1 ttl=127 time=0.576 ms

--- host.domain.local ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.576/0.576/0.576/0.000 ms

Solved?  It may work for you, but I would not call it a remedy.  You have only disabled mDNS and not addressed (no pun intended) Avahi at all.

Avahi uses the .local domain by default.  It can be configured to use any TLD.  How about .avahi as a TLD for example?   See [**_[COLOR="Indigo"]here [/COLOR]_**]("http://avahi.org/wiki/AvahiAndUnicastDotLocal")for info.  This leaves everything in place.

---

### Post by tallakt on 2012-05-11
Run this on the machine you can't ping

$ sudo apt-get install libnss-mdns

---

