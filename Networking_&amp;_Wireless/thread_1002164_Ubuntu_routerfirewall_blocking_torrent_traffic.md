---
title: "Ubuntu router/firewall blocking torrent traffic?"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by GekoIQ on 2008-12-04
Hello, my first post here as I've been able to search for all my other questions without having to post thumbs up to you guys. Here's my problem:

I have a Ubuntu box at home I use as a nat router/firewall, media server, vpn server, etc. It's kinda my experimental box to learn on. I have guidedog and guarddog installed on the router as iptables GUIs. My problem is that on my XP computer on the LAN I am unable to use uTorrent, I have the proper port (59249 in this case) forwarded to my pc in guidedog and the port opened for LAN computers in guarddog. In uTorrent I can test the port and it is open. I also have the 'bittorent client and peer' ports opened in guarddog for LAN computers. 

If I disable the firewall in guarddog, uTorrent immediately starts to download properly (though it still says no incoming connections... *scratches head*) So I am led to believe that this is a firewall issue. My question is how do I properly configure my firewall for such duties and specifically to allow torrent traffic to specific LAN PCs.

Cable Modem --> Ubuntu box (eth0 = internet, eth1 = LAN 192.168.10.1) --> HP Switch (192.168.10.10) --> LAN PC's (192.168.10.2-9)

---

