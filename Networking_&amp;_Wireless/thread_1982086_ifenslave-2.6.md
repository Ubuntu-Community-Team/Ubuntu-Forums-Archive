---
title: "ifenslave-2.6 ?"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by JuanPabloCuervo on 2012-05-17
Hi...

I have KXStudio 10.04.3 LTS x86_64
based on Ubuntu 10.04 LTS + KDE Plasma Desktop.

#1. don't want to upgrade to Ubuntu* or Kubuntu 12.04 LTS.

I have 2 different internet connections available...

eth0 & ppp0
or wlan0 & ppp0


both work when used 1 at a time... $ ping [www.yahoo.com](www.yahoo.com), etc...
but 
would like to round-robin load balancing the two with ifenslave.

i have iproute, libc6, net-tools NET-3 installed.
[http://packages.ubuntu.com/lucid-updates/ifenslave-2.6](http://packages.ubuntu.com/lucid-updates/ifenslave-2.6)
[http://manpages.ubuntu.com/manpages/lucid/man8/ifenslave-2.6.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/ifenslave-2.6.8.html)

steps i follow:
$ sudo modprobe bonding
$ sudo ifconfig bond0 192.168.0.1 ".10 or .99"
$ sudo ifenslave -f bond0 eth0
$ ifconfig
bond0 is **Master**
eth0 is **Slave.**
$ ping [www.yahoo.com](www.yahoo.com)
error #1. 

$ sudo ifconfig eth0 192.168.0.2
$ ping [www.yahoo.com](www.yahoo.com)
error #1.

$ sudo ifenslave -f bond0 ppp0
error #2.

??????????????????????????????????????????????

$ sudo ifenslave bond0 wlan0 
OK.
but...
$ ping [www.yahoo.com](www.yahoo.com)
error #1.

$ sudo ifconfig bond0 192.168.0.99
OK
$ ping [www.yahoo.com](www.yahoo.com)
error.

$ sudo ifenslave -d bond0 wlan0
waiting wlan0 to reconect..
$ ping [www.yahoo.com](www.yahoo.com)

PING any-fp3-real.wa1.b.yahoo.com (98.139.183.24) 56(84) bytes of data.
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_seq=1 ttl=48 time=218 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_seq=2 ttl=47 time=208 ms

**problem seems bond0.**

$ cat /proc/net/bonding/bond0 
Ethernet Channel Bonding Driver: v3.7.0 (June 2, 2010)

Bonding Mode: load balancing (round-robin)
MII Status: **up**
MII Polling Interval (ms): 0
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: wlan0
MII Status: **up**
Speed: 100 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 88:a5:bd:00:3f:14
Slave queue ID: 0

$ ping wwww.yahoo.com
error #3.
ping: unknown host [www.yahoo.com](www.yahoo.com)

$ sudo ifenslave -d bond0 wlan0
waiting wlan0 to reconect..
$ ping [www.yahoo.com](www.yahoo.com)

PING any-fp3-real.wa1.b.yahoo.com (98.139.183.24) 56(84) bytes of data.
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_seq=1 ttl=48 time=218 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_seq=2 ttl=47 time=208 ms

$ uname -a
Linux jpcjpcjpc 2.6.38-15-generic #59~lucid1-Ubuntu SMP Mon Apr 30 23:38:40 UTC 2012 x86_64 GNU/Linux


links:
[http://www.cyberciti.biz/tips/debian-ubuntu-teaming-aggregating-multiple-network-connections.html](http://www.cyberciti.biz/tips/debian-ubuntu-teaming-aggregating-multiple-network-connections.html)

???
bonding 2 interfaces has same problem.

```
jpc@jpcjpcjpc:~$ ping www.yahoo.com
PING any-fp3-real.wa1.b.yahoo.com (98.139.183.24) 56(84) bytes of data.
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_seq=1 ttl=48 time=218 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_seq=2 ttl=47 time=208 ms
^C
--- any-fp3-real.wa1.b.yahoo.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 208.136/213.302/218.469/5.187 ms
jpc@jpcjpcjpc:~$ modprobe -v bonding mode=0 arp_interval=100 arp_ip_target=192.168.0.1
jpc@jpcjpcjpc:~$ cat /proc/net/bonding/bond0 
Ethernet Channel Bonding Driver: v3.7.0 (June 2, 2010)

Bonding Mode: load balancing (round-robin)
MII Status: down
MII Polling Interval (ms): 0
Up Delay (ms): 0
Down Delay (ms): 0
jpc@jpcjpcjpc:~$ sudo ifenslave bond0 wlan0
jpc@jpcjpcjpc:~$ cat /proc/net/bonding/bond0 
Ethernet Channel Bonding Driver: v3.7.0 (June 2, 2010)

Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 0
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: wlan0
MII Status: up
Speed: 100 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 88:a5:bd:00:3f:14
Slave queue ID: 0
jpc@jpcjpcjpc:~$ ping www.yahoo.com
ping: unknown host www.yahoo.com
jpc@jpcjpcjpc:~$ ping www.yahoo.com
ping: unknown host www.yahoo.com
jpc@jpcjpcjpc:~$ cat /proc/net/bonding/bond0 
Ethernet Channel Bonding Driver: v3.7.0 (June 2, 2010)

Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 0
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: wlan0
MII Status: up
Speed: 100 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 88:a5:bd:00:3f:14
Slave queue ID: 0
jpc@jpcjpcjpc:~$ sudo ifenslave -d bond0 wlan0
jpc@jpcjpcjpc:~$ ping www.yahoo.com
PING any-fp3-real.wa1.b.yahoo.com (209.191.122.70) 56(84) bytes of data.
64 bytes from ir1.fp.vip.mud.yahoo.com (209.191.122.70): icmp_seq=1 ttl=52 time=151 ms
64 bytes from ir1.fp.vip.mud.yahoo.com (209.191.122.70): icmp_seq=2 ttl=52 time=151 ms
^C64 bytes from ir1.fp.vip.mud.yahoo.com (209.191.122.70): icmp_seq=3 ttl=52 time=374 ms

--- any-fp3-real.wa1.b.yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 151.166/225.928/374.726/105.217 ms
jpc@jpcjpcjpc:~$ uname -a
Linux jpcjpcjpc 2.6.38-15-generic #59~lucid1-Ubuntu SMP Mon Apr 30 23:38:40 UTC 2012 x86_64 GNU/Linux
jpc@jpcjpcjpc:~$ ping www.yahoo.com
PING any-fp3-real.wa1.b.yahoo.com (209.191.122.70) 56(84) bytes of data.
64 bytes from ir1.fp.vip.mud.yahoo.com (209.191.122.70): icmp_seq=1 ttl=52 time=150 ms
64 bytes from ir1.fp.vip.mud.yahoo.com (209.191.122.70): icmp_seq=2 ttl=52 time=151 ms
^C
--- any-fp3-real.wa1.b.yahoo.com ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2002ms
rtt min/avg/max/mdev = 150.604/151.178/151.753/0.693 ms
jpc@jpcjpcjpc:~$ sudo ifenslave bond0 wlan0 eth0
jpc@jpcjpcjpc:~$ ping www.yahoo.com
ping: unknown host www.yahoo.com
jpc@jpcjpcjpc:~$ ifconfig
bond0     Link encap:Ethernet  direcciónHW 88:a5:bd:00:3f:14  
          Direc. inet:192.168.0.99  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::beae:c5ff:fe5d:f05b/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MAESTRO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:1841922 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1277455 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:1944325780 (1.9 GB)  TX bytes:100773620 (100.7 MB)

eth0      Link encap:Ethernet  direcciónHW 88:a5:bd:00:3f:14  
          ACTIVO DIFUSIÓN FUNCIONANDO ESCLAVO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:1779495 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1237408 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:1874659346 (1.8 GB)  TX bytes:96965117 (96.9 MB)
          Interrupción:20 Memoria:fbbe0000-fbc00000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:834 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:834 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:82774 (82.7 KB)  TX bytes:82774 (82.7 KB)

wlan0     Link encap:Ethernet  direcciónHW 88:a5:bd:00:3f:14  
          ACTIVO DIFUSIÓN FUNCIONANDO ESCLAVO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:62427 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:40047 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:69666434 (69.6 MB)  TX bytes:3808503 (3.8 MB)

jpc@jpcjpcjpc:~$ cat /proc/net/bonding/bond0 
Ethernet Channel Bonding Driver: v3.7.0 (June 2, 2010)

Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 0
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: wlan0
MII Status: up
Speed: 100 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: 88:a5:bd:00:3f:14
Slave queue ID: 0

Slave Interface: eth0
MII Status: up
Speed: 100 Mbps
Duplex: full
Link Failure Count: 0
Permanent HW addr: bc:ae:c5:5d:f0:5b
Slave queue ID: 0
jpc@jpcjpcjpc:~$ ping www.yahoo.com
ping: unknown host www.yahoo.com
jpc@jpcjpcjpc:~$ sudo ifenslave -d bond0 wlan0 eth0
jpc@jpcjpcjpc:~$ ping www.yahoo.com
ping: unknown host www.yahoo.com
jpc@jpcjpcjpc:~$ ping www.yahoo.com
PING any-fp3-real.wa1.b.yahoo.com (98.139.183.24) 56(84) bytes of data.
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_seq=1 ttl=48 time=229 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_seq=2 ttl=47 time=207 ms
64 bytes from ir2.fp.vip.bf1.yahoo.com (98.139.183.24): icmp_seq=3 ttl=48 time=252 ms
^C

```

---

