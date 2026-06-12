---
title: "port forwarding rule"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by manfredell on 2010-03-12
I appreciate any help:

we have a Ubuntu VM running CrashplanPro.

We need to redirect all inbound traffic on port 443 to port 42828.

What do we have to do?


Thx in advance

---

### Post by groupmsl on 2010-03-12
Do you want to set up the port forwarding rule on your router, on on Ubuntu?

---

### Post by manfredell on 2010-03-12
> **groupmsl said:**
> Do you want to set up the port forwarding rule on your router, on on Ubuntu?

I want to setup the rule on the ubuntu server.

---

### Post by manfredell on 2010-03-15
Anyone? Please

---

### Post by groupmsl on 2010-03-15
> **manfredell said:**
> Anyone? Please

I'm sorry, I know I posted, I know how to port forward on many routers, but not Ubuntu... I did some reasearch, but I'm not exactly a Linux expert myself! Sorry.

---

### Post by adam814 on 2010-03-15
Let me see if I understand what you're trying to do here: You have an Ubuntu server acting as a router and you need to redirect port 443 traffic to port 42828

If so I think you can pull it off with something like this assuming you're also running iptables
```
sudo iptables -t NAT -A PREROUTING --destination-port 443 -j REDIRECT --to-port 42828
```

---

