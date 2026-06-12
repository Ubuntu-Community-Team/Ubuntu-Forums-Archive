---
title: "Setup ufw for skype"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by tomillares on 2012-10-19
I've set up ufw to use with skype. But is anything wrong? Any time I tried to connect to skype with ufw  enabled, it last more than three minutes to connect. When ufw is  disabled skype connect quickly. These are the rules:

manuel@manuel-HP-Compaq-nx7400-RH399ET-ABE:~$ sudo ufw status
[sudo] password for manuel: 
Estado: activo

Hasta                      Acción      Desde
-----                      ------      -----
443/tcp                    ALLOW       Anywhere
51413/tcp                  ALLOW       Anywhere
51413/udp                  ALLOW       Anywhere
80                         ALLOW       Anywhere (log-all)
37922                      ALLOW       Anywhere
443/tcp                    ALLOW       Anywhere (v6)
51413/tcp                  ALLOW       Anywhere (v6)
51413/udp                  ALLOW       Anywhere (v6)
80                         ALLOW       Anywhere (v6) (log-all)
37922                      ALLOW       Anywhere (v6)

443/tcp                    ALLOW OUT   Anywhere
51413/tcp                  ALLOW OUT   Anywhere
51413/udp                  ALLOW OUT   Anywhere
80                         ALLOW OUT   Anywhere (log-all)
37922                      ALLOW OUT   Anywhere
443/tcp                    ALLOW OUT   Anywhere (v6)
51413/tcp                  ALLOW OUT   Anywhere (v6)
51413/udp                  ALLOW OUT   Anywhere (v6)
80                         ALLOW OUT   Anywhere (v6) (log-all)
37922                      ALLOW OUT   Anywhere (v6)

Is dangerous to disable ufw?

---

