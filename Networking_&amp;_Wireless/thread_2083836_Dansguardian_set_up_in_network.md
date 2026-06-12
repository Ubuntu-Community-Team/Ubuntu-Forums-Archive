---
title: "Dansguardian set up in network"
date: 2012-11-13
forum: Networking &amp; Wireless
---

### Post by jwsicomputing on 2012-11-13
HI there,

Please can someone help me set up dansguardian for use with my home network.
My set up is a modem router connected to a ubuntu box with 2 ethernet cards (this acts as a dhcp machine) all other computers are then connected off this. I need to install dansguardian on ubuntu and make it effective for all the machines on the network.

I tried fiddling around with dansguardian and a few proxy programs, but it didnt work except on the local machine (ubuntu box).
Step by step instructions would be great.
My network is on the 10.42.0.0 range and the ubuntu box ip address is 10.42.0.1

Thanks.

---

### Post by anotherlinuxnewbie on 2013-01-07
> **jwsicomputing said:**
> 
I tried fiddling around with dansguardian and a few proxy programs, but it didnt work except on the local machine (ubuntu box).


I'm in the same boat, server machine goes thru dansguardian, but client machines just get "The proxy server is refusing connections"

---

### Post by furything on 2013-01-15
Firstly I recommend following this
[https://help.ubuntu.com/community/DansGuardian](https://help.ubuntu.com/community/DansGuardian)

In your squid.conf you need to ensure that you set your local lan to 10.42.0.0/24
you should find examples in there that state 192.168.0.0 and 172.x.x.x etc
There is plenty on info for setting up squid just try google or go here
[http://wiki.squid-cache.org/ConfigExamples](http://wiki.squid-cache.org/ConfigExamples)

If you are still having issues then repost and I will upload my squid.conf and dansguardian.conf as I have the save dhcp address (10.42.0.1) setup

I also have my iptables saved and auto restore on reboot to get this all working but for me my config is eth1 to internet and eth0 shared to lan as 10.42.0.1. SO you need to confirm which card connects to internet and there friendly names so I can tell you which bits need swapping.

---

