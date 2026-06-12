---
title: "UDP Packet loss."
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by pintoosingh on 2009-08-11
Hello,

I installed second life client for linux, but I am having big time problems due to packet loss. I am unable to know the reason behind it, cause traceroute packets are being blocked by firewall in our college network. How can I know the reason behind it? :(:(

---

### Post by aesis05401 on 2009-08-11
Hello, 

traceroute uses UDP, right?  Maybe you can talk to the network admins to find out if they can assist you.  You may be encountering a poorly written filter rule.

Edit: I believe traceroute also requires a range of ports open to function, but that may be outdated information...

---

### Post by pintoosingh on 2009-08-12
Yeah traceroute in linux uses udp packets. I want to know is there a way to find out the reason for packet loss?

---

### Post by aesis05401 on 2009-08-12
Discovering the reason for the packet loss without asking the admins is accomplished through inference... and will likely take a lot of time.  You may wish to look at techniques of tunneling through the firewall and running your game session through the tunnel instead of taking the time to reverse engineer the network filtering rules. 

If you choose to reverse the network filtering rules instead, just make sure you understand your school's policy on the matter.  Even if your network admins don't allow any sort of active analysis of their firewalls you can sidestep the issue yet still profile their firewalls by:
- obtaining control of test machines across several network segments of the LAN and attempting to run different types of traffic between them.
- attempting to route out to a controlled WAN side machine instead of the game servers so that you can see exactly how your stream is arriving at the host.
- initiating sessions from LAN to WAN based test boxes from multiple LAN segments using a spectrum of protocols.  Filtering rules may not be applied equally across the LAN, in which case a proxy on a different LAN segment may be all you need.

Anyhow, remember that your actions do not have to be illegal to get you into hot water with your school.  If you have never done anything like this before then I would suggest giving your IT department the benefit of the doubt... If you go down there are ask for some help not just solving your routing issue, but actually understanding the networking concepts you may make some friends in the department.. Once you have a friend on the admin team you will never need to wonder about these types of things again.

---

### Post by jonobr on 2009-08-12
+1 on that.

Just also to add, if that network is loosing UDP packets, then thats an issue IT should be aware of and they should be thanking you for the heads up,
although as he said, its all in the handling of the thing.
SOme people thing you just being nosey

---

