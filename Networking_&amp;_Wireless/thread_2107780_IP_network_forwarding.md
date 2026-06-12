---
title: "IP network forwarding"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by sQua on 2013-01-22
I have a Ubuntu 12.10 host and I'm trying to forward network traffic from one interface to another, and vice versa:
 
I have two network interfaces, vnet0 and vnet1, as shown by 'ip addr':
```

<SNIP>
4: vnet0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 0a:00:27:00:00:00 brd ff:ff:ff:ff:ff:ff
    inet 10.33.1.99/24 brd 10.33.1.255 scope global vnet0
    inet6 fe80::800:27ff:fe00:0/64 scope link 
       valid_lft forever preferred_lft forever
5: vnet1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UNKNOWN qlen 1000
    link/ether 0a:00:27:00:00:01 brd ff:ff:ff:ff:ff:ff
    inet 10.33.2.99/24 brd 10.33.2.255 scope global vnet1
    inet6 fe80::800:27ff:fe00:1/64 scope link 
       valid_lft forever preferred_lft forever

```

...as you can see, in the host I have IP address 10.33.1.99 associated with vnet0, and 10.33.2.99 associated with vnet1, each with an 8 bit subnet behind them.
 
Behind each interface, from the host (this Ubuntu 12.10) I can ping another connected host:
So I can ping the host 10.33.1.1 connected behind vnet0, and I can ping 10.33.2.1 connected behind vnet1, and each can ping me (this host).
 
However, how do I allow network forwarding of traffic, so that 10.33.1.1 can ping 10.33.2.1, and vice versa?  Also without upsetting any other interfaces or IP addresses I may add to this host.
 
I've tried 'echo 1 > /proc/sys/net/ipv4/ip_forward' and putting all sorts of routes under the 'ip route' command but at best only end up with nothing working.
 
With my other interfaces down, from 'ip route' I get:
```

10.33.1.0/24 dev vnet0  proto kernel  scope link  src 10.33.1.99 
10.33.2.0/24 dev vnet1  proto kernel  scope link  src 10.33.2.99 

```
Or equivalently with 'route' I get:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.33.1.0       *               255.255.255.0   U     0      0        0    vnet0
10.33.2.0       *               255.255.255.0   U     0      0        0    vnet1

```

...in short.  I just would like to forward traffic between the 10.33.1.0/24 subnet on vnet0, and the 10.33.2.0/24 subnet on vnet1.
 
Any help is greatly appreciated.  Thanks.

---

### Post by PowerBarry43 on 2013-01-22
Hi

have a read of this

[http://askubuntu.com/questions/95354/how-to-enable-forwarding-of-data-between-two-local-interfaces](http://askubuntu.com/questions/95354/how-to-enable-forwarding-of-data-between-two-local-interfaces)

Hope this helps!

Barry

---

### Post by sQua on 2013-01-23
Thanks for your reply.  I checked out the link.  I hadn't previously put anything into iptables, but I looked at the rules you linked to and tried what I think it is saying for my case:
```

iptables -A FORWARD -p tcp -m state -d 10.33.1.0/255.255.255.0 --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -p udp -m state -d 10.33.1.0/255.255.255.0 --state RELATED,ESTABLISHED -j ACCEPT

```
Which doing an 'iptables -S FORWARD' gave:
```

-P FORWARD ACCEPT
-A FORWARD -d 10.33.1.0/24 -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -d 10.33.1.0/24 -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT

```

And I also tried the equivalent in the other direction; changing the 10.33.1.0 for 10.33.2.0 in addition to the above rules:
```

-P FORWARD ACCEPT
-A FORWARD -d 10.33.1.0/24 -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -d 10.33.1.0/24 -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -d 10.33.2.0/24 -p tcp -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -d 10.33.2.0/24 -p udp -m state --state RELATED,ESTABLISHED -j ACCEPT

```
...but no luck whatsoever.

I tried my own rules in iptables, as I want all packets to flow from any host on the 10.33.1.0/24 subnet behind vnet0 to any host on the 10.33.2.0/24 subnet behind vnet1, and vice versa.

So, after doing a 'iptables -F' to flush the rules in each case, I did:
```

iptables -A FORWARD -i vnet0 -o vnet1 -j ACCEPT
iptables -A FORWARD -i vnet1 -o vnet0 -j ACCEPT

```
...which looks sensible and simple to me, though I have no experience with iptables so there may be something I'm not getting here.  It didn't work.

So, I tried:
```

iptables -A FORWARD -p all -i vnet0 -s 10.33.1.0/24 -d 10.33.2.0/24 -o vnet1 -j ACCEPT
iptables -A FORWARD -p all -i vnet1 -s 10.33.2.0/24 -d 10.33.1.0/24 -o vnet0 -j ACCEPT

```
Which doing an 'iptables -S FORWARD' gave:
```

-P FORWARD ACCEPT
-A FORWARD -s 10.33.1.0/24 -d 10.33.2.0/24 -i vnet0 -o vnet1 -j ACCEPT
-A FORWARD -s 10.33.2.0/24 -d 10.33.1.0/24 -i vnet1 -o vnet0 -j ACCEPT

