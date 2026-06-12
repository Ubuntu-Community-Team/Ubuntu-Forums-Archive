---
title: "Problem with two computers."
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by tomczyk85 on 2006-04-15
Computer A (eth0 -internet ,eth1-LAN) 
Computer B(eth0 -get internet fromm LAN) 
My configuration is:

**Computer A (server pentium 200Mhz):**

#konfiguracja serwera dhcp

authoritative;
#ddns-update-style none;
subnet 192.168.1.0 netmask 255.255.255.0 {
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
option domain-name-servers 192.168.1.0, 192.168.1.1, 85.128.39.1, 85.128.69.193;
option domain-name "tomczyk.net";

#dla obcych
#range 192.168.1.128 192.168.1.140;

#dla znanych
host xp{
hardware ethernet 00:50:8D:ED:16:8E;-this is MAC of computer B
fixed-address 192.168.1.6;
}
#itd

}

#################################
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#Realtek net przez dhcp od ISP
auto eth0
iface eth0 inet dhcp
hwaddress ether 00:50:8D:ED:16:8F

#3com na ktorym udostepniam neta
auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
hwaddress ether 00:0A:5E:55:31:36
###################################
Skrypt called QWE is sharing internet use IPTABLES
#!/bin/bash   
iptables -I FORWARD -s 192.168.1.0/24 -j ACCEPT
iptables -I FORWARD -d 192.168.1.0/24 -j ACCEPT

iptables -I INPUT -s 192.168.1.0/24 -j ACCEPT
iptables -I INPUT -d 192.168.1.0/24 -j ACCEPT

iptables -t nat -I POSTROUTING -s 192.168.1.0/24 -j SNAT --to-source 85.128.39.191 

#DNSY netpartnera 85.128.39.1 85.128.69.193
####################################

**Komputer B: (where is Windows Xp)**
Auto IP  :
Auto DNS :
When I make this on computer A:
1.I lunch scrypt QWE.
2.I lunch DHCP server /etc/init.d/dhcp restart

On computer B I get:
IP 192.168.1.6
Mask: 255.255.255.0
Gateway 192.168.1.1
Domain tomczyk.net

Every thing is okay on coumputer B but i don't have internet there. I can ping my default gateway and public IP computer A.I have internet on computer A.Why I **don't have** internet on coumputer B!!!. 
I use Hub to connect both computer. Please give some advice or tips what i have to do to share this internet on secend computer.

PS. I know that my english is not good but i tray explain this problem very good.

---

### Post by mips on 2006-04-15
What is the subnet/IP information for eth0 on Computer A ???

---

### Post by totalllama on 2006-04-15
Sounds like a DNS problem if you can ping a public IP.

---

### Post by tomczyk85 on 2006-04-15
[QUOTE=mips]What is the subnet/IP information for eth0 on Computer A ???[/QUOTE]

For eth0 on Computer A:
IP 85.128.39.191 -public IP frommy ISP
Mask 255.255.255.0
Gateway 85.128.39.191

> Sounds like a DNS problem if you can ping a public IP.
I can ping **only my public IP** which I get from my ISP (ping from computer B to computer A).

I have installed DNS forward and IP Masquarade. I think that DNS can be problem. How can I check this and what can I do for resolv this problem. If U want some more information plz write i will paste here this information.

---

### Post by mips on 2006-04-16
On both PC's
1. Please post output of **ifconfig eth[COLOR="Red"]x[/COLOR]** where x = number
2. Please post output of **route -n**
3. Please post output of **cat /etc/resolv.conf**
4. Please post output of **cat /etc/network/interfaces**

---

### Post by tomczyk85 on 2006-04-16
[QUOTE=mips]On both PC's
1. Please post output of **ifconfig eth[COLOR="Red"]x[/COLOR]** where x = number
2. Please post output of **route -n**
3. Please post output of **cat /etc/resolv.conf**
4. Please post output of **cat /etc/network/interfaces**[/QUOTE]

