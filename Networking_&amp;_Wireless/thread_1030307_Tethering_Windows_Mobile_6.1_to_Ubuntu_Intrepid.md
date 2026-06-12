---
title: "Tethering Windows Mobile 6.1 to Ubuntu Intrepid"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by Neon Lemmy Koopa on 2009-01-04
Hi.

I'm having trouble connecting my Ubuntu Intrepid laptop to the internet through my Windows Mobile 6.1 phone (HP iPAQ 910c) via USB.  I've read countless reviews and things saying that 8.10 USB tethering works straight out the box but it doesn't seem to be working for me.

I connect my phone via USB and start Internet Sharing, and Ubuntu will see it.  I know this because the Network Manager will connect to it and list it as "auto rndis0".  But when I go to open a web browser, it wont load the page.  

When I run ifconfig from a terminal, this the output for rndis0 (aka my phone):
```
rndis0    Link encap:Ethernet  HWaddr 80:00:60:0f:e8:00  
          inet addr:169.254.2.2  Bcast:169.254.2.255  Mask:255.255.255.0
          inet6 addr: fe80::8200:60ff:fe0f:e800/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:9 dropped:0 overruns:0 frame:0
          TX packets:75 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1324 (1.3 KB)  TX bytes:14134 (14.1 KB)

```It gives me an IP and all, but I notice that "errors:9" under RX packets, and I wonder if that is contributing to it.  If I have not posted enough information, please tell me what more to post.

I would appreciate any help possible.  I kinda depend on my phone to put me on the net cause my Pop barred me from the home network for running the bandwidth WAY over the limit.

EDIT:  Ok, I know the connection doesn't work at all.  I try to ping google, but I came out with this:
```
$ ping www.google.com
ping: unknown host www.google.com

```
Someone help me?

---

### Post by Forlornity on 2009-03-06
There are a few of these threads about, so I suspect there's a real issue here, with no-one offering a solution that I've found.
I'm poking around to see if I can find a solution, if I do I'll post it here:
[http://ubuntuforums.org/showthread.php?t=1032366]("http://ubuntuforums.org/showthread.php?t=1032366")

 - Forlornity

---

