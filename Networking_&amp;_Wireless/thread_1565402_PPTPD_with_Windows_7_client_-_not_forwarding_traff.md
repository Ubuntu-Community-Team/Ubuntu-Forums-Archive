---
title: "PPTPD with Windows 7 client - not forwarding traffic"
date: 2010-08-31
forum: Networking &amp; Wireless
---

### Post by Davorian on 2010-08-31
Hi all,

I apologise if this question has been asked a million times before.

I have an Ubuntu 9.10 server with the PPTP VPN server daemon installed (pptpd).  I can connect to this server successfully with a Windows 7 64-bit client - the client is assigned an ip address but the netmask is 255.255.255.255 (not sure if this is normal).

I would like all internet traffic requested by the client to go through the server.  Currently, however, whenever I connect to the server I am unable to access anything other than the server itself (requests to everything else time out).  DNS appears to work.  ipconfig on the client shows a default gateway of '0.0.0.0'.

Every tutorial on PPTP that I've read seems to go about it in a completely different fashion, so I'm a bit confused :(  Any insight would be appreciated.

Cheers,
Davorian.

---

