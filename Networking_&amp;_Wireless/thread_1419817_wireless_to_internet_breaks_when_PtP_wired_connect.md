---
title: "wireless to internet breaks when PtP wired connection established."
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by miatawnt2b on 2010-03-02
I am having an issue with networking, and I'm sure I'm not thinking of something dumb, but wondering if someone can point it out to me.  I use wireless to connect to the internet, and it works flawlessly.

eth1      Link encap:Ethernet  HWaddr 00:26:bb:0a:bc:c4  
          inet addr:10.132.203.139  Bcast:10.132.255.255  Mask:255.255.192.0
          inet6 addr: fe80::226:bbff:fe0a:bcc4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5071 errors:1 dropped:0 overruns:0 frame:37047
          TX packets:5083 errors:20 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3206468 (3.2 MB)  TX bytes:778477 (778.4 KB)
          Interrupt:22 

The problem is that I have this machine and another directly connected with an x-over cable. I used network manager to give eth0 an address of 10.10.10.2 netmask 255.255.255.254.

When I connect the wired connection, I no longer route over wireless.

What am I missing?
Thanks,
-J

---

