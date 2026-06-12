---
title: "Connect to UPnP outside LAN"
date: 2012-10-14
forum: Networking &amp; Wireless
---

### Post by acrocephalus on 2012-10-14
Hello,
Viewing a UPnP device within the same LAN is pretty straight forward with Banshee or VLC. However, I would like to know how to connect to a UPnP when I'm outside the LAN. I'd like to listen to my music when I'm at work, at my parent's home, ... I have a Conceptronic CH3HNAS NAS and a Cisco EPC3825 router. Is it possible?
Cheers!

Dani

---

### Post by acrocephalus on 2012-10-16
I should correct my last statment. I can stream music using a DAAP server instead of a UPnP server with Banshee. Now, said this, could anyone explain how to connect to a DAAP server outside my LAN?
Cheers!

Dani

---

### Post by acrocephalus on 2012-10-16
I've been trying to figure out how to do this and I've found something. The default DAAP port is 3689, so I forwarded this port on my router. However, when I check if it is forwarded with [http://www.whatsmyip.org/port-scanner/]("http://www.whatsmyip.org/port-scanner/") it says that the port is blocked. What's interesting is that when I check port 22 it also says it is blocked, but I know it is not as I have an SSH set up and running (no program using SSH when I check for open ports). The same happens with port 21, even if I know it is forwarded and open. Could anyone help? This is really important for me, so it'd be great to solve it!
Cheers!

Dani

---

