---
title: "PC stops responding on wireless interface"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by didix1 on 2011-11-22
Hi, everybody! This is my first posting here, hope you can help cuz this is driving me crazy :)
So, here's the situation: I have a N-wireless network set up in my office. There are my laptop running 11.10 64, my desktop also running 11.10 64 and a TP-Link wireless ip cam. The desktop has a mysql server installed which is necessary for the POS software my office is using. OK, here's the actual problem - when freshly booted up the desktop accepts all kinds of connections - mysql, ssh, can be pinged, etc. But after a random period of time it just stops responding on any network calls while still being able to reach the internet, have skype going on, etc. The only way to make it reachable again is to either reconnect it to the router or restart it. It showed the same behavior running 10.10. I have no issues with the laptop or the cam. They are working fine all the time. I've noticed that if I connect from my laptop to the desktop with the POS application while it's on everything is OK and when I disconnect it the PC stops responding right after.
The wifi signal is pretty strong, no package loss. All the devices are with static IPs - 10.1.1.x/255.255.255.224.
Anyone have an idea what's going on?

---

### Post by dandnsmith on 2011-11-22
You appear to have 2 installations with the same OS software releases, and static IP addresses. This rules out IP address leasing problems, I think, so puts the possible cause in a difference on the network hardware on the 2 PCs.
You could try googling for problems with the hardware network interface model on the desktop machine.
The comparison with 10.10 is interesting, but it would be better to have known whether the situation with the desktop was the same for 10.04LTS, as some significant changes happened after that.

---

### Post by didix1 on 2011-11-22
Thank you for the reply :)
Interesting you mention IP leasing since I forgot to write about a problem I think it's somehow relevant to the above situation. My router's DHCP server is now configured to give away addresses from 10.1.1.11 on because when it was configured to start at 10.1.1.2 (10.1.1.1 is the router itself) sometimes would lease 10.1.1.5 (which is the desktop) to a new device in the network, whether laptop or a smart phone. And then the new device (usually a windows laptop) would complain about address collision. It's like the router didn't know the desktop was in the network and at the same time would provide internet to it. Since this problem hadn't ocured ever with any other device I'm starting to think it's some strange defect of the wi-fi card of the desktop and I'll try asap with a new one.

---

### Post by dandnsmith on 2011-11-22
That router oddity over allocating IP addresses doesn't surprise me - it probably doesn't keep records of what devices are using static addresses (unless you've configured it to associate MACs with particular IP addresses).

Myself, I keep the ranges separated, just as you indicate.

Good luck with your hunt.

---

### Post by nigel@lucidata.com on 2011-11-22
I think our problems might be related. I did (I thought) make a post under the title "Can't locate the damage to network system" but cannot seem to find it.

10.10 running sweetly on Acer Aspire One D255 for many months. Somewhere along the line, I suspect an update, the WiFi no longer functions directly. The symptom is that it receives packets, you can watch the count go up, but does not respond specifically to ARP requests. It has obtained an IP by dhcp Ok and appears to have a good physical connection but will not function until a wired ethernet connection is plugged in briefly and then unplugged. All is then fine. Any ideas?

---

### Post by nigel@lucidata.com on 2011-11-28
Just to put on record the solution and to close the thread. 
The Routing table had become disordered so that the cable entry appeared  first. So if the WiFi came up first, which is the usual case, it would  try and use the first entry which was non-functioning. If the UTP  connection was briefly brought up and dropped the routing table was  correctly filled in and everything was OK from then on.
I think the problem might have occurred when struggling with the GUI of  Network Manager which, while not wanting to be too critical, is a bit  clunky and does not let (me at any rate ) one fill in all the fields,  listed for a static IP address. Thanks for those showing an interest in my problem. Nigel.

---

