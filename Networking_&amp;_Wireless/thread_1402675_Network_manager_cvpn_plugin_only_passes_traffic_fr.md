---
title: "Network manager cvpn plugin only passes traffic from network profile was created on"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by MSPdwalt on 2010-02-09
Hey guys, first post on this forum so bare with me please,

Last weekend I migrated from Windows 7 RTM to Ubuntu 9.10 and an xp vm using vmware unity for my windows only apps.  It's been going OK so far, just a couple of issues with the network manager cvpn plugin.

I setup my work's vpn ipsec remote access to a pix 515 and a client's ipsec-ra vpn to an ASA 5510.  Both connected and passed traffic from my home network, but when I take my laptop to work, or to another network, the vpns will connect, but they won't pass traffic.

In my experience this is usually a double nat issue (I know it's not because it's worked from these sites before) or a firewall issue.  Although I am a network guy at heart (mostly cisco) I know nothing about IP tables or how to troubleshoot linux firewalls.

Any help would be greatly appreciated, I use VPNs all the time for work and if I can't get them to work reliably I may have to switch back to windows :(

---

### Post by MSPdwalt on 2010-02-10
Update,

I did some more testing and my cvpn connections only work from my home network, no where else, I've been testing in places that I've used the VPNs before, such as vpning from my office to a client, and from a client site back to my office.
 
I found a way to check IP tables and it looks like I have no rules in place.  This is really confusing, is there something "under the covers" that binds the vpn connection to my network, or maybe my external IP?

Again, any help would be greatly appreciated,

DW

---

### Post by MSPdwalt on 2010-02-19
Hello? Anybody out there?  I understand that this is a very specific question and this may not have been the best place to post it.  Can anyone suggest a place I can go for info/support on the network manager cvpn plugin?

---

### Post by MSPdwalt on 2010-03-06
*bump*

---

### Post by MSPdwalt on 2010-05-10
Solved by updating to 10.0.4 LTS

---

