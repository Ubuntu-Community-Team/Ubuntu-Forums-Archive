---
title: "need help for network config"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by amitvn on 2011-02-04
Hello ppls,
m using dual boot 10.04 with xp
actually my isp provides two services in dsl one of which i need to connect to internet and one to connect to my lan network(for using dc++).

both with different service name and gateways

now in win xp/vista/7 i can set up to work both of them at same time

but after so much googling i haven't found any good page which can explain me how to do it in ubuntu..
any help will be :D

---

### Post by grahammechanical on 2011-02-04
Please explain the method that you use to connect to the router. Is it one router or two routers? Is it one telephone line or two telephone lines? Will you use ethernet cable?

Regards.

---

### Post by amitvn on 2011-02-04
basically i don't need to configure router as such....my connection is from cable provider...so only ethernet cable connected :P
and in windows i use raspppoe protocol to connect both at a time

equivalent rp-pppoe i have installed and configured 
but to connect both at a time i need to configure one network to disable default gateway in its config..

---

### Post by amitvn on 2011-02-04
basically i don't need to configure router as such....my connection is from cable provider...so only ethernet cable connected :P
and in windows i use raspppoe protocol to connect both at a time

equivalent rp-pppoe i have installed and configured 
but to connect both at a time i need to configure one network to disable default gateway in its config..

---

### Post by debd on 2011-02-04
your problem is not entirely clear to me.
but, you may try doing 

> sudo pppoeconf

---

### Post by amitvn on 2011-02-04
no no i don't want the pppoeconf
i am able to connect to dsl
i jus want to know if two dsl connections can be connected at same time

or just help me to set rp-pppoe based connection to not using default gateway which normal connection use

---

### Post by amitvn on 2011-02-17
actually running pppoe -A gives me this result and i need to connect to worldnet002 for internet access and zone.net to connect to LAN sharing

[B]amit-desktop ~ # pppoe -A
Access-Concentrator: Zone.Net
       Service-Name: Zone.Net
AC-Ethernet-Address: 00:1b:21:2d:96:61
--------------------------------------------------
Access-Concentrator: Rajeshnet3
       Service-Name: Rajeshnet3
Got a cookie: 6e fb ff b7 e9 e9 78 8f 72 bd d7 d1 2f af 82 22 aa 0e 00 00
AC-Ethernet-Address: 00:07:e9:0c:67:fd
--------------------------------------------------
Access-Concentrator: worldnet002
       Service-Name: worldnet002
Got a cookie: 77 2e 0d df 8a 80 a9 cb 6e 0b 89 36 00 2e d4 68 2d 3e 00 00
AC-Ethernet-Address: 00:15:17:c9:f0:5a
--------------------------------------------------
[/B]

and in windows i do this by using raspppoe protocol and disabling use of default gateway from tcp/ip properties.....

now in ubuntu i have set up rp-pppoe connection for zone.net service but m not able to figure out how to disable this use of default gateway in its config

i think now you may be able to understand what i want actually :D

---

