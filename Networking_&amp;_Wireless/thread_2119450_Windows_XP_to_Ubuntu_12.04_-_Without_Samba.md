---
title: "Windows XP to Ubuntu 12.04 - Without Samba"
date: 2013-02-23
forum: Networking &amp; Wireless
---

### Post by sjandrew on 2013-02-23
Hello there,

I'm trying to network a machine running XP to one running Ubuntu, for the purpose of sharing files. I've done some searching and see a lot of stuff about Samba, but installing new software is a pain in the ass, and I should think that running FTP between two machines doesn't require Samba. 

I've got a switch and two straight-through cables, and I'm not quite sure why I'm not seeing the other machine on the network. Obviously I've configured both to use private IP addresses (192.168.0.1 and 192.168.0.2, mask /24), instead of looking for non-existent DHCP servers.

So, what am I missing? The above solution should work, right? I should at least be filling my ARP tables on either side, right?

Thanks a bunch,
Steve

---

### Post by ahallubuntu on 2013-02-23
~

---

### Post by sjandrew on 2013-02-23
I'm pretty limited in hard disk space on the Ubuntu side, which is why I'd like to transfer files around. As to the router thing, I'm a poor college student, in a small town, and snowed in.

But apparently my solution actually was working - fun fact: Windows XP does not, by default, respond to ICMP echo requests. You have to explicitly allow that in the Windows Firewall

Thanks anyway

---

