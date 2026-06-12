---
title: "Unable to connect to port"
date: 2011-03-22
forum: Networking &amp; Wireless
---

### Post by mnorgate on 2011-03-22
Hi,

I have setup an OpenVPN server on my server box, it had been working perfectly until today. It operates on port 1194 which I am now unable to connect to (tried telnet). I have checked all the firewall rules and they still allow the port and I have also checked to ensure that OpenVPN is still listening to the port, which it's not but I have tried restarting the service and the box which dosent make any difference. The only thing that has changed is that yesterday I installed Openfire, could this have broken something? 

Really need help all responses greatly appreciated

Regards

---

### Post by sedawk on 2011-03-22
Have you tried to use the server itself for some local
"localhost" testing, e.g. telnet localhost 1194.
(telnet is okay for ASCII protocols, but i'm not sure
 that debugging openvpn works with telnet).

Check what is the difference between using a real
client (a second pc) and running the client software
on the server itself (so doing to openvpn connection
to itself).

---

