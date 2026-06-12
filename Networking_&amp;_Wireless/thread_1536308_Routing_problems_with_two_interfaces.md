---
title: "Routing problems with two interfaces"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by sonicbuddha on 2010-07-22
I run a small, low power machine with two interfaces as a file and torrent server.  Both interfaces are on the same LAN.  I typically assign different services to different interfaces, such as AFP, SMB, SSH to one and the Azureus to the other.  This has worked fine in 8.04 but with 10.04 if I bring up the machine with both interfaces active packets cannot find their way back through my firewall (LAN traffic is fine).  A traceroute stops right at my firewall.  This is not exclusive to my network environment, either- I've tested with a virtual machine at work as well and packets cannot find their way back beyond the first router.  I'm not the best at troubleshooting but the basic network issues so I'm at a loss what occurred between 8.04 and 10.04 that is causing this problem.

---

### Post by iponeverything on 2010-07-22
Your network layout is not clear. Is your "firewall" the same machine.

---

### Post by sonicbuddha on 2010-07-22
No, this is a single machine behind a firewall which is another machine.  There is no firewall software running on the server unless there is something preconfigured that I do not know about.  This is the same configuration that is running on the virtual machine that I have tested in other environments.  I invite you to attempt the same configuration using VirtualBox with a server install (not desktop).

---

### Post by sonicbuddha on 2010-07-22
For argument's sake, I created a default install of Debian 5.0.4 in a virtual machine and there is no problem with two interfaces and package routing.  The kernel is off by several versions, however (2.6.26), assuming that this could be at all kernel related.

Edit:
I updated to the most recent backported kernel in Debian 5.0.4, 2.6.32-bpo.5, and this issue does not exist.  It seems Ubuntu isolated.

---

### Post by iponeverything on 2010-07-22
Turn off sending and listening to ICMP redirects, if that does not fix it post your routing table.  It could very well be that you have two default routes. If that is case, just delete one of them and prevent its recurrence by configuring the interfaces in /etc/network/interfaces so that you can control which interface is going to get the gateway.

---

### Post by sonicbuddha on 2010-07-22
I'll try turning off sending and listening to ICMP redirects but having two default routes should not be a problem- and isn't a problem for 8.04, my Debian test install, or any other operating system I've tested with (OS X, Windows).  For not specific traffic it simply picks up the first default and for applications bound to specific applications they use the first default they can- the address they are bound to.  10.04 is the only install I've ever had that choked with more than one default route (thus the post).

---

### Post by iponeverything on 2010-07-22
Nice of you to clear things up. 

Two equal metric default routes on the same segment *on separate network devices* have always caused problems for me. Logically, how is that you would expect it to work correctly? 

If you don't want to remove one them to test or just out of principal or because "it worked before" that is your business. Good luck.

---

### Post by sonicbuddha on 2010-07-22
I have tested with a single interface- there is no routing problem with a single interface.  I have also tested by setting only one interface to to have a gateway, which also works. 

I am not against testing and have done so prior to my post and am open and eager for more suggestions.  My understanding of routing tables is that the first route that matches the destination is used- a second default should be, the majority of the time, ignored.

My reluctance to settle on using only one interface with a gateway is because I am reluctant to reduce functionality without explanation.  Two interfaces with gateway settings should work and, prior to 10.04 as well as with other operating systems, does work.

---

### Post by iponeverything on 2010-07-23
I've had different a experience under linux and I don't have much of an understanding of the MS network stack as they do a wonderful job of hiding what exactly the kernel is doing and of making it difficult to find out. Fortunately my world has always revolved UNIX variants or Linux. I have never needed use osX in a server setting, because of the availability better FOSS alternatives. 

Every time I have accidentally ended up with two identical default routes over separate interfaces on a machine, it has never worked correctly -- and in the past 17 years it has happened to me more that few times. As for "other operating systems" working, lots of vendors have/had broken or incomplete IPv4 implantations. BTW - just make sure I was not going senile, I just tested it 8.10 and 9.04 -- neither one works as configured:

> 
0.0.0.0         10.111.111.254  0.0.0.0         UG    0      0        0 eth0
0.0.0.0         10.111.111.254  0.0.0.0         UG    0      0        0 eth1


Increasing the metric on either default route does work. But, it doesn't really buy anything.  

How is not having two identical default gateways on the same segment over different interfaces "reduced functionality" ?

If anything two identical default gateways on the same segment over different interfaces is not extra functionality, its just broken. Making one of the defaults a higher metric might work, except for the fact that you have different services bound to the separate interfaces.  

