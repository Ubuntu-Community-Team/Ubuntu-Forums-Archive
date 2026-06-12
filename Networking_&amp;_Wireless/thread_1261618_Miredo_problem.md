---
title: "Miredo problem"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by tarkshya on 2009-09-08
Hi all IPv6 aficionado

I am having difficulty connecting two ubuntu machines using Miredo. I have successfully installed Miredo on both boxes. Both the boxes are located behind separate cone NAT routers. IPv4 Internet can be accessed from both the boxes. The NAT routers for both the machines are different. From each box, I can ping well known IPv6 sites like ipv6.google.com, and many others. Both boxes can be pinged from outside websites which provide a facility to do ping6 on any globally IPv6 address. I am using following websites to do IPv6 ping.

[http://www.berkom.blazing.de/tools/ping.cgi](http://www.berkom.blazing.de/tools/ping.cgi)
[http://www.subnetonline.com/pages/ipv6-network-tools/online-ipv6-ping.php](http://www.subnetonline.com/pages/ipv6-network-tools/online-ipv6-ping.php)

Both the boxes respond well to these ping probes.

**The only problem is, these two boxes just won't talk to each other.** When I try to ping box 1 from box 2, I get the error

ping6 2001:0:53aa:64c:142a:465f:ba07:6d2
PING 2001:0:53aa:64c:142a:465f:ba07:6d2(2001:0:53aa:64c:142a:465f:ba07:6d2) 56 data bytes
From 2001:0:53aa:64c:204b:7240:b9a5:ecae icmp_seq=11 Destination unreachable: Address unreachable
From 2001:0:53aa:64c:204b:7240:b9a5:ecae icmp_seq=12 Destination unreachable: Address unreachable
From 2001:0:53aa:64c:204b:7240:b9a5:ecae icmp_seq=13 Destination unreachable: Address unreachable


Here is the miredo.conf for both the machines.

cat /etc/miredo.conf 
# Please refer to the miredo.conf(5) man page for details.
InterfaceName    teredo

# Pick a Teredo server:
#ServerAddress    teredo.ipv6.microsoft.com
ServerAddress    teredo-debian.remlab.net

# Some firewall/NAT setups require a specific UDP port number:
#BindPort    3545

This cofiguration is same on both machines. As one can see, I am using teredo-debian.remlab.net as my teredo server.


Here is the relevent portion of the ifconfig output from one of the machine

teredo    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet6 addr: fe80::ffff:ffff:ffff/64 Scope:Link
          inet6 addr: 2001:0:53aa:64c:204b:7240:b9a5:ecae/32 Scope:Global
          UP POINTOPOINT RUNNING NOARP  MTU:1280  Metric:1
          RX packets:1290 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1816 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1036085 (1011.8 KB)  TX bytes:222821 (217.5 KB)


I have tried everything, including replacing one machine with a windowsXP + teredo setup, and then replacing XP+ teredo as both IPv6 nodes, and the behavior is unchnaged. In every configuration, individual IPv6 nodes will talk to outside machines, but will not talk to each other.

What could be wrong here. Can anybody help me here please.

[B]2001:0:53aa:64c:204b:7240:b9a5:ecae is the node which I always keep up. So can anybody please ping to this machine and see if it is reachable from their end.
[/B]
Thanks all
Tarkshya

---

### Post by Lrb_ on 2009-12-02
I have the same problem, please help to setup connection between both computers.

---

### Post by Malchio on 2010-05-07
/push 

I have the same problem and serached the for days but cant find a solution so plese answer *G

---

