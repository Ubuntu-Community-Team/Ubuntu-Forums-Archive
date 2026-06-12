---
title: "netbios over IPX"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by Geroz on 2012-03-06
Hi all,

Anybody know (if is possible) how add linux (ubuntu) machine into local network which work on NetBios over IPX ?

I read that is possible add support IPX/SPX into linux (add IPX support into Linux Kernel). But it is possible use NetBios over IPX ?

Thanks all and sorry for my terrible english.

---

### Post by bab1 on 2012-03-06
> **Geroz said:**
> Hi all,

Anybody know (if is possible) how add linux (ubuntu) machine into local network which work on NetBios over IPX ?

I read that is possible add support IPX/SPX into linux (add IPX support into Linux Kernel). But it is possible use NetBios over IPX ?

Thanks all and sorry for my terrible english.

You should be able to use IPX and its version NETBIOS.  The real question is: Why do you want to do that?  I have never used IPX with Linux.  The last time I used IPX was with Novell inthe late '90s.  

I wonder if you NIC will handle IPX.  Ethernet and IPX are not exactly the same. If you want to try it you need to add the universe repos and install the IPX package.

---

### Post by Geroz on 2012-03-06
> Why do you want to do that? Because we have a local network  which use it. In the local network isn't only normal PC's but there are a specialized HW as telephone exchange.

---

