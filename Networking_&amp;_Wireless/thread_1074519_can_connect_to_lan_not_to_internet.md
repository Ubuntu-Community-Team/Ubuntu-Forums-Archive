---
title: "can connect to lan not to internet"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by let_there_be_linux on 2009-02-19
hi,
im running ubuntuserver with gnome-desktop gui on a asus m2n sli-deluxe motherboard with 2 LAN ports, at first i could connect to the local servers on my LAN thu port1 and to internet thu port2 but not to the other. now i can only connect to the local network on one port, and the other does nothing anymore, i think it must be a setting, but which one? the dns is correct, i compared it with the dns on another machine on the same network that does work.

---

### Post by superprash2003 on 2009-02-19
are both getting an ip address??have you tried bringing down one interface?? are both on the same subnet?

---

### Post by let_there_be_linux on 2009-02-19
> superprash2003  	
Re: can connect to lan not to internet
are both getting an ip address??have you tried bringing down one interface?? are both on the same subnet? 

im not sure about the ip, id have to check tomorrow (its a server at work)if with bringing down you mean disable, then yes i have tried that, if you meant something else please clarify, and i connected both ports to the same switch, so yes they have the same subnet.
if it works with 2 than its ok, but ideally it should work on one.

---

### Post by let_there_be_linux on 2009-02-20
heres the terminal entry for ifconfig:

> 
user@ubuntu-server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:fc:a4:05:10  
          inet addr:192.168.1.120  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fea4:510/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:219 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27029 (26.3 KB)  TX bytes:17458 (17.0 KB)

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:a4:13:79  
          inet6 addr: fe80::21b:fcff:fea4:1379/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48761 (47.6 KB)  TX bytes:12053 (11.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31445 (30.7 KB)  TX bytes:31445 (30.7 KB)

peth0     Link encap:Ethernet  HWaddr 00:1b:fc:a4:05:10  
          inet addr:192.168.1.125  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fea4:510/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:265 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41367 (40.3 KB)  TX bytes:32897 (32.1 KB)
          Interrupt:17 Base address:0x4000 


im not sure what lo and peth0 are. any help on this problem would be greatly appreciated (boss is getting impatient)

---

### Post by superprash2003 on 2009-02-20
port 1 and port 2 are connected to same switch?? they have same gateways??

---

### Post by let_there_be_linux on 2009-02-20
yes, both ports are connected to the same swich

---

### Post by let_there_be_linux on 2009-02-21
does anyone have any idea what it could be?

---

### Post by superprash2003 on 2009-02-21
why do you need two interfaces connecting to the same place??

---

### Post by Iowan on 2009-02-21
> **let_there_be_linux said:**
> im not sure what lo and peth0 are. **lo** is loopback device - that's normal. I've never seen peth0 before - but **lshw -C network**
might give some idea what hardware device is connected to the alias.

Broadcast address  of 255.255.255.255 for 192.168.1 subnet seems a li'l strange.

---

### Post by let_there_be_linux on 2009-02-22
> **superprash2003 said:**
> why do you need two interfaces connecting to the same place??

if you read the original problem you will find that the one connected to our LAN server, the other connects to the internet, both on the same swich, but now the internet doesnt work anymore, other computers on the network can connect to the internet

---

### Post by superprash2003 on 2009-02-22
what is eth1 connected to?? and as lowan mentioned.. check out broadcast address.. have you manually entered those?? or via DHCP?

---

### Post by let_there_be_linux on 2009-02-26
i decided it was easier to just reinstall the whole thing, as it had worked in the beginning and went wrong before i got the chance to really use the server, its all working as it should now.

---

