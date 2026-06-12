---
title: "ipv6 disabled; dns query is still AAAA"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by surfer on 2012-06-07
i disabled ipv6 on my machine: it has no ipv6 address. but still the dns queries ([FONT="Courier New"]$ hostname -f[/FONT] or [FONT="Courier New"]$ sudo[/FONT]) are issued as AAAA queries.

how can i prevent that from happening and sending out A queries only? i tried to tamper a bit with [FONT="Courier New"]/etc/gai.conf[/FONT] but to no avail so far.

any ideas? ...this is on ubuntu 12.04.

---

### Post by Doug S on 2012-06-07
How did you disbale ipv6? I found that I had to disable it right at the grub level, or somehow some ipv6 stuff remained (I can not recall the exact details anymore). I have this line in my /etc/default/grub file:```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"
```If you edit the grub file remember to then execute```
sudo update-grub
```

---

### Post by surfer on 2012-06-12
thanks for your reply. but as i said: my ipv6 is disabled. and still applications (such as firefox e.g.) can decide to send out AAAA DNS queries.

---

### Post by lemming465 on 2012-06-19
What kind of DNS queries one sends out (A, AAAA, NS, PTR, SOA, TXT, ...) is pretty much independent of which network transport is carrying them to an upstream recursive server (IPv4, IPv6).  It's completely legitimate to ask AAAA questions over v4 transports. I quite understand your desire not to request  AAAA responses that will be unusable in the absence of any IPv6 routing.  Unfortunately, this is pretty much controlled by the client app, not generically by the OS, so it's hard to completely abolish.

For the specific case of firefox, in about:config set **network.dns.disableIPv6** to *true*.

Adjusting /etc/gai.conf isn't likely to affect A versus AAAA DNS query behavior by applications, sorry.  I think you can cause IPv4 destination addresses to be preferred to IPv6 (sorted earlier in the combined getaddrinfo(3) output list) by boosting the precedence of global scope V4 mapped addresses ::ffff:0:0/96 above global scope v6 ::0, e.g. replace
```
precedence ::ffff:0:0/96  10
```
with ```
precedence ::ffff:0:0/96  45
```
per RFC 3484 section 6 rule 6.  You don't need to adjust the label value; leave that alone.

---

