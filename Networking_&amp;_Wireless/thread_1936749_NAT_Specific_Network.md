---
title: "NAT Specific Network"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by miles007 on 2012-03-06
Hi.
I have setup Ubuntu server , I'm trying to NAT my ip address coming from different network. The ip network I'm able to NAT if I'm direct connected to server like.
Internet --- Ubuntu----Switch Client. I can do that no problem. But I want to setup mikrotik router between Ubuntu server and switch like this.
Internet---Ubuntu-100.10.100.0/29--Mikrotik--172.16.0.0/16---Swith---- Clients. If I try to ping example google from Mirktoik box I'm able to see internet but from 172.16.0.0/16 network I won't be able to get internet.
Any help I really appreciate.

thx
Miles

---

### Post by jonobr on 2012-03-06
Hello

If you can ping internet from Mikrotik but not from the 172.16.0.0/16 then the issue is your Mikrotik no?

I read this post a couple of times and figure Im missing something?

You could run a 
```
sudo tcpdump -nnvXSs 0 -c2 icmp 
``` and then ping and see if it hits your ubuntu box.

I hope the syntax is ok

---

