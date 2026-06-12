---
title: "fresh install cnot get interner here is ifconfig+netstat"
date: 2006-01-25
forum: Networking &amp; Wireless
---

### Post by xstation on 2006-01-25
Cannot access internet on fresh install  BUT can do apt-get update ans SSH 
connection from terminal

here is ifconfig and netstat:

andy@localhost:~$ sudo ifconfig
Password:
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:5C:AF:1F
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b0ff:fe5c:af1f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2100 (2.0 KiB)  TX bytes:1992 (1.9 KiB)
          Interrupt:19 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:236 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19667 (19.2 KiB)  TX bytes:19667 (19.2 KiB)




andy@localhost:~$ sudo netstat -a
Password:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 localhost.localdo:32769 *:*                     LISTEN
tcp        0      0 localhost.localdo:32770 *:*                     LISTEN
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN
tcp        0      0 localhost.localdo:32769 localhost.localdo:53776 ESTABLISHED
tcp        0      0 localhost.localdo:58278 localhost.localdoma:ipp ESTABLISHED
tcp        0      0 localhost.localdo:58279 localhost.localdoma:ipp TIME_WAIT
tcp        0      0 localhost.localdoma:ipp localhost.localdo:58278 ESTABLISHED
tcp        0      0 localhost.localdo:53776 localhost.localdo:32769 ESTABLISHED
udp        0      0 *:bootpc  







andy@localhost:~$ sudo netstat -lp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost.localdo:32769 *:*                     LISTEN     6888/hpiod
tcp        0      0 localhost.localdo:32770 *:*                     LISTEN     6944/python
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN     6864/cupsd
udp        0      0 *:bootpc                *:*                                5971/dhclient3
Active UNIX domain sockets (only servers)


many thanks

xstation:smile: :smile:

---

