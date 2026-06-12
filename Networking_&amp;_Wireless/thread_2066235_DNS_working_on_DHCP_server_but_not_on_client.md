---
title: "DNS working on DHCP server but not on client"
date: 2012-10-04
forum: Networking &amp; Wireless
---

### Post by sfault on 2012-10-04
Hi! I've successfully setup my DHCP server. Clients can connect and an IP gets assigned and the client is connected to the internet.

I have one problem, though. I can access(ping, telnet, web browser) an IP address but not a hostname from a client connected to the server. I can ping and telnet both IP addresses and hostnames from the server itself, though.

Honestly, I don't know what I'm missing here. I just know that it's a DNS issue. Has anyone had the same problem?

Thanks!

---

### Post by albandy on 2012-10-04
You have to syncronize dhcpd with bind9
Take a look:

[http://www.kootbox.com/images/fbfiles/files/Integrar_BIND_y_DHCP_Server.txt](http://www.kootbox.com/images/fbfiles/files/Integrar_BIND_y_DHCP_Server.txt)

---

### Post by sfault on 2012-10-04
Thanks for the link!

But what if I don't have a fully-qualified domain name? I'm just trying to make some sort of "small data center" work.

Thanks a lot! :)

EDIT: Solved the problem. Thanks a lot! I followed this guide: [http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/](http://ulyssesonline.com/2007/11/07/how-to-setup-a-dns-server-in-ubuntu/)

---

