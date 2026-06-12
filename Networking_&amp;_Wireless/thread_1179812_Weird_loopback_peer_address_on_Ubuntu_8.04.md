---
title: "Weird loopback peer address on Ubuntu 8.04"
date: 2009-06-06
forum: Networking &amp; Wireless
---

### Post by molon labe on 2009-06-06
I am seeing this on two different systems now, both running Hardy:

```
molon@molon-desktop:~$ nc -l -p 1234 -v &
[1] 11387
molon@molon-desktop:~$ listening on [any] 1234 ...

molon@molon-desktop:~$ nc 127.0.0.1 1234
192.168.2.1: inverse host lookup failed: Unknown server error : Connection timed out
connect to [127.0.0.1] from (UNKNOWN) [192.168.2.1] 57748
```192.168.2.1 belongs to one of my other network interfaces, yet it is being reported as the peer on a loopback connection.  On a properly functioning system, the peer name would of course be 127.0.0.1.

This causes all sorts of problems with access controls for local services and reverse DNS lookups, since I don't provide reverse lookups for 192.168.2.x IPs.

netstat looks something like:

```
tcp        0      0 127.0.0.1:1234          192.168.2.1:50146       ESTABLISHED
tcp        0      0 127.0.0.1:50146         127.0.0.1:1234          ESTABLISHED
```Any ideas what would cause this?

---

