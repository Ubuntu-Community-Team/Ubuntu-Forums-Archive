---
title: "MX key entry problems in named.conf.local"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by Mohed on 2009-06-04
Hello. My named.conf.local works well when I do not enter a MX key, but when I add one the dns server fails. Below is my named.conf.local file

;haidar.se
$TTL    604800
@       IN      SOA     ns1.haidar.se. mohed.haidar.se. (
                        2009060201 ; Serial
                        604800        ; Refresh
                        86400          ; Retry
                        2419200       ; Expire
                        604800)        ; Negative Cache TTL
;
@        IN      NS      ns1
ns1     IN      A       83.233.242.154
@       IN        NS    ns0.xname.org.
@       IN      NS    ns1.xname.org.
@       IN        MX    mail
mail    IN      A       192.168.0.99
           IN      A       192.168.0.99
www   IN      A       192.168.0.99
ssh        IN       A       192.168.0.99

a dig reveals

root@serveThem:~# dig haidar.se

; <<>> DiG 9.5.1-P2 <<>> haidar.se
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: SERVFAIL, id: 26000
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;haidar.se.            IN    A

;; Query time: 5 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Thu Jun  4 06:18:36 2009
;; MSG SIZE  rcvd: 27

root@serveThem:~# 

and a ping

ping: unknown host haidar.se

Any advice ? M Haidar

---

