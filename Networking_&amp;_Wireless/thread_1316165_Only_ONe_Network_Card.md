---
title: "Only ONe Network Card"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by mmoscosa on 2009-11-05
Hello!

Well, I am wondering if I can set a router with only one network card?! 

I am pretty sure there is a way for using only one network card and make it work as if they where two.

Google unfortunately didnt help.

I am using Ebox-Plattaform but it is installed over Ubuntu Server.

Thx

---

### Post by DGortze380 on 2009-11-05
> **mmoscosa said:**
> Hello!

Well, I am wondering if I can set a router with only one network card?! 

I am pretty sure there is a way for using only one network card and make it work as if they where two.

Google unfortunately didnt help.

I am using Ebox-Plattaform but it is installed over Ubuntu Server.

Thx

Maybe? With a virtual NIC?

Why? Just buy a second NIC, they're like $10USD.

---

### Post by falconindy on 2009-11-05
Not possible. The whole idea of a router is to connect two otherwise separated networks and act as a gateway between the two. Virtual NICs are only good for creating networks inside your own PC. If you only have 1 physical NIC, you can only connect to 1 physical network.

---

### Post by DGortze380 on 2009-11-06
> **falconindy said:**
> Not possible. The whole idea of a router is to connect two otherwise separated networks and act as a gateway between the two. Virtual NICs are only good for creating networks inside your own PC. If you only have 1 physical NIC, you can only connect to 1 physical network.

Technically you're correct, but it depends on what he wants to do... he could create a router-on-a-stick kind of scenario ... why he would want to, I have no idea.

---

