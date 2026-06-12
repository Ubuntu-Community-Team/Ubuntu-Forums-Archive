---
title: "For those of us in less than liberal countries."
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by CongoJim on 2010-10-29
We have elections coming up next year (hopefully) and our government  hasn't exactly a liberal attitude towards democracy. I would like to know how to proxy my IP to another server just in case certain sites get blocked by the local ISPs. I maintain a domain hosted in the US so I have access to their servers. How do I connect, masking my IP and still receive the potentially blacklisted sites? 

And send to the blacklisted sites I should add.

Ubuntu user since 2004, currently on Lucid, along with a significant percentage of the city where I live. I'm considered the cities premier (only) computer geek. "How do I fix windoz?" "Install Ubuntu."

---

### Post by SeijiSensei on 2010-10-29
If you just have off-shore hosting services, I don't think that will help.  If you can afford it, I'd suggest renting a virtual server in the US from someone like [www.linode.com](www.linode.com).  You could run an OpenVPN tunnel from your local machine to the remote VM and have it proxy your traffic with iptables masquerading.  Maybe you can share the cost with others and use multiple tunnels.  Linode has a huge pipe to the outside so even half-a-dozen VPN users won't see any speed reductions compared to direct connections.  Running tunnels is a very "lightweight" task, too, so you can host a number of them on one VM without much sweat.

---

