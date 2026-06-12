---
title: "Desktop Sharing (Vino) doesn't work Ubuntu 13.04"
date: 2013-06-16
forum: Networking &amp; Wireless
---

### Post by MeloCourier on 2013-06-16
Opened dash/desktop sharing.
Marked first and second check boxes to allow remote connection.
Going from my smartphone shows no service at my Ubuntu machine IP address.

Back to Ubuntu machine, netstat shows no listening at 5900 or 590x ports

Proto Recv-Q Send-Q Endereço Local          Endereço Remoto         Estado       PID/Program name
tcp        0      0 0.0.0.0:51413           0.0.0.0:*               OUÇA       5852/transmission-g
tcp        0      0 127.0.1.1:53            0.0.0.0:*               OUÇA       1369/dnsmasq    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               OUÇA       978/cupsd       
tcp        0      0 192.168.1.136:52798     187.126.226.33:23048    ESTABELECIDA 5852/transmission-g
tcp        0      0 192.168.1.136:43331     74.125.130.125:5222     ESTABELECIDA 8092/chrome     
tcp        0      0 192.168.1.136:59286     189.55.186.147:20885    ESTABELECIDA 5852/transmission-g
tcp        0      0 192.168.1.136:54968     91.189.94.12:80         ESTABELECIDA 8092/chrome     
tcp        0      0 192.168.1.136:40454     41.34.43.179:51463      ESTABELECIDA 5852/transmission-g
tcp        1      0 192.168.1.136:44130     91.189.94.25:80         ESPERANDO_FECHAR 8342/ubuntu-geoip-p
tcp        0      0 192.168.1.136:34566     74.125.234.78:443       ESTABELECIDA 8092/chrome     
tcp        0      0 192.168.1.136:43627     84.109.166.138:48437    ESTABELECIDA 5852/transmission-g
tcp        1      0 192.168.1.136:58087     5.135.176.153:80        ESPERANDO_FECHAR 5852/transmission-g
tcp        1      0 192.168.1.136:58088     5.135.176.153:80        ESPERANDO_FECHAR 5852/transmission-g
tcp        0      0 192.168.1.136:34236     84.104.15.176:23208     ESTABELECIDA 5852/transmission-g
tcp6       0      0 :::51413                :::*                    OUÇA       5852/transmission-g
tcp6       0      0 ::1:631                 :::*                    OUÇA       978/cupsd       


Had tried remove / reinstall vino from terminal and from Software Centre
Not working.

Any suggestion?
Ubuntu 13.04 x64

---

### Post by MeloCourier on 2013-06-21
help!

---

### Post by MeloCourier on 2013-06-25
Still haven't found solution...

---

