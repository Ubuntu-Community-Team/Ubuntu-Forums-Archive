---
title: "Karmic server - Problems with avahi daemon"
date: 2010-01-14
forum: Networking &amp; Wireless
---

### Post by BlackBird28 on 2010-01-14
Hi folks,
first of all I want to say thank you at all the community for the precious help that this board gives to all newbies like me!
 
I've another problem that needs to be solved but I couldn't be able to find any fix: 
 
My network layout is this:
 
WAN --- DSL Modem --- (eth1) Server (eth0) --- Wi-fi Router --- Clients
 
 

My server runs as internet gateway, DHCP and DNS server, file server, media server. I need to set file sharing on three different protocols:[LIST=1]
[*]FTP for file transfers on the external side of network (proftpd)
[*]AFP for file transfers to my MacBook (netatalk)
[*]SMB for file transfers to my Win7 pc and my girlfriend laptop.
[/LIST]No problems with the protocols configuration but the only way to have the avahi daemon service discovered on the network is to set the eth1 interface with static IP address...which means that I'm unable to connect to the internet.
I've already tried setting the daemon to ignore the eth1 (by setting it in /etc/avahi/avahi-daemon.conf) interface with no changes.
 
Any ideas?
 
Thank you and sorry for my poor english...

---

