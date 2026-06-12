---
title: "Multiple sessions using different IP's ?"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by terlington on 2009-02-07
Hi all,

I own a server (in OVH company) running Ubuntu 8.04 Desktop : On this server, I have my main IP (eth0) and a failover IP (eth0:0). Here is my ifconfig :


```

admin@rxxxxx:~$ sudo ifconfig
[sudo] password for admin:
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:76:cf:d4
          inet adr:94.23.X.Y  Bcast:94.23.Y.255  Masque:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:611697 erreurs:0 :0 overruns:0 frame:0
          TX packets:540303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000
          Octets reçus:610337496 (582.0 MB) Octets transmis:330082823 (314.7 MB)
          Interruption:19 Adresse de base:0x2000

eth0:0    Link encap:Ethernet  HWaddr 00:1c:c0:76:cf:d4
          inet adr:87.98.X.Y  Bcast:87.255.255.255  Masque:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interruption:19 Adresse de base:0x2000

lo        Link encap:Boucle locale
          inet adr:127.0.0.1  Masque:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:209975 erreurs:0 :0 overruns:0 frame:0
          TX packets:209975 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0
          Octets reçus:21308703 (20.3 MB) Octets transmis:21308703 (20.3 MB)

```

=> What I would like to do, I have two sessions (two different users) on this server : I would like the session 1 to access the outside trough the interface eth0 ( so trough IP 94.23.X.Y) and the session 2 should have access to the outside trough the interface et0:0 (so trough IP 87.98.X.Y)

I tried this :

ip ro change default via 94.23.X.254 dev eth0 src 87.98.X.Y

It works well but the problem is that it affect the two session !
So : How could i do in order for the session 1 and 2 to uses my 2 different ip ?

I really need your help ! Thank you in advance !

---

### Post by terlington on 2009-02-07
No Idea ?

---

### Post by terlington on 2009-02-07
Up ! Need your help !

---

