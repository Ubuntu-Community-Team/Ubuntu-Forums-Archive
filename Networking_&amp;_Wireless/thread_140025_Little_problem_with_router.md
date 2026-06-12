---
title: "Little problem with router"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by ruimoura on 2006-03-05
Hi.

Ie recently instaled Ubuntu 5.10 on my laptop and i'm having a little problem with networking.
I have a cable modem, wich conects with a router. That router is in dhcp mode, so every ine of us in the house (3 persons) get ip ny dhcp. When i'm on windows everything works fine, but on Ubuntu (and any othet distro, like knoppix) i cant get networking to the outside (i can connect to router interface, but not to outside).
I solved this by adding manualy the dns servers from my isp to the network confiiguration (tryed to configure network by dhcp and manualy and both get the same problem).
That way i get internet normaly, but there's something strange going on.  On windows pages open realy fast (2Mbits line), like 2 or 3 seconds, depending on day time and the page itself. 
On Ubuntu i allways have to wait about 8 to 10 seconds so the pages start to open. If i try to download a file from internet it gets the full speed (about 246 Kpbs) but it gets ages to open pages. I tryed Firefox, Opera and Konqueror and it's no use. Even when connecting with Kopete to msn service takes about 30 seconds, and getting mail with Evolution it's the same, about 20 seconds until it conncets to mail server.

Please does anyone has a clue about whats going on ?
I tryed to connect the cable modem directly to the laptop (without the router) and everything works fine ...

Ps: sorry about my english ... it's not my native language :|

Thanks in advance.

---

### Post by m.musashi on 2006-03-05
I had a very similar problem a while ago. For me it was a DNS problem. I added the DNS IPs from my ISP and that solved the problem. Since you did that and are still having the problem there might be more going on. Try using an IP address instead of a domain name (72.14.203.99 instead of [www.google.com](www.google.com) - at least that is the IP from where I live - you might want to find out the IP for your region). You can also use ping:
```
ping www.google.com
ping 72.14.203.99
```
Different speeds would tend to confirm a DNS problem. The contents of etc/resolv.conf and maybe /etc/network/interfaces would be helpful. Might be some other places to look but that should get us started. Maybe someone else can add to this.

---

### Post by ruimoura on 2006-03-05
Thank you so much for your help, but i allready found the problem.

May be useful to others.

Seems like my router doesn't like IPv6. 
So i did like in the sticky post on the main page of Networking :

sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a 

Disables IPV6 and now network runs at full speed.

Thank you so much again for the answer.

---

### Post by m.musashi on 2006-03-05
No problem. Just trying to give back a little. Glad you solved the problem. I forgot that I also had to disable the IPv6 stuff.

---