```

...In all cases, from this host (Ubuntu 12.10), I could ping the connected host now at 10.33.1.10, and I could ping the other connected host now at 10.33.2.10, and each of them could ping this host (10.33.1.99 on vnet0, and 10.33.2.99 on vnet1), but they couldn't ping each other.

I don't know what I'm missing.  Catting /proc/sys/net/ipv4/ip_forward gives me 1, I have the routes I indicated earlier, and I've tried the above in iptables.

---

### Post by Crafty Kisses on 2013-01-23
Hey sQua!

Can I just see some results of this command so I can get some more information? 
```
route -Cn
```
It should look something similar to this
```
Kernel IP routing cache
Source          Destination     Gateway         Flags Metric Ref    Use Iface
192.168.1.157   192.168.1.51    192.168.1.51          0      0        1 eth0
192.168.1.157   74.125.236.69   192.168.1.10  
```

---

### Post by sQua on 2013-01-24
Being able to ping and be pinged by each subnet connected host (10.33.1.10 and 10.33.2.10), but before putting any rules into the iptables filter table or '1' into 'ip_forward', the results were:

'iptables -L' was pretty empty, but the default policies were there:

iptables -S INPUT
```
-P INPUT ACCEPT
```
iptables -S FORWARD
```
-P FORWARD ACCEPT
```
iptables -S OUTPUT
```
-P OUTPUT ACCEPT
```

Which doing a 'route' gave me:

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.33.1.0       0.0.0.0         255.255.255.0   U     0      0        0    vnet0
10.33.2.0       0.0.0.0         255.255.255.0   U     0      0        0    vnet1
```

route -Cn
```
Kernel IP routing cache
Source          Destination     Gateway         Flags Metric Ref    Use Iface
10.33.2.99      10.33.2.255     10.33.2.255     bl    0      0        4    vnet1
10.33.1.99      10.33.1.255     10.33.1.255     bl    0      0        4    vnet0
127.0.0.1       127.0.0.1       127.0.0.1       l     0      0     8011 lo
127.0.0.1       127.0.0.1       127.0.0.1       l     0      0     2668 lo
```

- - - - - - -

Then after putting the following rules into iptables:
```

iptables -A FORWARD -i vnet0 -o vnet1 -j ACCEPT
iptables -A FORWARD -i vnet1 -o vnet0 -j ACCEPT

```

...I got the following results:

INPUT and OUTPUT were the same default policies only.

iptables -S FORWARD
```

-P FORWARD ACCEPT
-A FORWARD -i vnet0 -o vnet1 -j ACCEPT
-A FORWARD -i vnet1 -o vnet0 -j ACCEPT

```

Which doing a 'route' gave me:

route -n - same as above.

route -Cn
```
Kernel IP routing cache
Source          Destination     Gateway         Flags Metric Ref    Use Iface
127.0.0.1       127.0.0.1       127.0.0.1       l     0      0       23 lo
127.0.0.1       127.0.0.1       127.0.0.1       l     0      0        7 lo
```

...so it looks like my 'route -Cn' got emptier after adding the iptables rules to the filter table's FORWARD chain.  I'll have check out the significance of this, - I'm not yet sure the significance of 'route -Cn'.

---

### Post by SeijiSensei on 2013-01-24
Is IP forwarding enabled in /etc/sysctl.conf?  For a quick check run the command "cat /proc/sys/net/ipv4/ip_forward".  If it returns a zero, forwarding is disabled.  Edit sysctl.conf and uncomment the "net.ipv4.ip_forward=1" line as described in the comments in the sysctl.conf file.  Then reboot.

---

### Post by sQua on 2013-01-27
> **SeijiSensei said:**
> Is IP forwarding enabled in /etc/sysctl.conf?  For a quick check run the command "cat /proc/sys/net/ipv4/ip_forward".  If it returns a zero, forwarding is disabled.  Edit sysctl.conf and uncomment the "net.ipv4.ip_forward=1" line as described in the comments in the sysctl.conf file.  Then reboot.

I haven't edited /etc/sysctl.conf, but as root ('sudo su -') after doing a 'echo 1 > /proc/sys/net/ipv4/ip_forward' I have catted it to check it gives me a "1".


Anyway, it seems to work now, I'm not fully sure why - I'll have to start from the top next week to see what makes it work.

BTW. When I did the 'route -Cn' earlier, I must have done it after a long wait after trying to ping between the nodes.  I just realised they must have timed out and fell out of the cache.  Now when I do it straight after trying to ping between the nodes I get a much fuller table.


In addition to filling the iptables filter table's FORWARD chain as I last did, I also did:
```

iptables -A INPUT -i vnet+ -j ACCEPT
iptables -A OUTPUT -o vnet+ -j ACCEPT

```

...which also didn't work.  I could ping this host from each subnet node, and the connected nodes from this host, but not from one connected node to the other.

However, I got it working...

In each attached node, I previously brought it up with a default route:
```

ip addr add 10.33.1.10/24 dev p2p1
ip route add default dev p2p1

```
...and similarly for the node 10.33.2.10 on the second subnet.

I thought 'default' meant send everything that way if there is no other explicit route.

Anyway, in addition to the default, I just added an explicit route to the other subnet I want to reach:
```

ip route add 10.33.2.0/24 via 10.33.2.99

```
...and similarly for the node on the second subnet.

Now it works!  I'm quite surprised.  I thought I knew how 'route' works at least.

I'm wondering how much of the FORWARD, INPUT, and OUTPUT settings I actually need now. :D
I'll start with these route settings in the connected nodes, and then add to iptables bit by bit in this host to see what exactly I need.  I'll report back next week!

---

