---
title: "very specific NAT problem"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by vladk2k on 2011-08-17
Hello there

I have a box which I use as internet gateway and I need a very specific NAT rule which I can't seem to be able to grasp.

There is a very restrictive filter at my workplace which only allows outgoing packets on port 80 and pretty much nothing else (yep, not even FTP). I want packets from source X (my work IP) to port 80 on my box to be handled by the SSH server.
I've tried the following command:
```
iptables --table nat -I VSERVER -s X/32 -p tcp -j DNAT --dport 80 --to-destination 192.168.1.1:22
```
and also
```
iptables --table nat -I VSERVER -s X/32 -p tcp -j DNAT --dport 80 --to-destination 127.0.0.1:22
```

None of them seem to work. It works if I use any other port except port 80 (so if I put 11111 it works). It doesn't work if I remove the source address or if I forward it to another port...

What else can I do?

---

### Post by vladk2k on 2011-08-18
I wanted to add that I don't have the raw table in which to add trace rules, just so you know that I've tried that

---

