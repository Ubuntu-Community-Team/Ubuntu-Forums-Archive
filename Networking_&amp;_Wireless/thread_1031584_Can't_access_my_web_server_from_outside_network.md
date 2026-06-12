---
title: "Can't access my web server from outside network"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by htguy on 2009-01-05
I have been trying everything I can find to get access to my apache server through my IP address.  

My network is as follows:
Zoom X5 modem (port 80 has been remapped so it is available for my web server) -> Ubuntu Rounter/Firewall/Web Server -> PC

I can access the apache web server just fine from my PC.  But I can't access my server from outside of my network.  I have port forwarding (forwarding port 80 and 443 to my server) set up in the Zoom modem and have set the following rules (and others) for my server via webmin: 

#ACTION     SOURCE    DEST               PROTO     DEST PORT(S)
Web/ACCEPT  net       $FW
Web/ACCEPT  loc       $FW       

From:
[http://www.shorewall.net/two-interface.htm](http://www.shorewall.net/two-interface.htm)

Please help! :(

---

