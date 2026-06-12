---
title: "Computer to NMR"
date: 2012-07-25
forum: Networking &amp; Wireless
---

### Post by conradin on 2012-07-25
Hi All,
I have a NMR spectrometer which will not talk to my ubuntu computer despite having been set up according to directions.
I have a loaner SunBlade system which works fine though. 
I gathered some info using commands shown below, but Im confused about the netmask which from ifconfig is ffffff00 but in arp is 255.255.255.255
What Im planning to do is setup my config files the way the SunBlade station has them, and see if that works. Can someone have a look and see if it all makes sense, and maybe make suggestions about what Im trying to do. Am I missing anything?
```
$ ifconfig -a
eri0 flags=1000843<UP , BROADCAST< RUNNING,MULTICAST,IPV4> mtu 8232 index 1
inet 10.0.0.1 netmask ffffff00 broadcast 10.0.0.255

$cat /etc/hosts
127.0.0.1 localhost
10.0.0.1 I400 loghost
10.0.0.2 inova
10.0.0.4 inovaauto

$arp -a
Net to media table IPV4
Dvice     IP Address   Mask                Flags        Phys Addr
______   ____________  ______             ________     _________________
eri0	inova		255.255.255.255		      08:00:3e:27:9b:6e	
eri0	I400		255.255.255.255	   SP		00:03:ba:b0:6c:97
eri0	240.0.0.0	240.0.0.0	   SM		01:00:5e:00:00:00

$arp 10.0.0.2
10.0.0.2(10.0.0.2) at 8:0:3e:27:9b:6e
```

---

