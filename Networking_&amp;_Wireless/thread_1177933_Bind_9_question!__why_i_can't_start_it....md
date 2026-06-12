---
title: "Bind 9 question! : why i can't start it...?"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by AlexenderReez on 2009-06-03
```
root@ubuntu:/etc/bind/zones# /etc/init.d/bind9 restart
 * Stopping domain name service... bind9                                        
**[COLOR="Red"]rndc: connect failed: 127.0.0.1#953: connection refused[/COLOR]**
                                                                         [ OK ]
 * Starting domain name service... bind9                                 [fail] 

```

however i still can dig it..
```
root@ubuntu:/etc/bind/zones# dig NewCore.com

; <<>> DiG 9.5.1-P2 <<>> NewCore.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 55408
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;NewCore.com.			IN	A

;; ANSWER SECTION:
NewCore.com.		900	IN	A	70.35.16.71

;; Query time: 390 msec
;; SERVER: 202.188.0.132#53(202.188.0.132)
;; WHEN: Wed Jun  3 23:25:31 2009
;; MSG SIZE  rcvd: 45


```

please help :(

---

