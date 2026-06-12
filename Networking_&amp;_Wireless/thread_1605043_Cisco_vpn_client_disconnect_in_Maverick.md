---
title: "Cisco vpn client disconnect in Maverick"
date: 2010-10-24
forum: Networking &amp; Wireless
---

### Post by jcaplette on 2010-10-24
Hi guys,

I've installed Maverick on my work laptop.  I need a VPN connection to acces my job network.

I installed the Cisco vpnclient 4.8.02 0030 and I also tried vpnc, with both client I can connect to my job network but, with both I got disconnected sort of, the connection still active but I loose acces to my session and internet,  after less than a minute.  I also loose all my internet connection, i can't browse web and loose pidgin.. I used to have Cisco VPN client 4.8.01 on my old install of Ubuntu 8.10, which work perfectly without disconnect vpn or loosing internet.

I also tried a WinXP virtual machine that I build to use on my laptop and installed the Cisco vpn for Windows, I can stay connected for hours without any problems...

Anyone have a clue on to set it up on Ubuntu 10.10?

Thanks
Jonathan

---

### Post by tmazzotta on 2010-11-10
In the dialog that you use to configure your VPN parameters, make sure that you check "Disable Dead Peer Detection" under the "Optional" section. Before I checked this box, I would be able to bring up the tunnel, but I would always loose the connection after about a minute. (running vpc 0.5.3r449-2 on Maverick)

---

