---
title: "WAN, LAN, two NICs and ip_forwarding"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by jag7720 on 2011-09-07
I have a media server that has two NICs.  eth2 has a static public IP (WAN/Internet) and eth3 has a static (192.168.x.x)IP on a LAN.

My server is also hosting a DHCP server for the LAN.

What I need to do is allow the traffic on the the LAN to access the internet from eth3 to eht2 on the server. routing???  ip_forwarding??

My server also hosts a couple SMB shares and a UPnP server on eth3 that any PC on the LAN can access to but no access to them from the WAN.  I set up Samba and MediaTomb to only answer on eth3.

I don't have a simple hardware router (limited hardware in Afghanistan) so I have to do this on the server.

Can someone tell me how to accomplish this?

Thanks

---