**Computer A**
***ifconfig***
```
eth0      Link encap:Ethernet  HWaddr 00:50:8D:ED:16:8F  
          inet addr:85.128.39.191  Bcast:85.128.39.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:feed:168f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3485 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1811 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4626467 (4.4 MiB)  TX bytes:129230 (126.2 KiB)
          Interrupt:11 Base address:0xf200 

eth1      Link encap:Ethernet  HWaddr 00:0A:5E:55:31:36  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:5eff:fe55:3136/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:378 (378.0 b)
          Interrupt:10 Base address:0xf300 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
**route -n**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
85.128.39.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         85.128.39.1     0.0.0.0         UG    0      0        0 eth0
```
**cat /etc/resolv.conf**
```
search npgo.pl
nameserver 85.128.39.1
nameserver 85.128.69.193
```
**cat /etc/network/interfaces**
```
# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

#Realtek net przez dhcp od ISP
auto eth0
iface eth0 inet dhcp
hwaddress ether 00:50:8D:ED:16:8F

#3com na ktorym udostepniam neta
auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 85.128.39.1
hwaddress ether 00:0A:5E:55:31:36
```


**Computer B**
***ifconfig***
```
eth0      Link encap:Ethernet  HWaddr 00:50:8D:ED:16:8E  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:feed:168e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2991 (2.9 KiB)  TX bytes:8572 (8.3 KiB)
          Interrupt:22 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1211 (1.1 KiB)  TX bytes:1211 (1.1 KiB)
```
**route -n**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```
**cat /etc/resolv.conf**
```
search tomczyk.net
nameserver 192.168.1.0
nameserver 192.168.1.1
nameserver 85.128.39.1
nameserver 85.128.69.193
```
**cat /etc/network/interfaces**
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface

auto eth0
iface eth0 inet dhcp
hwaddress ether 00:50:8D:ED:16:8E
```

---

### Post by mips on 2006-04-16
Your A computers gateway for eth1 points to 85.128.39.1 which technically speaking is not correct as it should point to the next hop address/interface which is eth0 but it usually works. Try using 85.128.69.193 or eth0 , I assume this address never changes ???

For computer B try removing the Private addresses in resolv.conf and only leave the public address nameservers there. Also make the search domain the same as for computer A.

Why do you specify your MAC addresses in the config files ?

Besides the above I do not see anything wrong with your config.

Tried disabling IPv6 ?

---

### Post by tomczyk85 on 2006-04-16
[QUOTE=mips]Your A computers gateway for eth1 points to 85.128.39.1 which technically speaking is not correct as it should point to the next hop address/interface which is eth0 but it usually works. Try using 85.128.69.193 or eth0 , I assume this address never changes ???

```
Right this address is static. I chaned the gateway eth1 to 85.128.69.193.
85.128.69.193 --this is addres of DNS my ISP.
```

For computer B try removing the Private addresses in resolv.conf and only leave the public address nameservers there. Also make the search domain the same as for computer A.

```
Now in resolv.conf are only these address 85.128.39.1, 85.128.69.193
Domain are the same as my ISP - npgo.pl
option domain-name "npg.pl";
```


Why do you specify your MAC addresses in the config files ?

```
I have internet depend from my MAC. My ISP have only this 
MAC HWaddr **00:50:8D:ED:16:8F**
I have to change MACs becouse I want internet om Computer B but this original MAC is only on integrated eth0 in Computer B
Computer A
eth0 original MAC "I don't remember" change **00:50:8D:ED:16:8F**
eth1 original MAC 00:0A:5E:55:31:36
Computer B
eth0 original MAC **00:50:8D:ED:16:8F** change 00:50:8D:ED:16:8**E**
``` -only last char is chaned

Besides the above I do not see anything wrong with your config.
```
I thing that my script is wrong. I don't know well iptables, but I think that this script is bad.
###################################
Skrypt called QWE is sharing internet use IPTABLES
#!/bin/bash
iptables -I FORWARD -s 192.168.1.0/24 -j ACCEPT
iptables -I FORWARD -d 192.168.1.0/24 -j ACCEPT

iptables -I INPUT -s 192.168.1.0/24 -j ACCEPT
iptables -I INPUT -d 192.168.1.0/24 -j ACCEPT

iptables -t nat -I POSTROUTING -s 192.168.1.0/24 -j SNAT --to-source 85.128.39.191

#DNSY netpartnera 85.128.39.1 85.128.69.193
####################################
```


