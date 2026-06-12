---
title: "Static IP on virtual machine"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by ichhabekeineahnung on 2010-06-16
Hy guys, i'm banging my head on this and could not find a way out...so far!! I did already the same operation on my laotop and everything went smooth as silk!!
 
I have a 10.04 on virtual machine (VMWare)
Network card is bridged.
I wanted to change the connection from DHCP to static IP. Tried both ways already:
- automatic: Sys&shy;tem –> Pref&shy;er&shy;ences –> Net&shy;work Connections
- manual: gedit and stuff
as described here
[http://www.liberiangeek.net/2010/06/how-to-configure-static-ip-addresses-in-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/06/how-to-configure-static-ip-addresses-in-ubuntu-10-04-lucid-lynx/)
 
The connection is established and ifconfig shows the correct IP, but nobody can ping me and i cannot ping anybody!! I have no connection to the internet.
 
```
vm_ll@me:~$ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:0c:29:e6:87:69  
          indirizzo inet:10.1.1.45  Bcast:10.1.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::20c:29ff:fee6:8769/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1339 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:151544 (151.5 KB)  Byte TX:34578 (34.5 KB)
          Interrupt:19 Indirizzo base:0x2000 
lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:17657 (17.6 KB)  Byte TX:17657 (17.6 KB)
 
 
vm_ll@me:~$ ping 10.1.1.1
PING 10.1.1.1 (10.1.1.1) 56(84) bytes of data.
From 10.1.1.45 icmp_seq=2 Destination Host Unreachable
From 10.1.1.45 icmp_seq=3 Destination Host Unreachable
From 10.1.1.45 icmp_seq=4 Destination Host Unreachable
From 10.1.1.45 icmp_seq=5 Destination Host Unreachable
From 10.1.1.45 icmp_seq=6 Destination Host Unreachable
From 10.1.1.45 icmp_seq=7 Destination Host Unreachable
^C
--- 10.1.1.1 ping statistics ---
9 packets transmitted, 0 received, +6 errors, 100% packet loss, time 13718ms
, pipe 4

```
 
10.1.1.1 is the gateway, DNS server and DHCP server.
 
Any help is welcome ;)

---

### Post by ichhabekeineahnung on 2010-06-18
Nobody??
i think is something related to the virtual machine, as on my personal laptop works like a charm. Has anybody ever tried to force a static ip on a virtual linx?

---

