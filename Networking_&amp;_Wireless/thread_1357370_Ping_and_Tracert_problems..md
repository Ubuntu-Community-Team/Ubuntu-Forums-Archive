---
title: "Ping and Tracert problems."
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by zozza on 2009-12-17
I cannot seem to get ping or tracert working.  

I have moved to a new network and have the same problem in XP so it is the network rather than Ubuntu.

When I run ping I get this:

~$ ping website url.
PING(IP address) 56(84) bytes of data.
^C
--- ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5030ms

And for tracert:

~$ sudo tracert website url
traceroute to website (IP address), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  *^C

Any ideas how I can deal with this.  I have changed the TTL field but get the same results.

Thanks.

---

### Post by dandnsmith on 2009-12-17
The lack of ping response can occur when the site isn't prepared to give one, but the tracert results suggest you have no connectivity.

I'd start with an *ifconfig*, to see what network addresses have been assigned, and a *route print* to see what routing has been set up.

---

### Post by doas777 on 2009-12-17
try to ping [www.google.com](www.google.com) instead. if it works (it should; they respond to wan echos), then the problem is that the site admin has blocked ICMP either inbound or as a response.

---

### Post by DGortze380 on 2009-12-17
> **zozza said:**
> I cannot seem to get ping or tracert working.  

I have moved to a new network and have the same problem in XP so it is the network rather than Ubuntu.

When I run ping I get this:

~$ ping website url.
PING(IP address) 56(84) bytes of data.
^C
--- ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 5030ms

And for tracert:

~$ sudo tracert website url
traceroute to website (IP address), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *
 6  *^C

Any ideas how I can deal with this.  I have changed the TTL field but get the same results.

Thanks.

What network are you on? It appears as though you either don't have connectivity, or ICMP is being blocked.

---

### Post by zozza on 2009-12-18
Thanks for the suggestions.  I cannot ping [www.google.com](www.google.com)

I can use HTTP and send e-mail with POP3 and SMTP so I have connectivity.  

Therefore I assume either inbound or outbound or both ICMP traffic have been blocked.

Thanks again.

---

### Post by Kevbert on 2009-12-18
It may be that your router (if you're using one) is blocking ping requests. Are you behind a proxy server (as used at colleges and universities) ? That may be the problem.

---

