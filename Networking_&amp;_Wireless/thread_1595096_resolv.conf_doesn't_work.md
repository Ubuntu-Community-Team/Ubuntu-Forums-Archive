---
title: "resolv.conf doesn't work?"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by pgy on 2010-10-12
My network works before but now it has follow issue, when I ping google.com, I got
> ping: unknown host google.combut my network still works partially because I can still connect to a DNS listed in my /etc/resolv.conf to get host google.com's ip adress by
> host -t a google.com ip.of.one.dns
and then I ping the returned IP result 66.249.89.104, the ping works fine.

the issue is that I can't connect to Internet, what I can remember is that I ever removed /etc/resolv.conf and this file was created again by network-manager, and I already verified the two dns IPs listed in the resolv.conf are both correct and works fine with command host.

I tried to reboot my machine but it can't help resolve the issue.

Can someone tell me what's wrong with my network?

---

### Post by dineshs on 2010-10-13
If you are using Network manager try this
Right-click on the NM icon(on top right of the panel) then click  Edit Connections. 
Select the tab, wired 
select the ethernet connection  and click edit
select ipv4 
method-Automatic DHCP addresse only
DNS [COLOR="Blue"]4.2.2.1,8.8.8.8[/COLOR]
then click apply
Note:You can use your DNS values

---

### Post by pgy on 2010-10-13
The DNS is not bad actaully as you can see I can get IP with host, but not with ping.

---

