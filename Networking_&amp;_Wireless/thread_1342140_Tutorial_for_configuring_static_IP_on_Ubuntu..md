---
title: "Tutorial for configuring static IP on Ubuntu."
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by EAIVision on 2009-11-30
Hello,

I have obtained static ips from AT&T my ISP. I am trying to configure that to my server with Ubuntu9.2 but I am not successful in accessing the server from external(public) network. Could someone please suggest any tutorial ?

Thanks,
Raj

---

### Post by Iowan on 2009-11-30
Post */etc/network/interfaces* and results of **ifconfig -a **.
Is the machine connected directly to internet - or does it go through a router, modem, firewall, etc.? It's possible that the machine is set up properly, but is insulated from internet.

---

### Post by doas777 on 2009-11-30
this has a nice example of an /etc/network/interfaces file.
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

and what version of ubuntu did you say that was?

---

