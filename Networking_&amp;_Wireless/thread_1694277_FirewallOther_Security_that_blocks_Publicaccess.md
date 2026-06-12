---
title: "Firewall/Other Security that blocks Publicaccess"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by iTimOSX on 2011-02-24
Hi Guys,

I Installed a game server on my ubuntu desktop which is on port 7777.
I can join the gameserver without any problems on my local network but when I'm trying to join using my external IP address its not working.
This is what I did:
[LIST]
[*]I Forwarded my port inside my router but it still didn't work.
[*]I Removed UFW from my ubuntu machine
[*]I Tried portforwarding with an other machine (iMac) and it's working there
[/LIST]

Is there any Security on Ubuntu Desktop that's blocking my gameserver

EDIT: I Got 2 Network cards in my Ubuntu PC 
1. Is A Ethernet card that I use to connect my iMac to the Ubuntu PC (Internet Sharing on my iMac) For fast file transfers.
2. Is A WLAN card that I use to connect my Ubuntu PC to our network.

Thanks
Tim,

---

### Post by iTimOSX on 2011-02-24
I Found the solution but it's not nice at all.
If I disconnect my wired ethernet the gameserver works but when I connect my wired ethernet again it won't work!

---

