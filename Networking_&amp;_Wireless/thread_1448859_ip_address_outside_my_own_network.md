---
title: "ip address outside my own network"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by Windy Peaks on 2010-04-07
Ladies and Gentlemen of the Forum:

Does anyone know the command to identify my own complete ip address so that I can use a remote desktop from some where else ??

Thank You in advance

Windy

---

### Post by lisati on 2010-04-07
[http://whatismyipaddress.com]("http://whatismyipaddress.com")

---

### Post by Sooner Al on 2010-04-07
You may be better off using a free service like No-IP.com or DynDNS particularly if your behind a router that supports a service like that. That way you call home using a fully qualified domain name [FQDN], ie. like yourPCname.no-ip.com for example, versus needing to always know your public IP address. Remember most ISPs provide dynamic public IPs to residential accounts so it could change.

[http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html](http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html)
[http://www.dyndns.com/services/dns/dyndns/](http://www.dyndns.com/services/dns/dyndns/)

Check your router manual or users guide for help setting this up once you create a free account.

If your router does not support those then you can download and install a free update client on one of your home PCs. The update client contacts the servers on a time scheduled basis. The server then knows your current public IP and maps that to your FQDN. That information is propagated over the public internet so you can access your home LAN via the FQDN.

[http://www.no-ip.com/downloads.php](http://www.no-ip.com/downloads.php)
[http://www.dyndns.com/support/clients/](http://www.dyndns.com/support/clients/)

---

