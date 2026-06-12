---
title: "Route all traffic for Vuze over VPN"
date: 2010-02-02
forum: Networking &amp; Wireless
---

### Post by mynci on 2010-02-02
Hi,

I have only recently started playing with Ubuntu and am enjoying many aspects of it, but i do keep running into the 'limit of my knowledge/understanding' problem and then no amount of googling seems to help.

I suspect it will be easiest if I explain what it is I am trying to achieve then, no doubt, an expert will be able to explain what it is I have failed to understand!

Essentially i have Ubuntu 9.10 running (as well as on a laptop) as a file server and general work horse. I would love to be able to get Vuze (or any other torrent application) to be forced to use a VPN connection and only a VPN connection to get onto the internet. 

At the moment I have my router (draytek vigour 2820) set to block all PPTP traffic, however it does not block some (i suspect encrypted) torrent traffic meaning that some direct connections get back to my machine on my real IP.

I have set vuze to use only PPP0[0] in the appropriate setting box, but i have found it transferring away without a VPN.

Hence what i want to achieve is:
Full access to the local network.
Only access to the internet through the VPN, ideally just for Vuze, but I am happy for all non-local traffic to be routed over the VPN.

If it would change or make this easier i can dedicate a separate Ethernet port to this, although a single port solution would be preferable.

If I have overlooked some important information then please let me know and I will do my best to supply it.

oh, i have tried (and mostly succeeded) in following this guide:
[http://forums.fedoraforum.org/showthread.php?t=229337](http://forums.fedoraforum.org/showthread.php?t=229337)

However I could not get the routing to set correctly when bringing the connection up and down and the method of connection seemed much less reliable than network manager.

As a slight aside, if it were possible to keep the VPN active at all times (ie if it drops out to redial) then that would also be great (i have tried to implement the script linked below to do this, but i am not sure that it works yet)
[http://ubuntuforums.org/archive/index.php/t-1316314.html](http://ubuntuforums.org/archive/index.php/t-1316314.html)

Very many thanks
Mynci.

---

### Post by Mwbrouwer on 2010-05-23
Connect to your VPN service (Ipredator, AceVPN, etc).

Make sure Vuze User Proficiency is set to "Advanced".

Under "connections", select "Advanced Network Settings".

Change your max global connections to 150.

Under "Bind to local interface" enter the interface name of your VPN connection, listed below the entry box. i.e. ppp0

Checkbox "enforce IP bindings even when interface is not available."

Select transport encryption. The only checkbox that should be selected is "Require transport encryption". If you allow unencrypted connections, Ipredator will boot you occassionally.

Have fun!:guitar:

---

