---
title: "Borked network config files"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by quikone8 on 2009-10-23
Back a few releases ago when the Network Manager wasn't working so good, I changed the files that configure the network connections and did not save a backup.  Now it seems that in 9.04 the issue is mostly resolved.  How can I get back to the original files?  I don't want to mess myself up any more than I have already.  I just want to be able to assign static addresses to eth0 and eth1.  The way it is now I cannot modify these at all and to get it running added wired 1 and wired 2.  Now if the server is rebooted the connections go back to eth0 and eth1 which do not work as set.  Can I totally uninstall?  If so, what files should I have available to reinstall since the NM will be down?  Or better yet is there a place that I can get the default files for NM?

---

### Post by dmizer on 2009-10-23
If you are just using wired connections, simply install gnome-network-admin. Then, configure your network via system > administration > network and forget about it.

Why do I recommend gnome-network-admin over NM? From network-manager description:
> NetworkManager attempts to keep an active network connection available at all
times. It is intended only for the desktop use-case, and [B][COLOR="Red"]is not intended for
usage on servers[/COLOR][/B]. The point of NetworkManager is to make networking
configuration and setup as painless and automatic as possible.  If using DHCP,
NetworkManager is _intended_ to replace default routes, obtain IP addresses
from a DHCP server, and change nameservers whenever it sees fit.
If you have gnome-network-manger installed, just uninstall it and use gnome-network-admin instead.

---

### Post by jward3010 on 2009-10-23
Can you even install network manager in Server edition (unless of course you install a desktop package as well)?

---

### Post by dmizer on 2009-10-23
> **jward3010 said:**
> Can you even install network manager in Server edition (unless of course you install a desktop package as well)?

No. And I assume that the OP has indeed installed (or is using) a GUI because otherwise the solution would be a simple edit of /etc/network/interfaces, and the OP wouldn't be having a conflict between eth0/eth1 and wired 1/wired 2.

---

### Post by quikone8 on 2009-10-23
I did what you suggested and have checked etc/network/interfaces.  Both connections are enabled but no connectivity??

---

### Post by dmizer on 2009-10-23
> **quikone8 said:**
> I did what you suggested and have checked etc/network/interfaces.  Both connections are enabled but no connectivity??

Please post the contents of your current /etc/network/interfaces.

Also, please post the output of
```
lshw -C network
```

---

### Post by quikone8 on 2009-10-24
> **dmizer said:**
> Please post the contents of your current /etc/network/interfaces.

Also, please post the output of
```
lshw -C network
```

  *-network               
       description: Ethernet interface
       product: 82541GI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 7
       bus info: pci@0000:0b:07.0
       logical name: eth0
       version: 05
       serial: 00:11:43:ed:56:d7
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=173.160.43.132 latency=32 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Ethernet interface
       product: 82541GI Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:0c:08.0
       logical name: eth1
       version: 05
       serial: 00:11:43:ed:56:d8
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=192.168.1.252 latency=32 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=1GB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fe:d9:11:93:f3:0a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by dmizer on 2009-10-24
Still need the contents of /etc/network/interfaces.

Also, please post the output of:
```
ifconfig
```

---