Tried disabling IPv6 ?[/QUOTE]
I still don't have internet on Computer B.
I don't what is IPv6 but i try search in google. How can I disable this ? Is IPv6 very importent for my network. I think that me script can be more importent than IPv6.

Somebody know what is TTL ? How can I add this function to my Ubuntu.

---

### Post by mips on 2006-04-17
> Right this address is static. I chaned the gateway eth1 to 85.128.69.193.
85.128.69.193 --this is addres of DNS my ISP.

Sorry I don't understand how can you allocate the ISPs DNS server address to you PC.

> I don't what is IPv6 but i try search in google. How can I disable this ? Is IPv6 very importent for my network. I think that me script can be more importent than IPv6.

```
sudo mv /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko /lib/modules/$(uname -r)/kernel/net/ipv6/ipv6.ko.bak
sudo depmod -a
```

Somebody know what is TTL ? How can I add this function to my Ubuntu.

TTL stands for "Time To Live" basically indicates the maximum life of a data packet before it gets discarded/dropped. Unfortunately I don't know where to change it.

Have you tried simply using Firestarter ?

---

### Post by tomczyk85 on 2006-04-17
.

---

### Post by tomczyk85 on 2006-04-17
[QUOTE=mips]Sorry I don't understand how can you allocate the ISPs DNS server address to you PC.

```
So which address is correct?
```


TTL stands for "Time To Live" basically indicates the maximum life of a data packet before it gets discarded/dropped. Unfortunately I don't know where to change it.

TTL i can chaned, but ...
```
iptables -t mangle -A PREROUTING -i eth0 -j TTL --ttl-inc 1
iptables -t mangle -A OUTPUT -o eth0 -j TTL --ttl-set 128
iptables -t mangle -A FORWARD -o eth0 -j TTL --ttl-set 128
```
Only for use mangle i have tu pached kernel and iptables. Can U do that??

Have you tried simply using Firestarter ?

```
I don't tried Firestarter. I think this can't help me.
```
[/QUOTE]
I work on this TTL 24 H Somebody have good HOW-TO chaned TTL.

---

### Post by mips on 2006-04-17
Could I advise you to disable any firewalls and just to get the connection to work.

Once you have the connection working you can use fwbuilder to setup the firewall part.

---

### Post by tomczyk85 on 2006-04-17
[QUOTE=mips]Could I advise you to disable any firewalls and just to get the connection to work.

Once you have the connection working you can use fwbuilder to setup the firewall part.[/QUOTE]

Without firewall I don't have connection to. I need inc TTL +1 Look this.
In console: ```
tcpdump -nevi eth0
```

```
2:56:30.770224 00:90:27:2c:20:5c > 00:15:f2:b1:65:c2, ethertype IPv4 (0x0800), length 62: (tos 0x0, **ttl   1**, id 30467, offset 0, flags [DF], proto: TCP (6), length: 48) 217.197.67.129.3073 > 85.128.39.245.32459: S, cksum 0x7fd4 (correct), 86629800:86629800(0) win 64240 <mss 1460,nop,nop,sackOK>
22:56:30.885662 00:90:27:2c:20:5c > 00:15:f2:b1:65:c2, ethertype IPv4 (0x0800), length 143: (tos 0x0, **ttl   1**, id 24289, offset 0, flags [none], proto: UDP (17), length: 129) 88.7.151.110.10020 > 85.128.39.245.32459: UDP, length 101
22:56:30.930713 00:90:27:2c:20:5c > 08:00:46:81:c7:2f, ethertype IPv4 (0x0800), length 62: (tos 0x0, **ttl   1**, id 13672, offset 0, flags [DF], proto: TCP (6), length: 48) 81.210.71.10.2391 > 85.128.39.164.4662: S, cksum 0xb30d (correct), 2160114515:2160114515(0) win 25200 <mss 1460,nop,nop,sackOK>
```

---

