---
title: "can't conect 2 pc's with lubuntu but with ubuntu i can¿I need some package?"
date: 2012-07-08
forum: Networking &amp; Wireless
---

### Post by rolansel on 2012-07-08
Hi.
first I don't speak english sorry if i write bad :(

I'm trying to conect  2 pc for remote desktop by crossover wire

I sucess  conecting the same pcs with ubuntu

Pc_Master=ubuntu 10.04
Pc_slave=ubuntu 10.04

Pc_master
autoeth0  IPV4 method=automatic(DHCP)
Autoeth0 then conected success

Pc_slave
Edit conecction ->wire->add->name=conexion1  & IPv4 method=shared with others
then conecction succeed

when I do this with: 

Pc_Master = ubuntu 10.04 
Pc_slave=lubuntu 11.10

same Pcs, same procediment,
Pc_master
autoeth0 metod=automatic(DHCP)
Autoeth0 conecction fail

pc_slave
Edit conecction ->wire->add->name=conexion1 & IPv4 method=shared with others
conexion1 conecction fail

what happen?

---

### Post by praseodym on 2012-07-08
Lubuntu lacks the package "modemmanager" per default. Maybe this one is missing...

---

### Post by rolansel on 2012-07-17
Thanks finally I remove lubuntu 11.10 and installed ubuntu 10.04. in 10.04  problem was easily solved  about 2 minutes

---

