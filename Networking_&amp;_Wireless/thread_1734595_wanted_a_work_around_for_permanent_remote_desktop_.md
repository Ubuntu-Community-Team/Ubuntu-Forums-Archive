---
title: "wanted: a work around for permanent remote desktop access to a server with 3-NICs"
date: 2011-04-20
forum: Networking &amp; Wireless
---

### Post by tokunbo on 2011-04-20
hello guys,

kindly, I have a question and I seek some advise on how best to go about it.

I have a server with 3-NICs, each having static IPs. Only 1-of the three has a default GW address which allows me to access the server over the internet. The other two are just for local uses.

I want to access this server remotely, and using either VNC or the remote desktop feature that ships with Ubuntu. From the infos Ive gathered, VNC is dependent on Ubuntu's remote desktop app, as in it has to be enabled for VNC to work.

While trying to setup remote desktop for the Ubuntu server, system >> preferences >> remote desktop: **checking the connectivity of this machine**: Ive observed that it detects my IPs at random, especially for my case where I have 3-NICs. For example, it sometimes picks the IP of the first NIC when I lauch it. 20-minutes later, if I re-lauch it again, it picks the 2nd IP; and much more later on, the 3rd one. If I reboot the server, it would pick one of the three.

Therefore, I cant access the server remotely(over the internet) cause I would always need it to detect the NIC with the default GW address; and this is not guaranteed with remote desktop in Ubuntu.

**Question:** is there a way I  could configure my machine to bind 1-NIC/IP address(the one with the default GW address allowing access over the internet) to this Remote desktop feature in Ubuntu so that I can always access it remotely.

p.s: note. The RDP feature works but if I reboot the server, it picks one of the other 2-IPs, thus I cant login remotely until something happens that the server now detects the accessbile IP address.

Ive tried un-installing network manager(I thought it was the cause), and configuring my IPs from scratch, but the same observation persists.

Ive also tried using TeamViewer but it doesnt start except a user logs in locally.

---

