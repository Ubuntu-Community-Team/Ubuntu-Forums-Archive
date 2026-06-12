---
title: "Very low LAN speeds"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by effenberg0x0 on 2010-07-21
I have the following setup in my Home Office:

**- Server:** Ubuntu 10.04, fully updated, dual-core CPU, 4GB RAM, 100Mbit NIC. Samba is the file server.
- Router (Linksys WTR54GS 7.2)
- Lan Port 1: Server
- Lan Port 2: Notebook01: Ubuntu 10.04 and Windows 7 (grub)
- Lan Port 3: Notebook02: Ubuntu 10.04 and Windows 7 (grub)
- Lan Port 4: Free

**Other wireless clients:**
- iPhone
- Droid

- Internet download / upload speeds from all wired / wireless clients is coherent (about 14Mbps, I pay for 16Mbps but that's life I guess). 
[B]- [COLOR="DarkRed"]Wired[/COLOR] file transfer from Server to Notebooks reaches _400 KB/s at most_ 
- [COLOR="DarkRed"]Wireless[/COLOR] file transfer from Server to Notebooks reaches _155 KB/s at most_[/B]


As you can see, Wireless transfer is very slow. On the wired side, cabling is new, professionaly done (and redone yesterday to see if it was the problem - it was not). 


1) I have already tried replacing the router for another one (D-Link, TP-Link, etc) with no changes.

2) Booting on Win7 or Ubuntu, on the notebooks, makes no difference. 

3) Therefore, there´s gotta be something with the server setup. 

What kind of information can I provide you about the server networking setup that can help you help me?

Kind regards,
Effenberg

---

### Post by effenberg0x0 on 2010-07-23
Fixed by disabling negotiation and fixing 100baseTx-FD with mii-tool.

Regards,
Effenberg

---

