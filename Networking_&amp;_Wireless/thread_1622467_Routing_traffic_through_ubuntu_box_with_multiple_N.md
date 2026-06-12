---
title: "Routing traffic through ubuntu box with multiple NIC's - Trouble with NIC config"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by RoganTheBogan on 2010-11-15
Hi there,

Fresh install of Ubuntu 10.04 LTS desktop version on a box with two NIC's and one onboard as well.

I'm attempting to route traffic from my switch through this machine and then to the modem, essentially this is a monitoring box which I'll put nTop or something similar on.

Network Manager didn't appear to be installed, although when I attempted to install it, it said it already was. I've tried starting this from Alt+F2 and command line with no success.

I've installed WICD as well, but this didn't support multiple interfaces and wasn't very nice either.

I'm assuming I should simply settle for command line and editing of the interfaces file?
If so, I'm not entirely sure how to get this working, as I've made a few attempts with no success.

Ideal outcome:
Card A (Connected to router) has IP 192.168.1.252, on netmask 255.255.255.0 to gateway 192.168.1.254.
Card B (Connected to switch) has IP 10.0.1.254, and netmask 255.255.252.0... No gateway is needed?

Traffic should come in card B and go out card A. There is already routes set up on the router for traffic to return to this box, when looking for 10.0.0.0 IP's.

What am I doing wrong, what should be in my interface file and what more should can I provide if you need any info?


Previously I had this as a Windows Server box, which as much as I don't want to return to I may have to as I've spent far too long on this.

Pre-emptive thank you!

R

---

### Post by RoganTheBogan on 2010-11-15
Update:

I've managed to get past most of my networking issues.

I now have one card set up, connecting to the router, which can ping the router and talk to the outside world fine, it's IP is 192.168.1.197

I have the card that my hub/switch goes into, which is IP 10.0.1.195
Computers connected to the hub can ping this, but they cannot ping to the outside world, or even ping to the other card in the box.

The issue hear is IP fowarding.
I've enabled this in /proc/sys/net/ipv4/ip_forward already.

I'm not too sure what the issue is.

---

### Post by RoganTheBogan on 2010-11-22
Resolved now. No fix to share with the community, as I'm not entirely sure what I did, sorry.

This topic can be closed now :)

---

### Post by Iowan on 2010-11-22
Glad you got it to work. Did you end up configuring interfaces in */etc/network/interfaces*?

---

