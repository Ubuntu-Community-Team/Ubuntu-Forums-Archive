---
title: "Network Static IP unbuntu 9.10 Server"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by vipswiss on 2010-04-04
Hello guys I am a newbe in Linux trying to set up a server unbuntu 9.10 I am trying to set up stutic ip on eth0. I cant figure out what might be the problem 

here is my /etc/network/interfaces

> # This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5) 
auto lo eth0 
iface lo inet loopback 
 
# The primary network interface 
iface eth0 inet static 
        address 192.168.1.100 
        netmask 255.255.255.0 
        broadcast 192.168.1.255 
        network 192.168.1.0 
        gateway 192.168.1.1 

now when i this is what i get 
> root@jphost:~# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                         
SIOCDELRT: No such process


Now on the localhost and local adress it works but i can't conect to the network 

> root@jphost:~# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:0b:db:be:82:f0  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:febe:82f0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10545 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4678 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6426645 (6.4 MB)  TX bytes:798306 (798.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7653 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1929929 (1.9 MB)  TX bytes:1929929 (1.9 MB)

virbr0    Link encap:Ethernet  HWaddr ea:42:e5:9c:6f:0c  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:14994 (14.9 KB)

Please help I have read manuals tried thing but still please point me in the right detection 
):P

---

### Post by gzarkadas on 2010-04-04
Are you trying to setup a bridge? what is the network topology?

Some relevant guides:
[http://tldp.org/LDP/nag2/index.html](http://tldp.org/LDP/nag2/index.html) (Linux Network Administrator Guide)
[http://www.tldp.org/HOWTO/html_single/Ethernet-Bridge-netfilter-HOWTO](http://www.tldp.org/HOWTO/html_single/Ethernet-Bridge-netfilter-HOWTO)
[http://www.tldp.org/HOWTO/html_single/IP-Masquerade-HOWTO](http://www.tldp.org/HOWTO/html_single/IP-Masquerade-HOWTO)

---

### Post by vipswiss on 2010-04-04
I think it is a mesh or a star not shure my main line is connected to router and from router it conects to boxes hover i used another router to work as splitter to connect 2 computers and one of them I am trying to use as a server. 

1. Here is the current situation my /etc/network/interfaces

> # This file describes the network interfaces available on your system 
# and how to activate them. For more information, see interfaces(5) 
auto lo eth0 
iface lo inet loopback 
 
# The primary network interface 
iface eth0 inet static 
        address 192.168.1.100 
        netmask 255.255.255.0 
        broadcast 192.168.1.255 
        network 192.168.1.0 
        gateway 192.168.1.1                      With static configuration only the localhost is working when chenged to dhcp i can ping google.com but when I try to ping a local address from another comp on my home network the is no response. 

My gole is to set up a server so I can host content websites.

The main router that is conected to company box is WRT54GS with gateway 192.168.1.1 and the router that works as a spliter is on a sistem I am trying to set up is [FONT=Arial][SIZE=2]DI-514 I don't know if it maters for configuration[/SIZE][/FONT][B][FONT=Arial][SIZE=2]
[/SIZE][/FONT][/B]

---

### Post by chili555 on 2010-04-04
Please try this:```
auto lo eth0
iface lo inet loopback

# The primary network interface
[COLOR="Red"]auto eth0[/COLOR]
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
[COLOR="Red"]#[/COLOR]broadcast 192.168.1.255
[COLOR="Red"]#[/COLOR]network 192.168.1.0
gateway 192.168.1.1 
```Also, make sure you have populated */etc/resolv.conf*.

---

### Post by vipswiss on 2010-04-04
I have edited  /etc/network/interfaces the localhost stopped working 

ifconfig
   	 	 	 	 	 	  > eth0      Link encap:Ethernet  HWaddr 00:0b:db:be:82:f0  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::20b:dbff:febe:82f0/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:521 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:176756 (176.7 KB)  TX bytes:7526 (7.5 KB) 
          Interrupt:17 

virbr0    Link encap:Ethernet  HWaddr de:97:f0:48:03:73  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:3884 (3.8 KB)                           


 I hade to swich back to dhcp and reboot the system checked  /etc/resolv.conf - form dhcp conf 
nameserver 192.168.0.1

---

### Post by chili555 on 2010-04-04
> nameserver 192.168.[COLOR="Red"]0[/COLOR].1How is this consistent with this?> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5)
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.[COLOR="Red"]1[/COLOR].1 Let's tweak once again:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5)
auto lo 
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1 
```Is your network at x.0.1 or at x.1.1?

---

### Post by gzarkadas on 2010-04-04
Please post:

The output of **route** command in your machine.
The contents of your machine's /etc/hosts
The IP addresses of the other machines you want to reach.
The output of running **ping** on each of the machines you want to reach.

---

### Post by vipswiss on 2010-04-04
Thank you very much  chili555  I have understood my mistake gateway 192.168.1.1 - the adress of the main router from thir I have used a DI-514 an Wireless Broadband Router with an adress 192.168.0.1 as a splitter form my comp and server that was the problem I was trying to bypass to the main gatewy :) thank you chili555 
Ok now I can ping -c 3 google.com and my local adress

> > route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0


127.0.0.1    localhost
127.0.1.1    jphost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhostsOk no I have to open conection so I can ping my adress form the outside so server will be avalable.
I can ping 192.168.0.100 form the comp that is conected to the same router as server but I cant from other muchines.

---

### Post by gzarkadas on 2010-04-04
This is probably because the other machines are in a different subnet and/or you need to set a rule to your router to route traffic between the subnets. Post the same information (routing table, IP address, etc) for a machine that _cannot_ ping to your server, to trace this down.

---

### Post by vipswiss on 2010-04-04
Yes you right thank you very much guys for your help 
gzarkadas
chili555
:popcorn:

---

