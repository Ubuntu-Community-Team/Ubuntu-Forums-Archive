---
title: "Lucid DNS problems"
date: 2010-05-16
forum: Networking &amp; Wireless
---

### Post by odalvez on 2010-05-16
Hi guys!

I have used Karmic Koala without a problem. Now, when I actualize to Lucid Lynk, I begin with problems in my Internet connection.

I have a ADSL connection, and this are, at boot time, the result of "grep pppd /var/log/syslog":

[FONT="Courier New"]May 16 19:43:12 PCalvez pppd[828]: Plugin rp-pppoe.so loaded.
May 16 19:43:12 PCalvez pppd[828]: RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
May 16 19:43:12 PCalvez pppd[854]: pppd 2.4.5 started by root, uid 0
May 16 19:43:12 PCalvez pppd[854]: PPP session is 6122
May 16 19:43:12 PCalvez pppd[854]: Connected to 00:90:1a:42:8b:0a via interface eth0
May 16 19:43:12 PCalvez pppd[854]: Using interface ppp0
May 16 19:43:12 PCalvez pppd[854]: Connect: ppp0 <--> eth0
May 16 19:43:20 PCalvez pppd[854]: PAP authentication succeeded
May 16 19:43:20 PCalvez pppd[854]: peer from calling number 00:90:1A:42:8B:0A authorized
May 16 19:43:20 PCalvez pppd[854]: Cannot determine ethernet address for proxy ARP
May 16 19:43:20 PCalvez pppd[854]: local  IP address 190.172.170.61
May 16 19:43:20 PCalvez pppd[854]: remote IP address 200.63.148.113
May 16 19:43:20 PCalvez pppd[854]: primary   DNS address 200.63.155.87
May 16 19:43:20 PCalvez pppd[854]: secondary DNS address 200.63.155.215
[/FONT]


And this is "ifconfig -a":
[FONT="Courier New"]eth0      Link encap:Ethernet  direcciónHW 00:1d:92:73:13:95  
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:5392 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:5006 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:4006942 (4.0 MB)  TX bytes:805250 (805.2 KB)
          Interrupción:25 Dirección base: 0x2000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:54 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:54 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:3900 (3.9 KB)  TX bytes:3900 (3.9 KB)

ppp0      Link encap: Protocolo punto a punto  
          Direc. inet:190.172.157.199  P-t-P:200.63.148.113  Másc:255.255.255.255
          ACTIVO PUNTO A PUNTO FUNCIONANDO NOARP MULTICAST  MTU:1492  Métrica:1
          Paquetes RX:4930 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:4837 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:3 
          Bytes RX:3869800 (3.8 MB)  TX bytes:691436 (691.4 KB)
[/FONT]


But not all it's all right! Ping by IP works, "ping 8.8.8.8":
[FONT="Courier New"]PING 8.8.8.8 (8.8.8.8 ) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=243 time=205 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=242 time=194 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=243 time=191 ms
^C
--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 191.647/197.292/205.760/6.108 ms
[/FONT]


But not with an URL, "ping www.google.com":
[FONT="Courier New"]ping: unknown host [www.google.com](www.google.com)[/FONT]

Of course, the Chrome and Firefox shows the same behavior. Sometimes is enough with a "poff" and a "pon dsl-provider". Other times, I must run "pppoeconf".

I already disable IPv6!!!

**Why isn't working the DNS at boot time???** :confused:

Thanks in advance!

Daniel
Argentina

---

### Post by sedawk on 2010-05-17
```

May 16 19:43:20 PCalvez pppd[854]: primary DNS address 200.63.155.87
May 16 19:43:20 PCalvez pppd[854]: secondary DNS address 200.63.155.215

```

I'm not absolutely sure how pppd tells the system about the
two DNS servers, but have a look at /etc/resolv.conf
and see if there are any differences between the non-working
and working situation.

Instead of "ping www.google.com" you can directly test
the DNS with
[CODE]
# Using the default (from /etc/resolv.conf)
dig www.google.com
# Use primary server
dig @200.63.155.87 www.google.com
# Use secondary server
dig @200.63.155.215 www.google.com
[CODE]

---

### Post by odalvez on 2010-05-17
Thanks a lot sedawk!

I'll try it later and then I post the results! Best regards...

Daniel

P.D: I love the "awk", but never use "sed"! :)

---

### Post by odalvez on 2010-05-18
Hi guys!

The problem is an empty /etc/revolv.conf file at boot time!!! :mad: In this moment, the file has modified time 3/3/2009!

When I do "poff" and then "pon dsl-provider", the /etc/revolv.conf file is populated with the 2 DNS address that are shown in the pppd messages written in the /var/log/syslog, and everything works fine.

Now, the question is: why the /etc/revolv.conf file isn´t written at boot time?

Thanks a lot!

Daniel

---

