---
title: "LAN, no Internet."
date: 2010-07-23
forum: Networking &amp; Wireless
---

### Post by mentalow on 2010-07-23
Hey.

I have a strange problem. I can access to the admin-panel of my router, can ping it, can ping LAN-computers but, cant do anything with internet, except of DNS Resolution. Internet works with another Wireless Network, but not with this one. Its not cuz of WPA, already tried to disable any security.
Dell Studio 17. 

```
scratchy@scratchy-laptop:~$ uname -a
Linux scratchy-laptop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
``````
scratchy@scratchy-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:19:d8:d6:de  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:17 

eth1      Link encap:Ethernet  HWaddr 00:23:4e:b6:fc:b8  
          inet adr:192.168.1.6  Bcast:192.168.1.255  Masque:255.255.255.0
          adr inet6: fe80::223:4eff:feb6:fcb8/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:165723 erreurs:0 :0 overruns:0 frame:94430
          TX packets:127877 errors:103 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:223124114 (223.1 MB) Octets transmis:14861793 (14.8 MB)
          Interruption:17 
``````
scratchy@scratchy-laptop:~$ route -n
Table de routage IP du noyau
Destination     Passerelle      Genmask         Indic Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1
``````
scratchy@scratchy-laptop:~$ nslookup google.fr
Server:        192.168.1.254
Address:    192.168.1.254#53

Non-authoritative answer:
Name:    google.fr
Address: 66.249.92.104

``````
scratchy@scratchy-laptop:~$ ping 192.168.1.254
PING 192.168.1.254 (192.168.1.254) 56(84) bytes of data.
64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=5.59 ms

``````
scratchy@scratchy-laptop:~$ ping google.fr
PING google.fr (66.249.92.104) 56(84) bytes of data.
^C
--- google.fr ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

``````
scratchy@scratchy-laptop:~$ tracepath 192.168.1.254
 1:  scratchy-laptop.lan (192.168.1.3)                      0.157ms pmtu 1500
 1:  no reply
 2:  no reply
^C
``````
scratchy@scratchy-laptop:~$ tracepath google.fr
 1:  scratchy-laptop.lan (192.168.1.3)                      0.926ms pmtu 1500
 1:  no reply

```What's wrong ? =S

Thanks !

---

### Post by Iowan on 2010-07-23
have you tried pinging Internet by IP address?

---

### Post by mentalow on 2010-07-23
Yes I tried that already. Nothing.

---

### Post by dca on 2010-07-23
Everything looks right.  How's it set-up?  Cable modem -> Router -> Laptop/PC?
 
...then again why does both eth0 & 1 indicate "Interruption: 17" down below?  Also, was NIC put into 'Promiscuous' mode by issuing a 'tcpdump' command?

---

### Post by mentalow on 2010-07-23
Hey.

Sorry for inconvenience.

My GF just arrived at home, tried to connect to the network with her comp ( Ubuntu fresh install too ), it worked, tried, worked for me too. Dunno what happened.

Its okay.

Thanks guyz !

---

### Post by dca on 2010-07-23
Must've been something to do w/ last line of each interface indicating 'Interruption: 17'...
 
 Mine say 'Interrupt: 11' on eth0 and 'Interrupt: 13' on eth1 for second NIC...  Laptop doesn't display either...

---

### Post by Iowan on 2010-07-23
Give it a couple of days to make sure it **stays** fixed. If it does, you can mark the thread [SOLVED] (under Thread Tools). :)

---

### Post by kharoon on 2010-07-25
hey guys i have the same problem with Ubuntu 10.04
when i use freedom proxy server i can access Internet but no direct Internet connection in Mozilla neither pidgin , update manager , ...

plz help me ...

---

