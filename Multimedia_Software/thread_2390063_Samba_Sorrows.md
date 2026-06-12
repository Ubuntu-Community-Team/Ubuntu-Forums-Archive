---
title: "Samba Sorrows"
date: 2018-04-25
forum: Multimedia Software
---

### Post by nightraver on 2018-04-25
So I am currently working on my internal homelab VLAN configurations for both my internal networking and server configurations. At the moment, I am having a bit of an issue trying to get my Samba filesharing server back off its knees after the transfer to my new VLAN segmented network.


In the past, I have been able to get my samba fileshare directories added into my windows PC fairly easy. Map network drive, add the correct directory structure, done. My shared file server even managed to show up under the network section of file explorer. Everything was awesome and (despite a few Windows hiccups) it worked well.


Fast forward to my new, segmented network. I can still ping the server, and connect via telnet to 139 and 445. But when I try to re-map my network drives via the standard map network drive function, I get an error of:


"Windows cannot access \\%IPofServer% Check the spelling of the name. Otherwise there might be a problem with your network."


So as stated before, I can ping the server, and access the standard ports. In addition, while in testing phase, all my VLAN segments have an allow all protocol to any host/source rule as the only firewall rule utilized.


Diag I have tried: Disabling UFW on my samba server, disabling my firewall on the PC which I desire access from, double checking my samba config; everything checks out, more or less. (I can post the config if needed).


Any help would be appreciated here; either paths to take, diag to try, etc.

---

### Post by wyliecoyoteuk on 2018-04-25
SMB is not routable, as it is based on Netbios, which uses broadcasts, so if it is on a separate VLAN, no go, unless you use a VPN link.

EDIT: apparently it is possible via netbios over tcp/ip, using a WINS server (however WINS is no longer developed).
It is limited to port 445.

---

