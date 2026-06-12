---
title: "Why port 53 and 5353 neccesary for wireless?"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by friv_livs on 2010-07-02
In my port experimentation, I cannot connect to secured or unsecured  wifi without 53 and 5353 out. What function does port 53 and 5353 out do  in connecting to a wireless  network?

I understand port 53 is FTP and avahi-daemon looks for network connected devices via 5353.

Why is FTP out being required to connect?

Thanks in advance.

---

### Post by capscrew on 2010-07-02
> **friv_livs said:**
> In my port experimentation, I cannot connect to secured or unsecured  wifi without 53 and 5353 out. What function does port 53 and 5353 out do  in connecting to a wireless  network?

I understand port 53 is FTP and avahi-daemon looks for network connected devices via 5353.

Why is FTP out being required to connect?

Thanks in advance.

These ports are for DNS.  Specifically DNS = port 53 -- mDNS = port 5353.

See [**_here _**]("http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers")for a list of TCP/UDP ports.

DNS is needed to resolve the mapping of names to IP addresses/

---

