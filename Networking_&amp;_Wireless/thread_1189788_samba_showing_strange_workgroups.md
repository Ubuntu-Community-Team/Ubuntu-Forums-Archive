---
title: "samba showing strange workgroups"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by pro003 on 2009-06-17
This is the situation. Ubuntu 9.04 Desktop which is primary PC connected directly through a cable DSL to ISP but uses PPPoE (ppp0) protocol, and the other machine is Windows based which goes on internet by using Ubuntu desktop as gateway. Now, samba works well and there's no bigger problems but there's only one annoying thing about it. Actually, when I click on Network I get my WORKGROUP name and I can access on Windows machine and vice versa. But there ALSO appear to be several other WORKGROUPS (every and each of them with their respective names). Now, how can I exclude those workgroups from my samba shared network?

The only thing I come to think about it is that I need to add dns server ip to windows machine so that it could access internet, without it - it can't.

Any thoughts, ideas are welcomed.

Thanks.

---

### Post by Tom Mann on 2009-06-17
Out of interest what are the workgroup names?

From what I recall Ubuntu machines use the workgroup MSHOME by default, which can be changed to match your workgroup name in /etc/samba/samba.conf (I think that's the right path)

If you need guidance I can help further...

---

### Post by pro003 on 2009-06-17
Of course I've put my workgroup name in /etc/samba/smb.conf, thats not the issue. And whats the real problem is that beside I've put my wrkgrp name in smb.conf I can see other workgroups beside mine, and to be honest I can easily access to one of those unsecured machines if ya know whatta mean...

---

### Post by redmk2 on 2009-06-17
> connected directly through a cable DSL to ISP It sounds like you are connected to a larger LAN, that is managed by your ISP.  You are seeing fellow ISP users workgroups.  Yikes!

I would run a dedicated router/NAT/firewall as the gateway host.  Check out using a small Linksys, D-Link or Netgear product.

---

### Post by puppywhacker on 2009-06-17
you can specify the interfaces (or ip-addresses) that samba is listening to. so make sure samba isn't binding to the internet. Other people will otherwise probably also be abled to connect to your shares.

```
/etc/samba/smb.conf
interfaces = 127.0.0.0/8 eth0

```
This I consider a mistake from the internet provider, they haven't disabled broadcasting over the ip network, which means you will probably see also broadcast traffic on your network which isn't specifically destined for you, notably arp requests from your neighbors

---

### Post by pro003 on 2009-06-17
redmk and puppywhaker you are both right, but am interested more in chip in one dedicated router, the only thing is the cost (money), thats why I tried first to se if there is a solution for this already in ubuntu, but in the end I will buy this router, what else...

thank you both of you, and please more ideas are welcome too.

---

