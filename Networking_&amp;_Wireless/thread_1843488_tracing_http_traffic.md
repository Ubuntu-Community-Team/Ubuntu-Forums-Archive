---
title: "tracing http traffic"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by alex245 on 2011-09-13
Does anyone know a command line tool to trace http traffic?

---

### Post by haqking on 2011-09-13
> **alex245 said:**
> Does anyone know a command line tool to trace http traffic?

trace ? or youmean monitor ?

To trace a path you use traceroute.

Monitoring would be best with something like Wireshark.

tcpdump, iptraf, netstat

what exaclty do you need to do ?

---

### Post by alex245 on 2011-09-13
> **haqking said:**
> trace ? or youmean monitor ?

To trace a path you use traceroute.

Monitoring would be best with something like Wireshark.

tcpdump, iptraf, netstat

what exaclty do you need to do ?

I need to monitor HTTP traffic between a server and a web server, I'm currently using tcpdump. but I'm looking for a tool that show me the http headers more easily

---

### Post by alex245 on 2011-09-13
> **haqking said:**
> trace ? or youmean monitor ?

To trace a path you use traceroute.

Monitoring would be best with something like Wireshark.

tcpdump, iptraf, netstat

what exaclty do you need to do ?

Found exactly what I was looking for.

[justniffer]("http://justniffer.sourceforge.net/")

It comes as deb package – yeah! ;)

---

### Post by haqking on 2011-09-13
> **alex245 said:**
> Found exactly what I was looking for.

[justniffer]("http://justniffer.sourceforge.net/")

It comes as deb package – yeah! ;)


ahh cool, sorry i didnt get back earlier.

glad you got it sorted.

remember to mark your thread as solved using thread tools.

cheers

---

