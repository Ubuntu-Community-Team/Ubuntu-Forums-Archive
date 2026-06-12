---
title: "resolv.conf -- domain search"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by trspencer on 2010-03-10
On my work machine I'm running Karmic as a guest OS inside VirtualBox with a Windows 7 host. I work remotely and an connected to our network via VPN.

On the Windows side I have our 4 work domains added to the DNS Suffix box in the VPN connection properties. I've also added those same 4 domains to resolv.conf as well, so whether I'm on the host or the guest I can access resources by machine name. Works great.

ex:
search my.workdomain.com
nameserver 10.1.x.x
nameserver 10.1.x.x
nameserver 8.8.8.8

But because the guest uses DHCP that 'search' line I'm adding to resolv.conf gets overwritten every time I bounce the box. Is there any way to set it up so every time that file is written those 4 entries are added? Or do I have to manually edit the file every time I boot the box?

---

### Post by doas777 on 2010-03-10
you can enter them into network-manager itself, so that theoretically it would regen the file correctly. give it a try.

---

### Post by trspencer on 2010-03-10
You are correct sir...worked perfectly. Never noticed the 'dhcp - address only' option, that gives me exactly what I need (dymanic address with static dns/suffix) . Thanks for your help.

---

