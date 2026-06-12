---
title: "Iptables on xenserver host"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by lashae on 2008-12-31
Hi all,

I have a box working on Ubuntu 7.1 which runs xenserver on it. There are two guest operating systems on xen which are configured to have their own ip addresses.

```

**Type       Name       Local IP**
----------------------------------------------------------------
Host       HNaru      10.0.0.254
Guest      Manu       10.0.0.20
Guest      Danu       10.0.0.10    

```

The host HNaru has 3 real IP's, and assigns 2 of them to the guest systems via nat.

```

root@HNaru:/# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source              destination         
DNAT       0    --  anywhere             144.124.110.204     to:10.0.0.20 
DNAT       0    --  anywhere             144.124.110.203     to:10.0.0.10 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:1022 to:10.0.0.10:22 
DNAT       tcp  --  anywhere             anywhere            tcp dpt:www to:10.0.0.10:80 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5280 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:5280 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  0    --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

The host system's iptables is also configured as follows to satisfy guests' needs.
```

root@HNaru:/# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source              destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:5280 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:5280 

Chain FORWARD (policy ACCEPT)
target     prot opt source              destination         
ACCEPT     0    --  Danu                 anywhere            PHYSDEV match --physdev-in vif1.0 
ACCEPT     udp  --  anywhere             anywhere            PHYSDEV match --physdev-in vif1.0 udp spt:bootpc dpt:bootps 
ACCEPT     0    --  Manu                 anywhere            PHYSDEV match --physdev-in vif4.0 
ACCEPT     udp  --  anywhere             anywhere            PHYSDEV match --physdev-in vif4.0 udp spt:bootpc dpt:bootps 

Chain OUTPUT (policy ACCEPT)
target     prot opt source              destination         


```

Guest systems, ie. Manu, have no firewall rules installed.
```

Manu:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

```

All of the configuration works here perfect, except that the port 5280. If I try to connect from Manu to 10.0.0.20:5280, the connection is successfull. However when I try to access 'http://144.124.110.204:5280/' (from Manu again) what I get is a connection timeout. 

If I run the following on the host 
```
root@HNaru:/# nmap -p 5280 10.0.0.20
```

I see that the port is open. 

However executing the following from outside,
```
root@HNaru:/# nmap -p 5280 144.124.110.204
```
states that the port is closed.

Any thoughts would be appreciated.

---

