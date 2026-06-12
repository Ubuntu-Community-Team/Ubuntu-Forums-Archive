---
title: "Odd wired network problem this morning"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by ratcheer on 2010-11-03
I have been running several versions of Ubuntu for almost two years and never had anything like this happen, before. I was using the internet last night, with no problems. But this morning, I could not surf. The ethernet icon at the top right indicated I was connected. The green ethernet lights were on at both the computer and the ethernet switch. Querying the router from a Windows PC on the network showed my Ubuntu connection as Active.

So, I rebooted. Everything remained the same, except now the Ubuntu network icon showed it to be disconnected. Still green connection lights on all the hardware and the router still showed it to be Active.

I finally got it to connect to the LAN by going into the Network tools applet and editing the IPv4 settings of the Auto eth0 device, changing them from DHCP to "DHCP addresses only". I then reversed the edit and still had the LAN connection. However, I still could not access the internet.

So, I rebooted again and everything finally went back to normal.

What happened? There were no apparent network hardware problems and all the Windows PC's (2) were fine. My Ubuntu PC lost its connection and it was fairly difficult and non-intuitive to get it back.

Tim

---

