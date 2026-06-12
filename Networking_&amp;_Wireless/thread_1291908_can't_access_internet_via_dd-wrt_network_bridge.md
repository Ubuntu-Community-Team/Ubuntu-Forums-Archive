---
title: "can't access internet via dd-wrt network bridge"
date: 2009-10-15
forum: Networking &amp; Wireless
---

### Post by arber6 on 2009-10-15
I have a WRT54GL with dd-wrt installed, acting as an Access Point and it is the DHCP Server. It has an IP of 192.168.1.1 and it has wired and wireless clients.
I also have a WRT54GL with dd-wrt installed, acting as a Client Bridge. It has an IP address of 192.168.1.2 and it has wired clients only, but the connection back to the Access Point is wireless.
I have an XBOX (with XBMC) connected to the Client Bridge, and the XBOX can access the internet and stream files from a SMB share on my Windows XP box (which is connected to the Access Point).
I've just installed 9.04 on a HTPC that is connected to the Client Bridge, and it reports that the connection is OK, and it receives an IP address from the Access Point's DHCP Server (and the Access Point sees the ubuntu box as a client IP), and the ubuntu box knows the default gateway is 192.168.1.1. HOWEVER, the Ubuntu box cannot access the internet, and it cannot ping the AP, and it cannot ping to, or be pinged from the Access Point clients. The ubuntu box can ping the Client Bridge and the client-bridge-connected XBOX, and it can HTTP into the Client Bridge's web management console.
If I connect the ubuntu box by Cat5, to the Access Point, then internet access is perfect (so I don't think this is a NIC issue).
I had thought that the Wireless Bridge would be "invisible" to clients connected to the Client Bridge (indeed it has been to the XBOX), so I'm unsure if this is an ubuntu problem or a dd-wrt issue, or both.
I can't remember if I had the same network topology when I last tried ubuntu (8.10 about 12 months ago), but I don't recall internet access having been an issue.
Are there any settings I need to make in ubuntu, so it'll work over the bridge?

---

