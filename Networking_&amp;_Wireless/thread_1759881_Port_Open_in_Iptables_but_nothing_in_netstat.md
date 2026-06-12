---
title: "Port Open in Iptables but nothing in netstat"
date: 2011-05-16
forum: Networking &amp; Wireless
---

### Post by gael.d on 2011-05-16
Hi there, 

i've just got a problem from this morning, i've got no idea where this is came from. 
I need the port 27015 to be open. I've opened it in iptables : 
> iptables -A INPUT -p tcp -i eth0 --dport 27015 -j 

But when i try : 
> netstat -nan
The port 27015 do not appear as "LISTEN". 

Why that ?
Thanks !

---

### Post by SeijiSensei on 2011-05-16
Because there's no program actually listening on the port.

Suppose, for instance, you open port 80 on your firewall.  Will someone then be able to fetch web pages from your server?  No, you'd need to be running web server software like Apache as well.

---

