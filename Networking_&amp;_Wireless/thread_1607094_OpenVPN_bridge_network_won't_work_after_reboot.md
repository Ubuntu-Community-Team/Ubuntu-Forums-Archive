---
title: "OpenVPN bridge network won't work after reboot"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by Bacaryu on 2010-10-27
Hello,

I followed this tutorial => [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)
I'm working on ubuntu 10.10 OS

So everything is ok when i start the tutorial with my interface on:

auto lo 
iface lo inet loopback

Then I have to change the interfaces with

auto lo br0
iface lo inet loopback

iface br0 inet static 
  address 192.168.1.10 
  netmask 255.255.255.0
  gateway 192.168.1.1
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down 

if i do a network restart => the OVPN (already configured) works (tested connection from outside = ok) ! 
But when I reboot my ubuntu and start openvpn I can't acces it from the internet anymore !! also no ssh connection from outside
I still can acces the server over ssh on the local network.
It seems like the br0 is not bridged with the eth0 card anymore!

The only way I can make it work again is by setting the interfaces back to  

auto lo 
iface lo inet loopback

>> then reboot
and after that put back the br0 settings in the interfaces en restart the network. 

I know it seems complicated but its hard to explain.

---

### Post by Bacaryu on 2010-10-27
It seems that this guy had the same issue but he didn't knew that his server was not online.

[http://ubuntuforums.org/showthread.php?t=1584125&highlight=openvpn](http://ubuntuforums.org/showthread.php?t=1584125&highlight=openvpn)

---

### Post by ryanczak on 2010-10-27
You need to have something in your interfaces file that joins the tap interface to eth0.

Try adding the following under iface br0 inet static

```

pre-up /usr/sbin/openvpn --mktun --dev tap0

```

and change

```
bridge_ports eth0
```

to

```
bridge_ports eth0 tap0
```

and make sure openvpn is setup to use tap0

---

### Post by Bacaryu on 2010-10-27
I did what you told me but I still can't connect from outside.

[PHP]auto lo br0
iface lo inet loopback

iface br0 inet static
pre-up /usr/sbin/openvpn --mktun --dev tap0
address 192.168.1.113
netmask 255.255.255.0
gateway 192.168.1.1
bridge_ports eth0     #here i removed the tap0 because when i start the openvpn he cannot use tap0 (in use)


iface eth0 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down
[/PHP]I can connect to ssh on 192.168.1.113 on my local network (weird) but i cannot connect from outside thru my dns or ip adress (forwarded DMZ host) 

I can connect to this dns when I reset my interfaces to normal.

my problem is only that its not accesible from the internet

[PHP]br0       Link encap:Ethernet  HWaddr 00:11:09:da:fe:67  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:feda:fe67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1464785 (1.4 MB)  TX bytes:813319 (813.3 KB)

eth0      Link encap:Ethernet  HWaddr 00:11:09:da:fe:67  
          inet6 addr: fe80::211:9ff:feda:fe67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3175 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1579870 (1.5 MB)  TX bytes:813838 (813.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1704 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1704 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:266427 (266.4 KB)  TX bytes:266427 (266.4 KB)

ra0       Link encap:Ethernet  HWaddr 00:22:f7:02:3b:d4  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:f7ff:fe02:3bd4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5229 errors:0 dropped:0 overruns:0 frame:0
          TX packets:313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1253574 (1.2 MB)  TX bytes:17980 (17.9 KB)
          Interrupt:17 

tap0      Link encap:Ethernet  HWaddr 4e:c7:0b:86:2f:df  
          inet6 addr: fe80::4cc7:bff:fe86:2fdf/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:2178 (2.1 KB)


[/PHP]

---

### Post by Bacaryu on 2010-10-27
OK I Solved it

wasn't an easy one :-)

I found in my router dhcp log 

Tue, 26 Oct 2010 23:10:50 sending OFFER to 255.255.255.255 with 192.168.1.113Tue, 26 Oct 2010 23:10:50 received REQUEST from 00:11:09:DA:FE:67

so I decided to put the br0 to 255.255.255.255  and it works !!

I don't know how it comes, maybe someone can explain it for me ? 

Anyway the topic can be marked as SOLVED

---