So - If you don't mind me asking - why are using two interfaces on same segment with each offering a different set of services? 

If you want to make use of both interfaces, I suggest bonding them or setting up one as hot standby for automatic failover if the primary becomes inactive.

If you really do want to find out what is happing with regard to your traffic with your unique configuration, use an instance of tcpdump on each of the interfaces and send the output to a files. Then run some tests, it should not be hard to deduce how things are getting mucked.

---

### Post by iponeverything on 2010-07-23
> **sonicbuddha said:**
> For argument's sake, I created a default install of Debian 5.0.4 in a virtual machine and there is no problem with two interfaces and package routing.  The kernel is off by several versions, however (2.6.26), assuming that this could be at all kernel related.

Edit:
I updated to the most recent backported kernel in Debian 5.0.4, 2.6.32-bpo.5, and this issue does not exist.  It seems Ubuntu isolated.

Let me see the routing table for this and the output from ifconfig, just to make sure we are the same page.

---

### Post by sonicbuddha on 2010-08-01
If we can, I'd like to move away from discussing why the question was asked and instead focus on answering the question itself, please.    Something is different in 10.04 and even if the purpose may not be applicable in a particular environment, the result still remains interesting, worthwhile, and, in fact, may apply in ways not otherwise immediately evident.  I am really hoping there is a security protocol, kernel setting, or service running that was implemented somewhere between 8.04 and 10.04 that can be identified, if not managed.

As for proof of concept, here are the ifconfig and route values from installs where two interfaces with the same gateway works, 8.04, Debian 5.04, OS X 10.6.4, and Open Solaris 9, and a non-working 10.04.  I just created a default 9.10 install and this 'problem' exists here, too.  Note that Open Solaris and OS X do not have a 'route' command that returns routing like Linux, so I used netstat -nr

