---
title: "Ubuntu 11.10 refusing all incoming connections"
date: 2012-08-07
forum: Networking &amp; Wireless
---

### Post by james19869 on 2012-08-07
My Ubuntu 11.10 server is refusing all incoming connections from elsewhere on its network. This seemed to occur just after I restarted the network router, but I can't be sure that's what caused it. I have several services running on the server, listening on various ports. I can't connect to any of these, or to SSH, from any other computers on the network. I can, however, connect to them from the server itself.

I've checked the following:

[LIST=1]
[*]I have PeerGuardian installed, but it's not running.
[*]netstat reports that the services in question are listening on the ports they should be listening on.
[*]I've obviously tried to connect with an IP and a hostname. My router does have the Ubuntu server in its DHCP hosts lists, and its IP and MAC address match -- so I'm definitely connecting to the server I think I am.
[*] I can ping the server.
[/LIST]

I'm basically looking for a way to debug this problem. Does anyone have any idea how I could begin?

---

### Post by gorgonzola79 on 2012-08-09
Hi James,

I have the same problem and I cannot figure it out.

I have checked my router aswell, the logs are ok .
I tried to disable the firewall within my router , still the same problem.
I tried to disable iptables temporarily, same problem.

btw I can reached the server from all the local network but not from the outside.

So I checked my apache2 logs and I have just a warning message: 
> [warn] RSA server certificate is a CA certificate (BasicConstraints: CA == TRUE !?)

I use  an openerp appliance on an ubuntu 10.04 with openssl.

any ideas ?

---

### Post by gorgonzola79 on 2012-08-09
I got it !!!!

I wrongly add the gateway ip as as dns server ip.

I found it by switching the eth2 to dhcp mode.
After that i switched back to static typing exactly the same IPs.

---

