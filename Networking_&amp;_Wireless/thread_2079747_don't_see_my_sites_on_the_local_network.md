---
title: "don't see my sites on the local network"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by Maiti on 2012-11-02
Good evening. Actually the problem in the subject. I have ubuntu server is behind a router, the world's seen in a local network router sites too visible, but in LAN provider can not see them. In iptables, is not configured, tried but did not work. The router is configured correctly, as can be seen in the world's. The server has two interfaces eth0 and lo (lo is not used at all). In resolv.conf set ip router. Over ngnix installed apache2 port is 8080. With 80 ports to 8080 throws ngnix.

thanks

p.s. Sorry for my English

---

### Post by jonnyboysmithy on 2012-11-02
I know that if you have a server on a lan you can't connect to it using the external ip. You have to use the internal ip (I was told). I don't know why but thats the way it is. Maybe thats what you're doing wrong?

---

### Post by Maiti on 2012-11-03
> **jonnyboysmithy said:**
> I know that if you have a server on a lan you can't connect to it using the external ip. You have to use the internal ip (I was told). I don't know why but thats the way it is. Maybe thats what you're doing wrong?

thanks its helped

---