Working 8.04 configuration:
eth0      Link encap:Ethernet  HWaddr 00:30:18:ad:ed:ec  
          inet addr:10.1.1.15  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fead:edec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26595768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12716759 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3427873578 (3.1 GB)  TX bytes:3744703590 (3.4 GB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:30:18:ad:ed:ed  
          inet addr:10.1.1.16  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fead:eded/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27604069 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54302172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4183963946 (3.8 GB)  TX bytes:1736026744 (1.6 GB)
          Interrupt:17 Base address:0x2000 


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        *               255.255.255.0   U     0      0        0 eth0
10.1.1.0        *               255.255.255.0   U     0      0        0 eth1
default         blackbox.xxxx 0.0.0.0         UG    100    0        0 eth1
default         blackbox.xxxx 0.0.0.0         UG    100    0        0 eth0

Debian 5.0.4
eth0      Link encap:Ethernet  HWaddr 00:0c:29:87:c0:5d  
          inet addr:10.1.1.133  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe87:c05d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32228 (31.4 KiB)  TX bytes:4072 (3.9 KiB)
          Interrupt:19 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:0c:29:87:c0:67  
          inet addr:10.1.1.109  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe87:c067/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3319 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7677393 (7.3 MiB)  TX bytes:248631 (242.8 KiB)
          Interrupt:19 Base address:0x2080 


Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        *               255.255.255.0   U     0      0        0 eth1
10.1.1.0        *               255.255.255.0   U     0      0        0 eth0
default         blackbox.xxxx 0.0.0.0         UG    0      0        0 eth0
default         blackbox.xxxx 0.0.0.0         UG    0      0        0 eth1

OS X 10.6.4
en0: flags=8963<UP,BROADCAST,SMART,RUNNING,PROMISC,SIMPLEX,MULTICAST> mtu 1500
        ether 00:1f:5b:32:37:88 
        inet6 fe80::21f:5bff:fe32:3788%en0 prefixlen 64 scopeid 0x4 
        inet 10.1.1.100 netmask 0xffffff00 broadcast 10.1.1.255
        media: autoselect (1000baseT <full-duplex,flow-control>)
        status: active
en1: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
        ether 00:1f:5b:32:37:89 
        inet6 fe80::21f:5bff:fe32:3789%en1 prefixlen 64 scopeid 0x5 
        inet 10.1.1.157 netmask 0xffffff00 broadcast 10.1.1.255
        media: autoselect (1000baseT <full-duplex,flow-control>)
        status: active
 netstat -nr
Routing tables

Internet:
Destination        Gateway            Flags        Refs      Use   Netif Expire
default            10.1.1.1           UGSc           12        0     en0
default            10.1.1.1           UGScI           0        0     en1
10.1.1/24          link#4             UCS            13        0     en0
10.1.1/24          link#5             UCSI            1        0     en1
10.1.1.1           0:18:f8:77:a0:3f   UHLWI           6       74     en0   1167
10.1.1.11          0:1a:92:b9:e2:1    UHLWI           1        6     en0   1169
10.1.1.14          link#4             UHLWI           0       33     en0
10.1.1.15          0:30:18:ad:ed:ec   UHLWI           0      269     en0   1125
10.1.1.16          0:30:18:ad:ed:ec   UHLWI           0       78     en0   1128
10.1.1.21          0:c0:48:26:27:5e   UHLWI           0        0     en0   1171
10.1.1.21          0:c0:48:26:27:5e   UHLWI           0        0     en1   1171
10.1.1.100         127.0.0.1          UHS             0        0     lo0
10.1.1.148         0:c:29:3e:40:c5    UHLWI           0       10     en0   1137
10.1.1.157         127.0.0.1          UHS             0        1     lo0
10.1.1.255         ff:ff:ff:ff:ff:ff  UHLWbI          0       15     en0
127                127.0.0.1          UCS             0        0     lo0
127.0.0.1          127.0.0.1          UH              1       14     lo0

Open Solaris 9
ifconfig -a
lo0: flags=2001000849<UP,LOOPBACK,RUNNING,MULTICAST,IPv4,VIRTUAL> mtu 8232 index 1
        inet 127.0.0.1 netmask ff000000 
pcn0: flags=1004843<UP,BROADCAST,RUNNING,MULTICAST,DHCP,IPv4> mtu 1500 index 2
        inet 10.1.1.148 netmask ffffff00 broadcast 10.1.1.255
pcn1: flags=1004843<UP,BROADCAST,RUNNING,MULTICAST,DHCP,IPv4> mtu 1500 index 3
        inet 10.1.1.125 netmask ffffff00 broadcast 10.1.1.255
lo0: flags=2002000849<UP,LOOPBACK,RUNNING,MULTICAST,IPv6,VIRTUAL> mtu 8252 index 1
        inet6 ::1/128 

Routing Table: IPv4
  Destination           Gateway           Flags  Ref     Use     Interface 
-------------------- -------------------- ----- ----- ---------- --------- 
default              10.1.1.1             UG        1          2 pcn0      
default              10.1.1.1             UG        1          1 pcn1      
10.1.1.0             10.1.1.148           U         1          2 pcn0      
10.1.1.0             10.1.1.125           U         1          1 pcn1      
127.0.0.1            127.0.0.1            UH        1         28 lo0       

Routing Table: IPv6
  Destination/Mask            Gateway                   Flags Ref   Use    If   
--------------------------- --------------------------- ----- --- ------- ----- 
::1                         ::1                         UH      1       0 lo0 


10.04
eth0      Link encap:Ethernet  HWaddr 00:0c:29:30:6f:8f  
          inet addr:10.1.1.139  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe30:6f8f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:258 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19342 (19.3 KB)  TX bytes:1152 (1.1 KB)

eth1      Link encap:Ethernet  HWaddr 00:0c:29:30:6f:99  
          inet addr:10.1.1.115  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe30:6f99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:86839 (86.8 KB)  TX bytes:157150 (157.1 KB)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.1.0        *               255.255.255.0   U     0      0        0 eth1
10.1.1.0        *               255.255.255.0   U     0      0        0 eth0
default         blackbox.xxxx 0.0.0.0         UG    100    0        0 eth0
default         blackbox.xxxx 0.0.0.0         UG    100    0        0 eth1

---

### Post by sonicbuddha on 2010-08-09
AH HA!!!  Found it!

It looks like there is a sysctl setting that was set in 8.04 LTS but was broken and is now fixed in at least 9.10 forward:

rp_filter is for Source Address Verification, setting to 1 enables it.
net.ipv4.conf.default.rp_filter=1
net.ipv4.conf.all.rp_filter=1

On 8.04 this results in 

net.ipv4.conf.lo.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.eth0.rp_filter = 0  <== should have inherited the 1
net.ipv4.conf.eth1.rp_filter = 0  <== should have inherited the 1

On 10.04 this results in

net.ipv4.conf.lo.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.eth0.rp_filter = 1
net.ipv4.conf.eth1.rp_filter = 1 

This setting is probably not a big deal on a LAN.  Now that I see that this is a 'fixed bug' between 8.04 and 10.04 I may go a different direction to separate my network traffic.... or not.

---

