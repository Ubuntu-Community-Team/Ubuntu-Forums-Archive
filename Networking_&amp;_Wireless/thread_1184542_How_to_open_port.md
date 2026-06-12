---
title: "How to open port ?"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by reyhan on 2009-06-11
hello everyone I wanna ask something
how do i open port with Iptables on my ubuntu server
and 1 more thing do i have to edit my squid.conf for opening port ??
(sorry for my english , my english is bad)

---

### Post by kevdog on 2009-06-11
Which port do you want to open?

Can you post the following:

sudo iptables -L

---

### Post by Tews on 2009-06-11
Using the UFW allow command is easiest .

```
sudo ufw enable
sudo ufw allow xxxxx 
```

---

### Post by reyhan on 2009-06-11
i want to open tcp port  



```
10000-10100 and  13456-13556 
```

```
iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```

okay.. ufw is a firewall ? right ?

---

### Post by iponeverything on 2009-06-11
> **reyhan said:**
> i want to open tcp port  



```
10000-10100 and  13456-13556 
```

```
iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  
```


None of your ports are blocked. Your default policy on all chains is ACCEPT and there are not any rules in place.

> okay.. ufw is a firewall ? right ?

ufw is not a firewall, it just a frontend for iptables. And it sets up, what I assume, is set of sane default rules. I don't use it, but if it makes it a bit easier for someone to do something basic like a opening a port, then yea.

not like the below command is hard.. but hey. 

iptables -A INPUT -p tcp --destination-port 22 -j ACCEPT

---

### Post by iponeverything on 2009-06-11
> **reyhan said:**
> hello everyone I wanna ask something
how do i open port with Iptables on my ubuntu server
and 1 more thing do i have to edit my squid.conf for opening port ??
(sorry for my english , my english is bad)

Don't feel bad, I don't speak bahasa Indonesia.

Squid does not "open" ports. You can change the port squid "listens" on, this very easy. Just look through the squid.conf, it is heavily commented and the line will have "listen" in it.

---

### Post by kevdog on 2009-06-12
All of your ports are open.  The only need to open them would be to make your default input chain set to reject and then open up specific ports or port ranges using whatever method.

---

