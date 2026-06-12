---
title: "Forward all traffic from eth1 to eth2"
date: 2012-01-23
forum: Networking &amp; Wireless
---

### Post by bonesjones256 on 2012-01-23
trying to monitor network traffic. 
Got a simple setup but having trouble finding the right answer. 

I have currently

Cable modem >>> Firewall

I want

Cable modem >>> ETH1 >>>>ETH2 >>>>>Firewall
Then outbound would be vice versa. 

the point is to build a quick a easy internet traffic monitor.
I'm using eth0 to SSH, eth1 and eth2 shouldn't have an ip address i dont think. 

Can this be done WITHOUT messing with current setup of other devices?

---

### Post by iponeverything on 2012-01-23
just create a transparent bridge.

---

### Post by bonesjones256 on 2012-01-26
Cool i'll see what i can't figure out with that term. thanks.

---

