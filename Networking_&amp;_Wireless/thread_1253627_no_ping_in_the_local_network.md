---
title: "no ping in the local network"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by jrev on 2009-08-30
Hi all,

My local network is out of order.
My main PC sharing the dial-up connection cannot ping the other PC's. 
the result of the "ifconfig" command is here :

jean@jean:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:db:5e:3d:07  
 
->  the second line is missing 

          adr inet6: fe80::219:dbff:fe5e:3d07/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:468 (468.0 B)
          Interruption:18 Adresse de base:0xe000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:2002 erreurs:0 :0 overruns:0 frame:0
          TX packets:2002 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:100100 (97.7 KB) Octets transmis:100100 (97.7 KB)


Any idea where I should look to understand this fault ? I am on ubuntu 8.04 and have only the Etho module on the motherboard of this computer.

Thanks 

:lolflag:

---

### Post by Iowan on 2009-08-30
That second line should have the IP address. Should the machine get it via DHCP or is it (supposed to be) a static address?

---

### Post by jrev on 2009-08-30
> **Iowan said:**
> That second line should have the IP address. Should the machine get it via DHCP or is it (supposed to be) a static address?

It is a static address 192.168.0.1 

If I change this computer for another I got the same answer to the "ifconfig"
So the fault isn't in the Etho :)

---

### Post by jrev on 2009-08-31
up please :/

---

### Post by Iowan on 2009-08-31
> **jrev said:**
> If I change this computer for another I got the same answer to the "ifconfig"
So the fault isn't in the Etho :)Sorry, I'm confused...
You have another computer with the same IP address???

---

### Post by jrev on 2009-09-01
I have a local network of 3 computers which share a dial-up connection (external modem 56k) 
The main computer ISC is on Ubuntu 8.04

If I change that computer with a computer on Ubuntu 9.04, this new computer cannot connect to the net and this is the start of all my troubles.

My question : what can I do to have this computer connecting ? 

I have downloaded the following packages :

[http://www.zimagez.com/zimage/capture-basdebit904.php](http://www.zimagez.com/zimage/capture-basdebit904.php)

Thanks for your help

---

