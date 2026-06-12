---
title: "block remote port and/or telnet it"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by itmozart on 2009-08-31
we're receiving some warnings on our servers (hardy server) using rkhunter.
they are very likely to be apache listening processes that happen to use as remote port the ones that are detected as suspicious.

now, I have to questions:
1. is it possible with some tool (e.g. telnet) to initiate a connection from a client specifying the local port as well (so that I could connect to the server using e.g. 2001), so that I can manually trigger a rkhunter warning on the server?
2. is it possible to setup the server so that a set of given remote ports (e.g. again, 2001) are blocked, without creating problems to the incoming connections?

thanks,
Saverio

---

### Post by shredder12 on 2009-08-31
why don't you use a firewall to block those set of ports for any incoming connection..??

---

### Post by itmozart on 2009-08-31
The server ports are appopriately blocked by iptables; the only two allowed are the usual 80 and 443.

RKHunter is (as far as I understand) checking the local port of the client connections, so that an example that would trigger an RKHunter warning would be

**client local port: 2001 => server port: 80**

If i do:

**telnet myserver.com 80**

the client local port is going to be random. I'd like instead it to be predefined.

Thanks anyway :-)
Saverio

---

### Post by itmozart on 2010-01-19
I guess it's not possible - I'm going to solve the issue adding an automated cross-check against netstat.

---

