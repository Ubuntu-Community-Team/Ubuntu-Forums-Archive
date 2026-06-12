---
title: "ssh, ping, traceroute ... terminal problems"
date: 2008-12-11
forum: Networking &amp; Wireless
---

### Post by weboholic on 2008-12-11
Hi,

I know its a very obscure title but I couldn't come up with a better one.

I have a hosting, a regular one, no vServer. When I load my page with the browser - it works. When any other application tries to access the internet - it works.

But with the terminal, I get the following:
```
en@en-desktop:~$ ssh user@weboholic.de
ssh: connect to host weboholic.de port 22: Connection refused
en@en-desktop:~$ ping weboholic.de
PING weboholic.de (213.83.63.50) 56(84) bytes of data.
From 192.168.2.104 icmp_seq=1 Destination Port Unreachable
^CFrom 192.168.2.104 icmp_seq=2 Destination Port Unreachable

--- weboholic.de ping statistics ---
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 5044ms
, pipe 2
en@en-desktop:~$ traceroute weboholic.de
traceroute to weboholic.de (213.83.63.50), 30 hops max, 40 byte packets
 1  192.168.2.104 (192.168.2.104)  0.091 ms  0.040 ms  0.038 ms
en@en-desktop:~$ ping google.com
PING google.com (72.14.205.100) 56(84) bytes of data.
From 192.168.2.104 icmp_seq=1 Destination Port Unreachable
^CFrom 192.168.2.104 icmp_seq=2 Destination Port Unreachable

--- google.com ping statistics ---
2 packets transmitted, 0 received, +2 errors, 100% packet loss, time 5049ms
, pipe 2
en@en-desktop:~$ traceroute google.com
traceroute to google.com (209.85.171.100), 30 hops max, 40 byte packets
 1  192.168.2.104 (192.168.2.104)  0.127 ms  0.044 ms  0.040 ms
en@en-desktop:~$ 
```

It's not even working with google.

Yes, I'm behind a router. Funny thing is - everything worked just fine 5 days ago. And I'm not aware of somebody messing with the router. I've asked my roommates - nobody touched it.

I can't also VPN to my workplace, this was also working fine last week ...

Do you need any more info? What could be the problem?

---

