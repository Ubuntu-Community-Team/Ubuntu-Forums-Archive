---
title: "No Network connection (wired)"
date: 2010-12-26
forum: Networking &amp; Wireless
---

### Post by thras on 2010-12-26
I'm fairly new to Linux so I'm not too sure how to proceed with this.  My Linux machine can't connect to the internet.  I'm running Ubuntu 10.04, I also have a Vista partition on this computer. I've googled around and looked at a few things I've seen, my ifconfig output looks like this:
eth0    Link encap:Ethernet    HWaddr   1c:6f:65:21:6c:e1
          iet6 addr: fe80::1e6f:65ff:fe21:6ce1/64  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0  errors:0  dropped:0  overruns:0  frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0x2000
if anyone wants me to type out the lo line of this I can.
I've tried switching my IPv6 settings from 'ignore' to 'automatic' and it still behaves the same.  Not sure how/why that seems to be an ipv6 address in there.
Also I've checked to make sure it isn't just the cable by using the cable from my windows only machine (the one I'm typing on now) and it still behaves the same.
Any help would be greatly appreciated.

---

### Post by thras on 2010-12-26
Well it somehow worked out.  I was going to try to run the try-before-you-install version of 10.10 thinking maybe just reinstall/upgrade would be the easiest fix.  The computer seemed to freeze when in restarted with the 10.10 disc in so I turned off the tower and it booted up on 10.04 with the network connection working.  I had tried restarting the computer a dozen times before.  I have no idea what this fault is, it happened one other time like this.  About 3 weeks ago I lost internet on that computer for like 2 days then suddenly it started working again.  I have no idea what I did wrong or what I might have done right.

---

### Post by grahammechanical on 2010-12-27
For the record, ifconfig shows that eth0 is UP and RUNNING. So, the system is recognizing the wireless adapter and it is switched on but you do not have an inet addr (Internet address) which should be the address of the router/modem.

Run ifconfig again when you have an Internet connection and you will see the difference. It is as if you are not connected to the router. Try running some commands when everything is working and save the output, then you can use these results to work out what is missing when you have a problem.

regards.

Regards.

---

