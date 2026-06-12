---
title: "Can't ping the other PC"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by Roque on 2009-03-25
I added an ethernet adapter (Realtek chipset) to each one of my two PCs and connected them with a crossover cable. I get green light in each adapter, the hardware autonegotiation is successful, and if I boot Knoppix in both computers I certainly can upload the interfaces and ping both PCs without problem. But I can't do this in Ubuntu. 

In Ubuntu with iptables loaded any attempt at pinging gets no response. If I flush iptables and set default policies to ACCEPT, and then issue a ping command, I get a "sendmsg: operation not permitted" message.

Can anyone help? I really have no idea on what's going on here.

---

### Post by Roque on 2009-03-25
Also if I boot Knoppix in one PC and Ubuntu in the other I cannot ping anymore. 

So it is Ubuntu's fault.

---

### Post by dfreer on 2009-03-25
Did you set up a static IP address for each machine? Since you are connecting these machines via a crossover cable, there shouldn't be any sort of DHCP server running to give out IP addresses unless you set that up too.

Posting your /etc/network/interfaces files from both machines with Ubuntu and the results of the ifconfig -a command might be helpful as well.

---

### Post by Roque on 2009-03-25
> Did you set up a static IP address for each machine? Since you are connecting these machines via a crossover cable, there shouldn't be any sort of DHCP server running to give out IP addresses unless you set that up too.
Yes, after boot up I write:

In PC#1:
```
sudo ifconfig eth1 192.168.0.1
```

In PC#2:
```
sudo ifconfig eth1 192.168.0.2
```

This allows pinging under Knoppix, but fails under Ubuntu:
From PC#1:
```
ping 192.168.0.2
```


Here's what you asked for:


PC#1:
```

ifconfig -a

eth1      Link encap:Ethernet  HWaddr 00:08:54:a5:e0:13
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1368 (1.3 KB)  TX bytes:5688 (5.5 KB)
          Interrupt:18 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:692 (692.0 B)  TX bytes:692 (692.0 B)

nas0      Link encap:Ethernet  HWaddr 00:13:49:03:fa:55
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:174157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:144962 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:218382784 (208.2 MB)  TX bytes:13667481 (13.0 MB)

ppp0      Link encap:Point-to-Point Protocol
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:79047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78147 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:88553347 (84.4 MB)  TX bytes:4664524 (4.4 MB)

```

```

cat /etc/network/interfaces

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig nas0 up # line maintained by pppoeconf
provider dsl-provider

auto nas0
iface nas0 inet manual

```

PC#2 has the same interfaces (they were configured to replace each other). The ip addresses for the eth1 are the ones I setup with ifconfig

---

### Post by Iowan on 2009-03-25
How is **route** configured.  Is "the other" PC set as gateway?

---

### Post by Roque on 2009-03-25
Here's the ouput of "route" in PC#1:
```
route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
XXXXXXXXXXXXXXX *               255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth1
default         *               0.0.0.0         U     0      0        0 ppp0

```

PC#1 is where the modem is connected, but I am not trying (yet) to set it as a gateway or to share internet access. I am only trying to establish a basic connection between both PCs under Ubuntu.

---

### Post by mhgsys on 2009-03-25
Maybe a stupid question from my side here. 
but, ehm, 

are both pc's in the same network?

edit: Meaning the same workgroup.

---

### Post by Roque on 2009-03-25
Sorry for the dumb question, but how can I determine that?

---

### Post by mhgsys on 2009-03-25
Well, 

The only way I know to do what you want to do  is to have samba installed on both pc's.

```

sudo apt-get install samba

```

Then make sure that there on the same network by 


```

sudo nano /etc/samba/smb.conf

```

There you'll find your network name and sharing settings. Edit them as you like
restart samba 

```

sudo /etc/init.d/samba restart

```


I guess it would be possible in other way's as well, if both pc's are booting linux, 
Anyway, I only know this way,

---

### Post by Roque on 2009-03-25
Ok, thanks. But for now I only want to confirm that each PC can communicate with the other one. As I said, in Knoppix I can verify this with ping; something in Ubuntu seems to be conflicting with the connection.

---

### Post by WrathofthePenguin on 2009-03-25
> **Roque said:**
> I added an ethernet adapter (Realtek chipset) to each one of my two PCs and connected them with a crossover cable. I get green light in each adapter, the hardware autonegotiation is successful, and if I boot Knoppix in both computers I certainly can upload the interfaces and ping both PCs without problem. But I can't do this in Ubuntu. 

In Ubuntu with iptables loaded any attempt at pinging gets no response. If I flush iptables and set default policies to ACCEPT, and then issue a ping command, I get a "sendmsg: operation not permitted" message.

Can anyone help? I really have no idea on what's going on here.

From strictly a networking perspective, there should be no problem. I suspect the problem is with iptables. Can we see the output of this:

sudo iptables -L

WOTP

---

### Post by Roque on 2009-03-25
```

sudo iptables -L

Chain INPUT (policy DROP)
target     prot opt source               destination
DROP       icmp --  anywhere             anywhere            icmp echo-reply
ACCEPT     all  --  anywhere             anywhere
DROP       tcp  --  anywhere             anywhere            tcp dpt:www
DROP       tcp  --  anywhere             anywhere            tcp dpt:ssh
DROP       tcp  --  anywhere             anywhere            tcp dpt:smtp
DROP       tcp  --  anywhere             anywhere            tcp dpt:pop3
DROP       tcp  --  anywhere             anywhere            tcp dpt:domain
LOG        all  --  anywhere             anywhere            state NEW LOG level warning prefix `Non-requested: '
DROP       all  --  anywhere             anywhere            state NEW
LOG        icmp -f  anywhere             anywhere            LOG level warning prefix `Fragmented ICMP: '
DROP       icmp -f  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request
ACCEPT     all  --  anywhere             anywhere
REJECT     tcp  --  anywhere             anywhere            tcp spt:www reject-with icmp-port-unreachable
REJECT     tcp  --  anywhere             anywhere            tcp spt:ssh reject-with icmp-port-unreachable
REJECT     tcp  --  anywhere             anywhere            tcp spt:smtp reject-with icmp-port-unreachable
REJECT     tcp  --  anywhere             anywhere            tcp spt:pop3 reject-with icmp-port-unreachable
REJECT     tcp  --  anywhere             anywhere            tcp spt:domain reject-with icmp-port-unreachable
ACCEPT     all  --  anywhere             anywhere            state NEW,RELATED,ESTABLISHED

```

The problem persists even if I flush iptables and free all traffic with default policies:
```

sudo iptables -F

sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
```

---

### Post by WrathofthePenguin on 2009-03-26
> sudo iptables -F

sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT

So after doing these commands, let's do another sudo iptables -L and see how you rules look afterward.

---

### Post by Roque on 2009-03-26
Here it is:
```
iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

---

### Post by WrathofthePenguin on 2009-03-26
> **Roque said:**
> Here it is:
```
iptables -L

Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

I would say that if you don't have another firewall installed you may have found a bug.

---

