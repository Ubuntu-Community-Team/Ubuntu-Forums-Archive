---
title: "Ethernet connection between Linux and Windows PCs broken after Breezy&gt;Dapper upgrade"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by OrangeGoblin on 2006-06-27
Before I upgraded to Dapper, I had my Linux PC connected to my Windows XP PC via an Ethernet cable. All I had done was set the Windows XP to be 192.168.10.1, and the Linux to be 192.168.10.2, and enabled the connections, and it worked, but now after the upgrade it doesn't. Both PCs claim to be connected, but nothing is passing between them, they can't even ping. Any ideas? Thanks.

---

### Post by OrangeGoblin on 2006-06-27
On futher inspection it appears that the Linux PC is both sending and receiving packets, but the Windows PC is only sending. I disabled Windows firewall, and the problem still occurs, so I don't think it is that...

---

### Post by OrangeGoblin on 2006-06-27
Turns out [this]("http://www.ubuntuforums.org/showthread.php?t=186430") was the fix I needed.

---

