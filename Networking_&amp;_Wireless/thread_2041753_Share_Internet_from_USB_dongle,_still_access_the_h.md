---
title: "Share Internet from USB dongle, still access the home network"
date: 2012-08-13
forum: Networking &amp; Wireless
---

### Post by Younio on 2012-08-13
[FONT="Verdana"]Hello people,

I tried to deal with this problem myself for quite a while , but I failed, nothing helped, so I am here for your help.

I need to share Internet from WIMAX dongle and still be able to access the home network from the same computer. 
Here is the scheme how it is right now.

[img]http://foto.terpe.lt/inkelti/20120813/i90_Untitled.png[/img]

The red line is on the different sub-net.

I use Lubuntu 12.04
Basically what I did was:
1. Automatically connected to Eth0
2. Shared my connection trough Eth1
3. Connected Eth1 to router Internet socket
4. Connected router LAN to Eth2

The thing is that my configuration works for a while and then crashes. 
Usually all of the computers connected to router works fine and can access 
the internet until I connect a cable from router LAN to main computer Eth2 (to acess the home network). 
Then sometimes, for a while I can access the internet and home network too. 
But after some time none of the computers nor the router can access the internet.

In my opinion what I need is to bridge Eth0 and Eth1. And make the main computer access the internet from Eth2. I tried to do that using brctl, but I failed.  Maybe I am missing some steps.

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:42:02:a8:c8  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:42ff:fe02:a8c8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:136440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:112833676 (112.8 MB)  TX bytes:11318725 (11.3 MB)

eth2      Link encap:Ethernet  HWaddr 00:0c:6e:96:ee:db  
          inet addr:192.168.1.80  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:6eff:fe96:eedb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1341 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:241311 (241.3 KB)
          Interrupt:23 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:14:78:7b:fc:38  
          inet addr:10.42.0.1  Bcast:10.42.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:78ff:fe7b:fc38/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:19130 (19.1 KB)
          Interrupt:18 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:103376 errors:0 dropped:0 overruns:0 frame:0
          TX packets:103376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16875707 (16.8 MB)  TX bytes:16875707 (16.8 MB)

```


So I would be glad if anyone could help me.

[COLOR="RoyalBlue"]EDIT:[/COLOR]

After a 5 days I finally found the solution [HERE]("http://www.wmaus.net/wordpress/?p=953")

I just had to change the IP addresses.

I looked at my connection properties when connected directly to WIMAX USB dongle,
And they were:

IP address:   192.168.0.8
Gateway:      192.168.0.1
Network mask: 255.255.255.0
Broadcast:    192.168.0.252

And accordingly changed the bridge properties to the following: 

(this is my /etc/network/interfaces)

```
auto lo
iface lo inet loopback

auto br0 
iface br0 inet static
address 192.168.0.8
netmask 255.255.255.0
network 192.168.0.8
broadcast 192.168.0.252
gateway 192.168.0.1
bridge_ports eth0 eth1
```

Now when I restart the computer in Network manager the cards Eth0 and Eth1 
are being displayed as unusable, And trough Eth2 I can easily connect to my router using static or DHCP.

Obviously the internet works on router and computer
as well as the other computers connected to the router, as it is displayed on my scheme above.

I hope this will help somebody in the future. :7

Kindly,

Younio[/FONT]

---

### Post by Younio on 2012-08-14
[COLOR="Silver"]Bump[/COLOR]

---

### Post by Younio on 2012-08-16
[COLOR="SlateGray"]Bump Again[/COLOR]

---

### Post by Younio on 2012-08-16
[COLOR="Silver"]The Last Desperate [/COLOR][COLOR="DimGray"]Bump[/COLOR]

---

### Post by Younio on 2012-08-19
Bump for those who need help

---

