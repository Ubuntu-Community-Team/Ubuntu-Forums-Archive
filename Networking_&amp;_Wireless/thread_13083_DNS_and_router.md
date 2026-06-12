---
title: "DNS and router"
date: 2005-01-28
forum: Networking &amp; Wireless
---

### Post by bob k on 2005-01-28
I want to change DNS servers. I have Ubuntu setup as a DHCP client connected to the router. I also have the router Zyxel P334 setup as DHCP. I have the option to specify the DNS servers as user defined instead of supplied by system (by system I would take it to mean the DHCP defined DNS from ISP).

The question I have is if I change the DNS servers in the router will Ubuntu use the router values, or do I have to change a conf file in Ubuntu.

TIA
Bob

---

### Post by az on 2005-01-28
/etc/resolv.conf gets rewritten every time you connect with dhcp.

---

### Post by bob k on 2005-01-28
[QUOTE=azz]/etc/resolv.conf gets rewritten every time you connect with dhcp.[/QUOTE]

Great! Just so I have this right, with my client setup as a DHCP client would make my router the DHCP server and supply the DNS servers that I have configured in my router, and the gateway supplied by the ISP.

And thats how it works on my router. Changed DNS servers on the lan side of my router rebooted router and rebooted linux, and etc/resolv.conf was updated with new DNS settings.

Works great, I was on Comcast's crappy DNS server and changed to a faster DNS, here in Dallas we have Version regional, and Sprint's international gateway DNS. Round trip to DNS is < 25ms. you'd think I was on a LAN the pages are so fast.

---

### Post by paultje3181 on 2005-01-29
I know this bug is there, but is there a way to solve it? It's really annoying, because my VoIP-telephone gets kicked off as well. So noone can call me, due to this bug.

---

### Post by bob k on 2005-01-29
[QUOTE=paultje3181]I know this bug is there, but is there a way to solve it? It's really annoying, because my VoIP-telephone gets kicked off as well. So noone can call me, due to this bug.[/QUOTE]

I think you posted to the wrong thread, but thats ok I run VOIP off of my router too. If you need any help let me know.

Bob

---

### Post by paultje3181 on 2005-01-30
Yes, this is the right post, as well as the howto, but my resolv.conf is still being changed after every reboot. And my VOIP-telephone responds to this by not getting an IP-adress...

---

### Post by William Hamby on 2005-03-21
[QUOTE=bob k]Round trip to DNS is < 25ms. you'd think I was on a LAN the pages are so fast.[/QUOTE]

you are on a lan

---

