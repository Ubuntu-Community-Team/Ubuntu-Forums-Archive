---
title: "Broken Networking after OpenVPN configuration attempt"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by WilcoRogers on 2011-07-13
Hey Guys,

I'm at a bit of a loss. Here's what's up:

I have been trying to set up openVPN on a Virtual Machine running Ubuntu 10.04 with the eventual intention of having a closed VPN in the workspace I'm at, and a bridged internet connection out through the server.

My initial process/instinct was to go through Webmin. After a fair bit of tooling around making keys/certificates, I was able to get a response (and that's all it was, really) from my windows machine accessing the VPN server. However, in my attempt to bridge the network, I have lost all internet/networking capabilities from the server.

Fortunately I am able to access the server directly from the hardware underneath (i.e. I don't need to SSH in or anything), and so I've been attempting to restore the server's networking back to default. I have returned the /etc/network/interfaces file to it's original state (just the loop, and an eth0 on dhcp) and restarted the networking. A check with ifconfig returns what seems to be a working eth0, and the loop (noting else) however I am unable to ping any outside server. When I do, I am given the message:

From XXX.XXX.XXX.XXX icmp_seq=1 Destination Host Unreachable

(where of course XXX is my IP address).

Another VM on the server is able to access the internet just fine, so it's not the overall server hardware...

I guess at this point I'm just trying to take steps back, but if any of you have any suggestions/ideas/questions they would all be very helpful. This is my first time posting for help here, so I hope I've included enough information.

Thanks in advance,

WilcoRogers

**EDIT:** In my haste I never tried to give the VM a reboot. I now have ping access to the outside world. However setting up a VPN is a whole other ballgame. Sorry if I wasted anyone's time.

---

### Post by idlemind324 on 2011-07-13
Edited Out As It Was Resolved

---

