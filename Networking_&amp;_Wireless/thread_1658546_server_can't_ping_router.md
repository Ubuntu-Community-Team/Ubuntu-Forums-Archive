---
title: "server can't ping router"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by mbvpixies78 on 2011-01-02
Hello,

     I'm setting up a home network and trying to set up a Ubuntu Server (10.04) as a samba file server and a web server.

     I installed Ubuntu 10.04 Server ](*,) and the automatic network configuration during installation failed.  I can't ping my router and have read a lot of online articles and still I can't fix this problem.

I've looked into host.conf, networks, interfaces, hosts and resolv.conf and either my settings are wrong or it's something else.  I have a Win7 computer connected to same router and DSL modem and it works fine (*edit:  most of the time---  see below)*.

More information:

*ifconfig shows eth0 is broadcasting but without an IP address
*route shows an empty routing table

```

**sudo route add default gw 192.168.1.254** doesn't work:
SIOCADDRT:  No such process

``````

**sudo /etc/init.d/networking restart** doesn't work:
$sudo /etc/init.d/networking restart
Listening on LPF eth2/<MAC address>
Sending on LPF eth2/<MAC address>
Sending on socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 15
...  and it keeps doing this a few more times and then:
No DHCPOFFERS received no working leases in persistent database--sleeping


[code]
**/etc/host.conf**

#The order line is only used by old versions of the C library
order hosts, bind

``````

**/etc/networks**

default      0.0.0.0
loopback   127.0.0.0
link-local   169.254.0.0
localnet     192.168.0.0

``````

**/etc/network/interfaces**

#This file describes the network interfaces on your system and how
#to activate them.  For more info see interfaces(5)

#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
iface eth0 inet dhcp
#The following is all commented out...  uncomment gateway, broadcast??
#address      192.168.0.101
#netmask     255.255.255.0
#network      192.168.0.0
#broadcast    192.168.0.255
#gateway      192.168.0.1

#dns-search   seventhring.tzo.net

``````

**/etc/hosts**

127.0.0.1            localhost
192.168.0.101     buddha.seventhring.tzo.net     buddha

#The following lines are desirable for IPV6 capable hosts
(what follows is IPV6 info.  Should I comment it out?

``````

**/etc/resolv.conf**
search seventhring.tzo.net

```Can anyone see any reason why these config files may be preventing me from being able to ping my router, much less have any network access?  Loopback works but that's it.

I greatly appreciate anyone pointing me where to look to fix this.

---

### Post by Iowan on 2011-01-02
The server has only one interface? It looks like eth2 is trying to get DHCP address. 
What are results of **ifconfig -a**. If you want the static address via */etc/network/interfaces*, change it:

```


#This file describes the network interfaces on your system and how
#to activate them.  For more info see interfaces(5)

#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static

address      192.168.0.101
netmask     255.255.255.0
network      192.168.0.0
broadcast    192.168.0.255
gateway      192.168.0.1

dns-search   seventhring.tzo.net
```
Looks like there *might* be some subnet issues - is the router 192.168.0.1 or 192.168.1.254?

---

### Post by mbvpixies78 on 2011-01-09
> **Iowan said:**
> The server has only one interface? It looks like eth2 is trying to get DHCP address. 
What are results of **ifconfig -a**. If you want the static address via */etc/network/interfaces*, change it:

```


#This file describes the network interfaces on your system and how
#to activate them.  For more info see interfaces(5)

#The loopback network interface
auto lo
iface lo inet loopback

#The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static

address      192.168.0.101
netmask     255.255.255.0
network      192.168.0.0
broadcast    192.168.0.255
gateway      192.168.0.1

dns-search   seventhring.tzo.net
```Looks like there *might* be some subnet issues - is the router 192.168.0.1 or 192.168.1.254?

Right now my internet is working, but still a little slow.  I switched PPPoE from the AT&T-provided modem to a 3rd party router which fixed Windows' inability to maintain a stable internet connection.  Of course this being AT&T, I gotta figure this **** out by myself.

In the past I've installed a new wall jack, tried different filters and cables, 2 different modems with and without a router, with and without a switch.  AT&T's modem does NOT like a router or a switch between it and your computer. 
[U]
*Best to limit AT&T's modem's functions to passing PPPoE signals between the CO and your router/computer.  In all situations*[/U].  The hardware is crappier than it used to be and it can't be trusted.

Ok, I'm done ranting.  I hope that helps someone down the line in my situation.  

I really don't know how much that has to do with these problems but I would say quite a bit since my only problem now is somewhat of a lag in loading pages (maybe the router is somehow slowing the signal down.)


Here is my ifconfig -a
```

ifconfig -a
eth0      Link encap:Ethernet  HWaddr ***
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr ***
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe48:b8e7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:601862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:405322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:602074924 (602.0 MB)  TX bytes:37023943 (37.0 MB)
          Interrupt:22 Base address:0x6000 

eth2      Link encap:Ethernet  HWaddr ***
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:605385 errors:0 dropped:0 overruns:0 frame:0
          TX packets:605385 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:493142617 (493.1 MB)  TX bytes:493142617 (493.1 MB)

```

Also, as it's working, here's the new routing table:
```

$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

```

---

### Post by PatchesTheCaveman on 2011-01-10
Have you tried anything other than loading websites to test your connection speed?  If it's just Firefox that's being slow, try disabling IPv6.  There are instructions here:
[http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can?redirectlocale=en-US&redirectslug=Firefox+cannot+load+web+sites+but+other+programs+can#w_ipv6](http://support.mozilla.com/en-US/kb/Firefox%20cannot%20load%20websites%20but%20other%20programs%20can?redirectlocale=en-US&redirectslug=Firefox+cannot+load+web+sites+but+other+programs+can#w_ipv6)

There are a few other instructions on that page on how to improve page loading time as well.

---

