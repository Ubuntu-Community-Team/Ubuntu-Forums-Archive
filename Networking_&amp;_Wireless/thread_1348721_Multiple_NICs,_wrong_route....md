---
title: "Multiple NICs, wrong route... ?"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by Djense on 2009-12-07
Hi,

I have 2 NICs in my computer and a lot of trouble to set it right...
I found some threads dealing with the same issue, but still could not find the solution to my problem.

One of the interface (eth0) goes to a private network connected to the internet. I get my IP through DHCP on this 192.168.40.x network.

The other one (eth1) has a static IP : 192.168.0.10 and not connected to the internet.

When I reboot, I cannot access the internet.

I am a bit confused between the configuration in /etc/network/interfaces and /etc/NetworkManager/system-connections/ (not sure really which one is being used).

Here are some outputs :
[FONT=Courier New]$ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:4d:7c:b7  
          inet addr:192.168.40.185  Bcast:192.168.40.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe4d:7cb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15969 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17895580 (17.8 MB)  TX bytes:3377833 (3.3 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:6b:bc:98:40  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::222:6bff:febc:9840/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21827 (21.8 KB)  TX bytes:21827 (21.8 KB)[/FONT]

[FONT=Courier New]$cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
address 192.168.0.10
netmask 255.255.255.0

auto eth0
iface eth0 inet dhcp

up route add default dev eth0[/FONT]
[FONT=Courier New]
$route -n
[/FONT][FONT=Courier New]Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.40.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 eth0
0.0.0.0         192.168.40.1    0.0.0.0         UG    100    0        0 eth0[/FONT]

After I run 'sudo dhclient eth0' then I can recover my internet connection, the route output is changed like this :
[FONT=Courier New]$route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.40.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.40.1    0.0.0.0         UG    0      0        0 eth0[/FONT]

But every time I reboot, I have to do that.

Thanks for any help...

Matt

---

### Post by lloyd_b on 2009-12-07
You've got conflicting netmasks for the two interfaces.

First question: Does the network on eth1 *have* to be 192.168.0.x?  If you could move it to 192.168.1.x, and make the appropriate changes in your configuration, then the problems should disappear.

What's happening is that it sees the route for 192.168.0.x on eth1, and with a netmask of 255.255.255.0, assumes that this is the correct interface to reach the gateway at 192.168.40.1.  When you run the 'dhclient' command, it corrects this error, forcing it to use eth0 to reach the gateway.

Other than moving the network, try changing the 'netmask' entry for eth1 to "255.255.255.224" (rather than 255.255.255.0).  Be advised that this will limit your access on eth1 to the range 192.168.0.1 through 192.168.0.31, so this may or may not be an option for you.

Lloyd B.

---

### Post by Djense on 2009-12-07
Hi Lloyd,

Thanks for the help.
I changed the local network to 192.168.1.x from 192.168.0.x and still see the same issue... ?

I am not sure if that has anything to do with my problem, but I don't understand where this route to 169.254.x.x come from.

Since I still don't know if one is taking precedence on the other, I changed both network configuration locations in /etc

[FONT=Courier New]$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.40.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 eth0
0.0.0.0         192.168.40.1    0.0.0.0         UG    100    0        0 eth0
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:4d:7c:b7  
          inet addr:192.168.40.185  Bcast:192.168.40.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c9ff:fe4d:7cb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:344 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44739 (44.7 KB)  TX bytes:9606 (9.6 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:22:6b:bc:98:40  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:6bff:febc:9840/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8620 (8.6 KB)  TX bytes:8620 (8.6 KB)
[/FONT]

---

### Post by lloyd_b on 2009-12-07
Okay, suggestion ```
sudo apt-get remove network-manager
```:D
Personally, I *hate* network manager, but then I'm perfectly comfortable tweaking /etc/network/interfaces to suit my taste.

The problem is this route:```
0.0.0.0 0.0.0.0 0.0.0.0 U 0 0 0 eth0
```This is telling the system that it can send just about anything out on eth0 without a gateway.  I have no clue where it's coming from (though I suspect Network Manager, of course).

I wouldn't worry about that 169.254.x.x route - it's pretty restricted (with a netmask 255.255.0.0, it'll only affect addresses that start with 169.254).  If you run 'route' without the "-n", you'll see it listed as "link-local", so I assume it's something that needs to be there.

Lloyd B.

---

### Post by Djense on 2009-12-07
I removed network manager
To remove that route, I commented out that line in /etc/network/interfaces
[FONT=Courier New]up route add default dev eth0[/FONT]

Works now.

Thanks !

---

