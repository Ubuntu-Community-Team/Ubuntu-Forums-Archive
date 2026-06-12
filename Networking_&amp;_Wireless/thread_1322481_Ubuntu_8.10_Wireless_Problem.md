---
title: "Ubuntu 8.10 Wireless Problem"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by bf109 on 2009-11-11
I have a laptop running Ubuntu 8.10 and for some reason it is unable to connect to shares on my internal network using wireless G, unable to open the router config webpage or ping the gateway there as well or ping any of my pc's in the internal network yet it can route through the router gateway and out to the Internet just fine via NAT. When I connect it to my internal network via ethernet to my switch it can do it all. Can anyone tell me where to begin troubleshooting this issue? I am quite a newb with Linux. Also, I have another laptop that is running XP that has a wireless G adapter that can do whatever I ask of it so I wonder if there is a configuration that I might have accidentally messed up on the Ubuntu laptop that is causing this?

---

### Post by Iowan on 2009-11-11
Check */etc/resolv.conf* - both ways.  I have a link at home regarding wrong nameservers - I'll try to check it tonight. I'm probably off-base, but it kinda seems like it may be using external DNS which knows nothing about your local network.

FWIW: [This]("http://ubuntuforums.org/showthread.php?t=971064") is the thread. (It's for Kubuntu)

---

### Post by bf109 on 2009-11-11
Thank you for your reply. Actually I am using UNC to try and access shares on my network in the \\192.168.xxx.xxx\share format so there is no name resolution occuring. And also remember from my post that ping is not functioning either and I am getting "destination unreachable" packet lossage (I'm sorry, I believe I failed to mention that in my first post). I will paste in my /etc/resolv.conf file later today.

---

### Post by Iowan on 2009-11-11
"Destination unreachable" sounds like a routing problem. Does **route -n** show a line for the local network?

---

### Post by bf109 on 2009-11-11
> **Iowan said:**
> "Destination unreachable" sounds like a routing problem. Does **route -n** show a line for the local network?

Yes it does for both network interfaces:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0    0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1    0.0.0.0         UG    0      0        0 wlan0
0.0.0.0         192.168.1.1    0.0.0.0         UG    100    0        0 eth0

---

### Post by Iowan on 2009-11-12
I don't deal with routing enough to know if the metrics will sort things out - or if having doubles for eth0 and wlan0 is responsible for the trouble.

---

### Post by bf109 on 2009-11-13
> **Iowan said:**
> I don't deal with routing enough to know if the metrics will sort things out - or if having doubles for eth0 and wlan0 is responsible for the trouble.

Yeah, I'm not to versed in that either but if I recall correctly the lower the number the higher the priority given to that interface. I would think that if one of the interfaces is not available the OS would just pick the one that is available but I guess I could try changing the metric values and see if there is a change. Thanks for the suggestions.

---