### Post by quikone8 on 2009-10-24
ron@tolmarket:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:ed:56:d7  
          inet addr:173.160.43.132  Bcast:173.160.43.135  Mask:255.255.255.248
          inet6 addr: fe80::211:43ff:feed:56d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2337 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1630 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:216732 (216.7 KB)  TX bytes:112252 (112.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:11:43:ed:56:d8  
          inet addr:192.168.1.252  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:feed:56d8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:32370 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4653004 (4.6 MB)  TX bytes:2683262 (2.6 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1377 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:333265 (333.2 KB)  TX bytes:333265 (333.2 KB)

---

### Post by quikone8 on 2009-10-24
This is what  firefox says when I try to login to onw of my local websites with 127.0.0.1;

Failed to Connect

      

      
      
      

      
        
        

          

Firefox can't establish a connection to the server at 127.0.0.1.
 


        
        

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

---

### Post by dmizer on 2009-10-24
Without the contents of /etc/network/interfaces, I can't help you. Please post the contents of /etc/network/interfaces.

---

### Post by quikone8 on 2009-10-25
Thanks,

I will get that posted tomorrow.

---

### Post by quikone8 on 2009-10-25
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 173.160.43.132
netmask 255.255.255.248
gateway 173.160.43.122

iface eth1 inet static
address 192.168.1.252
netmask 255.255.255.0
gateway 192.168.1.1





auto eth1



auto eth0

---

### Post by Iowan on 2009-10-25
Are those the address you want - or the ones that don't work?  Ordinarily, the settings in */etc/network/interfaces* override Network Manager.

---

### Post by quikone8 on 2009-10-25
Yes,

Network Manager has been uninstalled in favor of Network Administrator because I was having problems with static ip's.  If you look at the first couple of posts you can see the progression.  After removing Network Manager and installing Network Admin., I lost connection to the server.  I can browse out but cannot terminal in or get to my mail server or web sites.  What is interesting is that I can get to mail mail server with 127.0.0.1:8080 but using 127.0.0.1 alone will not get to any of the local web sites.  If there is another way to accomplish this I would greatly appreciate hearing it.

---

### Post by Iowan on 2009-10-25
What addresses did you set up for wired1/wired2? 
By "the local websites" you mean on this server - (otherwise, 127.0.0.1 won't get there)?

---

### Post by quikone8 on 2009-10-25
> **Iowan said:**
> What addresses did you set up for wired1/wired2? 
By "the local websites" you mean on this server - (otherwise, 127.0.0.1 won't get there)?

Before I nuked Network Manager they were set for;

iface eth0 inet static
address 173.160.43.132
netmask 255.255.255.248
gateway 173.160.43.122

iface eth1 inet static
address 192.168.1.252
netmask 255.255.255.0
gateway 192.168.1.1

Of course the iface's were then wired 1 and wired 2

---

### Post by dmizer on 2009-10-25
Please post the following two items

1. The contents of /etc/hosts
2. The output of: sudo iptables -L

Also, do you have a local DNS server?

---

### Post by quikone8 on 2009-10-26
> **dmizer said:**
> Please post the following two items

1. The contents of /etc/hosts
2. The output of: sudo iptables °L

Also, do you have a local DNS server?

An answer to your last question; I don't mean to be vague, but I started to setup bind9 before the isp switch but did not finish it, so a long answer is I don't think so.  I will get items 1 and 2 to you in a few hours.  Thanks for your help.

---

### Post by dmizer on 2009-10-26
> **quikone8 said:**
> An answer to your last question; I don't mean to be vague, but I started to setup bind9 before the isp switch but did not finish it, so a long answer is I don't think so.  I will get items 1 and 2 to you in a few hours.  Thanks for your help.

Well, an incorrectly configured DNS server could be causing you trouble.

---

### Post by jward3010 on 2009-10-26
To give us the output of interfaces file, simply type: ```
cat /etc/network/interfaces > Desktop/interfaces.txt
```

This will pump the output of the command to a txt file on your desktop where you can copy and paste it's contents.

---

### Post by quikone8 on 2009-10-26
> **dmizer said:**
> Please post the following two items

1. The contents of /etc/hosts
2. The output of: sudo iptables -L

Also, do you have a local DNS server?
  1.  127.0.0.1 localhost
127.0.1.1 tolmarket

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

2.  Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

### Post by quikone8 on 2009-10-26
> **jward3010 said:**
> To give us the output of interfaces file, simply type: ```
cat /etc/network/interfaces > Desktop/interfaces.txt
```

This will pump the output of the command to a txt file on your desktop where you can copy and paste it's contents.


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet static
address 173.160.43.132
netmask 255.255.255.248
gateway 173.160.43.122

iface eth1 inet static
address 192.168.1.252
netmask 255.255.255.0
gateway 192.168.1.1





auto eth1



auto eth0

---

### Post by quikone8 on 2009-10-26
I thought this might be helpfu;

ron@tolmarket:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
173-160-43-128- *               255.255.255.248 U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
169.254.0.0     *               255.255.0.0     U     1000   0        0 eth1
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth1

I have done a bit more testing to make sure this is not a modem or router problem.  I have a couple of windows servers behind the same modem/router.  I can access both of them remotely.  I can also now that I removed bind9 get to my email server remotely but not through outlook or spicebird,  I can now also terminal in through ssh.  Just thought the additional information would be useful.

---

### Post by quikone8 on 2009-10-27
bump

---

### Post by jward3010 on 2009-10-27
What are eth0 and eth1 connected to respectively?

---

### Post by quikone8 on 2009-10-27
This has been solved, it turned out to be an Apache2 problem with a port the Apache was looking for.  The port was ousted from the other program and now everything works.

---

### Post by jward3010 on 2009-10-28
Thank goodness, it was weird.

---

