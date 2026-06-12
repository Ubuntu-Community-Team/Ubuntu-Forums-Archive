---
title: "Strange IP when I type: route -n"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by MWesten on 2010-09-18
Hello friends, I'm a happy Ubuntu user (since 9.4) and I really like it.
I use Witopia VPN and never had a problem, yesterday it stopped working so I search on google hoping to find info, and somehow I found "route -n" command to see the table, I don't know if that has something to do with my issue about not connecting to vpn, but, what got my attention was the results, so If I type: route -n I get:

Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask                    Indic Métric Ref    Uso Interfaz
74.115.160.143  192.168.1.1     255.255.255.255   UGH   0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0              U     1      0        0         eth0
169.254.0.0     0.0.0.0         255.255.0.0                 U     1000   0        0         eth0
0.0.0.0         192.168.1.1     0.0.0.0                        UG    0      0        0            eth0

I don't know what is the normal table I should be getting, but I just want to know:
-  if is normal to get: 74.115.160.143
- if there's a way to "restore" this table in case something is wrong

Thanks a lot guys! I really appreciate your help.
):P

---

### Post by MWesten on 2010-09-18
I just found that the ip is from my Witopia VPN service.
Thanks.

---

