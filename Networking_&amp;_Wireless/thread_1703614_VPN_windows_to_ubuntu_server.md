---
title: "VPN windows to ubuntu server"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by nhtraven on 2011-03-09
Hello All
 
I am a complete newbie when it comes to ubuntu. I have a windows SBS 2003 server to which i have my guys VPN into. I have just put up the Ubuntu Server 10. I want this to be a file repository viewable thru local network and the VPN connection they make to windows server. Within my network i can see and log onto the Ubuntu server, but when i VPN into my windows server from outside the network, then try either a mapped drive, shortcut or the IP address it give me the following error:
 
Windows cannot find "196.1.1.1/Mysambasharedfolder"
 
Is there a way to do this? ANy and all help would be greatly appreciated!
 
Nhtraven

---

### Post by koszta on 2011-03-09
well in computer networks the good thing is stick to iso/osi troubleshooting paradigm:
that means -> go from layer one (physical) up, not the other way... That windows thing tells you absolutely nothing. It tells you something has gone wrong. Any time in the future you start fixing something in computer networks approach it form iso/osi view... 

Anyway... you probably want to start with ip layer (since you say you can connect from your network therefore layers 2 and lower are ok). That means try pinging the machine first...

If that works, it is probably a firewall/samba settings issue. Most likely samba tho... 

Let me know how it goes... 

PS Samba is insecure crap to be honest. I know sometimes you have to use it. But if I may suggest I advice using project Dokan for connecting Linux filesystems to windows... It uses ssh by default which is fast and yet secure. It would be great especially since your guys will be connecting to Linux fileserver from a single windows machine. 
[http://dokan-dev.net/en/2010/07/07/dokan-library-053-released/](http://dokan-dev.net/en/2010/07/07/dokan-library-053-released/)
[http://code.google.com/p/dokan/](http://code.google.com/p/dokan/)

---

