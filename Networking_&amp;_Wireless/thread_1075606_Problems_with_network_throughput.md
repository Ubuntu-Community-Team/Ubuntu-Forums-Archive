---
title: "Problems with network throughput"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by mikebeecham on 2009-02-20
I wonder if I could get some help with this issue...first some topology:

I have a linux machine, and a windows machine plugged into a 5-port netgear switch.  This, in turn, is plugged into a Devolo HighSpeed 85mbps ethernet plug.  This carries my ethernet through the power supply.

Downstairs, I have another Devolo HiSpeed 85mbps ethernet plug, plugged into the wall socket. Plugged into this is a netgear DG834 v3 router, which feeds a cat5 cable into my mac mini in the sitting room.

Here is my problem...

If I have only the windows machine plugged into the netgear switch, then I can see a network throughput of around 60-75mbps...I'm happy with this.  However, the moment I plug the linux machine into the 5-port switch as well, then the throughput drops to around 10mbps.

I tried to check the network drivers in Linux, by using the command:

sudo lshw -C network

This then brings back a shed load of information.  What is interesting, is that it shows my internet connection on the linux machine as 100mb/s.  

Ok, so I have a couple of questions:


1) Should I not have an internet connection of 100mbps, or is this just a grammar issue?

2) Is there anything in particular that I can look at in terms of resolving the drop in throughput when the linux machine is plugged into the network?

Thanks in advance.




Mike

---

