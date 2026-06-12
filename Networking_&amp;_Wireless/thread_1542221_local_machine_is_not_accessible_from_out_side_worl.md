---
title: "local machine is not accessible from out side world"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by jigneshvasoya on 2010-07-30
I m using the pc as gateway..............
i have two NICs:
[INDENT]1) 10.6.15.254 ---> for internal network 10.6.15.0
2) 10.6.0.115 -----> for out side world

[/INDENT]I can ping and ssh any out side machine but when i try to ping or ssh any machine in the 10.6.15.0 network it says host unreachable....

i can ping and ssh gateway i.e. 10.6.15.254 and 10.6.0.115 but not the client machine in the 10.6.15.0 network from out side world

even i flush iptable rules i can not access any client machin

i m using ubuntu 10.04 as operating system..

---

### Post by Iowan on 2010-07-30
Post results of **route -n**.
Those addresses are in "private network" range - They *shouldn't* be accessible from Internet (outside world?). If you have port-forwarding to the gateway machine, though...

---

### Post by jigneshvasoya on 2010-08-11
> This is the routing table info on (10.6.15.254 &
> 10.6.0.115):
>
> sysad@gateway:~$ route
> Kernel IP routing table
> Destination    Gateway     Genmask          Flags  Metric  Ref  Use  Iface
> 10.6.16.0       *                 255.255.255.0    U         0        0
> 0     eth0
> 10.6.15.0       *                 255.255.255.0    U         0        0
> 0     eth0
> 10.6.0.0         *                 255.255.0.0       U         0
> 0      0     eth1
> link-local        *                 255.255.0.0       U       1000
> 0      0     eth1
> default         gateway.out.com 0.0.0.0           UG      100      0
> 0     eth1
>
> This gateway has two NICs:
> 10.6.15.254 : has an alias 10.6.16.254 - this is eth0 and connected with
> internal network
> 10.6.0.115 : this is eth1 and connected with outside network
>
> And this is iptables entry:
>
> root@gateway:/home/sysad# iptables -L
> Chain INPUT (policy ACCEPT)
> target         prot opt  source               destination
> ACCEPT     tcp   --    [10.6.0.0/16]("http://10.6.0.0/16")           anywhere       tcp dpt:ssh
> ACCEPT     tcp   --    anywhere            [10.6.0.0/16]("http://10.6.0.0/16")      tcp dpt:ssh
> ACCEPT     tcp   --    anywhere            anywhere        tcp dpt:www
>
> Chain FORWARD (policy ACCEPT)
> target     prot opt source               destination
> ACCEPT     all  --  [10.6.0.0/16]("http://10.6.0.0/16")          anywhere            ctstate
> NEW,RELATED,SNAT,DNAT
> ACCEPT     all  --  [10.6.0.0/16]("http://10.6.0.0/16")          anywhere            ctstate
> NEW,RELATED,SNAT,DNAT
> ACCEPT     all  --  [10.6.0.0/16]("http://10.6.0.0/16")          anywhere            ctstate
> NEW,RELATED,SNAT,DNAT
> ACCEPT     all  --  [10.6.0.0/16]("http://10.6.0.0/16")          anywhere            ctstate
> NEW,RELATED,SNAT,DNAT
>
> Chain OUTPUT (policy ACCEPT)
> target     prot opt source               destination

---

