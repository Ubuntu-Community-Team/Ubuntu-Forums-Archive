---
title: "PPPOE not working"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by pe7o on 2012-01-24
Hi 
I am trying to configure pppoe
I do the steps as required and even i did them several times
i tried pppoeconf i runed RP-PPPoE 3.8
when i use :
sudo pon dsl-provider 
sudo pppoe-start

It says that I am conected but when i ping anyone (even localhost) : 100% loss
i use pppoe-connect and it gives me :
CHAP authentication succeeded: Welcome to ISP
CHAP authentication succeeded
not replacing existing default route through ppp1
Cannot determine ethernet address for proxy ARP
local  IP address adres-1
remote IP address adress-2
primary   DNS address dns-adress2
secondary DNS address dns-adress1

before that it have been giving me error 
pppd cannot conect to interface so i used
pppd adres-1:adres-2

Can you tell me what I have did wrong ?
I am conected to my ISP throug local network
p.s.: before I re-install the same ubuntu I managed to connect somehow(I don't know how :D)
so I know it works :)

---

