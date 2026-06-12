---
title: "Port forwarding local network"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by bendt.v.rasmussen on 2012-06-23
I have a static ip-address from my isp.
This points to the ip of the router in my house.
I have my rooter port forwarding this to my apache server.

This works like a charm, when I access my web server from the outside world, but whenever I try to access it from another device on my lan, I get the configuration page for my router.

I also use this server as an ssh-, pop3, imap-, ect-server, so I would like to access this at all times.

What to do?

---

### Post by papibe on 2012-06-24
Hi bendt.v.rasmussen.

My first guess is that your are trying to access your server from your LAN using either its public IP, or its full name ([FQDN]("http://en.wikipedia.org/wiki/Fully_qualified_domain_name")).

That functionality is called NAT loopback (read about it [here]("http://opensimulator.org/wiki/NAT_Loopback_Routers")). Most consumer routers don't support it.

When inside your LAN, use the short server name (if your router provide DNS), or the server LAN IP.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by bendt.v.rasmussen on 2012-06-24
Ouside my Lan, I can access [www.myserver.com](www.myserver.com) from a browser and ssh into myserver.com as well as do telnet pop3.myserver.com. My router forwards all of this to my Ubuntu server at 198.168.1.10.

Inside my LAN all calls to *.myserver.com are directed to my router, and I either get an error or the router setup page in my browser.

---

### Post by papibe on 2012-06-24
Try accessing your server using its LAN IP: 198.168.1.10 while inside your LAN.

Regards.

---

### Post by bendt.v.rasmussen on 2012-06-24
I have no problems accessing my server by ip. I want to access my server by its name, so that for instance my mail/dns/telnet clients will work with the same settings both inside and outside my network.

---

### Post by papibe on 2012-06-24
Take a second look at the NAT loopback link I included on post #2.

If you really want to do it, you only need to enable that functionality in your router, or get one that supports it.

Regards.

---

