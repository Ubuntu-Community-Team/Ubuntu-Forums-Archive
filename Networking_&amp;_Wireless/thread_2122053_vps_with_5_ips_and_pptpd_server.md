---
title: "vps with 5 ips and pptpd server"
date: 2013-03-03
forum: Networking &amp; Wireless
---

### Post by jcheve on 2013-03-03
Hi,

I want to start a small pptpd server on a vps in the us so I can spoof the ip and get hulu and netflix us version etc.  I have gone and set up the pptpds server works great.

My question is:

Since the vps comes with 5 ips, how can I allocate a specific ip to a pptpd client.  The reason being is say I want to connect to the pptpd server and have a special application running that needs a port forwarded, and say my brother who lives elsewhere wants to use the pptpd server also but is also needing to forward the same port to his pc.  Since we both are under the same ip under my current set up, we can't both have the port forwarded to us simultaneously. Is there is a way to assign an ip to nat directly my pptp client and another available public ip to nat to my brothers pptp client ip which would allow us both simultaneous use of the ports since the connection originates from separate ips yet under the same server?

Is this doable in iptables?.

I know how to forward ports from public ip to the pptp client ip, I just dont know how to set up using the available ips off my vps to go to different client ips on the pptp end.

Thanks!

---

