---
title: "Hey its me again..."
date: 2012-03-15
forum: Networking &amp; Wireless
---

### Post by kenshen on 2012-03-15
hey guys its me again with one last question i am trying to install dnsmasq but when i try to start it it gives me dnsmasq: failed to create listening socket: Port 53 already in use help?

---

### Post by kenshen on 2012-03-16
Bump

---

### Post by wannabe user on 2012-03-16
It's probably running, network manager will start it. This thread might help you:

[http://ubuntuforums.org/showthread.php?t=1473485](http://ubuntuforums.org/showthread.php?t=1473485)

---

### Post by jerrrys on 2012-03-17
check it out, may help

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=descriptive+title&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=descriptive+title&sa=Search&cof=FORID:9)

---

### Post by matt_symes on 2012-03-17
Hi

> **kenshen said:**
> hey guys its me again with one last question i am trying to install dnsmasq but when i try to start it it gives me dnsmasq: failed to create listening socket: Port 53 already in use help?

It's almost certainly running.

```
matthew@matthew-Aspire-7540:~/test$ sudo netstat -plan | grep -w [L]ISTEN
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN      7673/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      1077/cupsd      
tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN      1391/ntop       
tcp        0      0 0.0.0.0:17500           0.0.0.0:*               LISTEN      2015/dropbox    
tcp6       0      0 ::1:631                 :::*                    LISTEN      1077/cupsd      
matthew@matthew-Aspire-7540:~/test$ ps aux | grep [d]nsmasq
nobody    7673  0.0  0.0  28808  1104 ?        S    19:50   0:00 /usr/sbin/dnsmasq --no-resolv --no-hosts --keep-in-foreground --cache-size=0 --bind-interfaces --pid-file=/var/run/sendsigs.omit.d/network-manager.dnsmasq.pid --listen-address=127.0.0.1 --proxy-dnssec --conf-file=/var/run/nm-dns-dnsmasq.conf
matthew@matthew-Aspire-7540:~/test$ which dnsmasq
/usr/sbin/dnsmasq
matthew@matthew-Aspire-7540:~/test$
```

Why are you trying to reinstall it ?

Kind regards

---

