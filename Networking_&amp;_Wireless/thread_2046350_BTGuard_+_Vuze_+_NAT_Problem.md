---
title: "BTGuard + Vuze + NAT Problem"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by mmtaylor on 2012-08-22
Hokay, so...

I have Vuze installed with BTGuard on my Mac and it works. I remember having trouble setting it up a few months ago, but have no idea what I did to fix it.

Now I'm trying to set up Vuze with BTGuard on Ubuntu 12.04. Have been playing with this for a week now, and not getting anywhere. 

Basically, my download speeds are almost nonexistent, and the smiley faces are always yellow. The NAT / Firewall test always says connection refused, no matter what port number I type in.

I have messed around with some port forwarding stuff on my router, and tried using iptables in command line to open up ports, but it doesn't seem to be affecting anything.

I have no idea what to do next. Please help?!

---

### Post by mmtaylor on 2012-08-25
No one has any suggestions? :(

---

### Post by havock07 on 2012-09-13
Not sure will this help, but have are the ports being randomized? Try to deselect that option and go with a port of your choice, something above 49000 etc. Any trying opening that port manually thru your router and also add that same port in ufw exception rule if you use that. I'm pretty new as well, but I had a similar prob. and I tried this and it worked. Deluge is the one I used. Now I was looking to try BTGuard, wondering how it performs in Linux. Please post about that sometime, if you get it to work as you wish.

---

