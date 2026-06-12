---
title: "Problems with sharing internet connection"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by MarineMan215 on 2009-06-18
Hello, i have two computers: an old dell latitude c610 laptop ([http://www.epinions.com/specs/pr-Laptops_Dell_Latitude_C610_Laptop_220_9503](http://www.epinions.com/specs/pr-Laptops_Dell_Latitude_C610_Laptop_220_9503)), and a HP desktop (i'm pretty sure it's a [http://www.epinions.com/specs/Hewlett_Packard_HP_SR2020NX_Compaq_Presario_Desktop_PC_882780665859](http://www.epinions.com/specs/Hewlett_Packard_HP_SR2020NX_Compaq_Presario_Desktop_PC_882780665859))

Anyway... I have ubuntu 9.04 on both of the computers (the desktop also dual boots with windows xp home edition). Back when the laptop had windows xp pro on it, it could share the wifi signal through a ([http://www.staples.com/office/suppli...P1804:CL140456]("http://www.staples.com/office/supplies/p4_Staples-10-Crossover-Cable-Yellow_166723_Business_Supplies_1_10051_SC3:CG58:grin:P1804:CL140456")) ethernet crossover cable with no trouble at all. Now since it has ubuntu on it i can't seem to get it to work. I went into the network settings and added a new wired network with the "shared to other computers" option selected. Now when i connect the cable and select to use the wired network i made on the laptop it connects! and then after a second it disconnects...

Can anyone help me?
~MarineMan215

---

### Post by iponeverything on 2009-06-18
It all fairly mechanical.

Net <---> Machine 1 <---xover-cable---> Machine 2

Machine 1:

Add the following lines to your /etc/rc.local (above the "exit 0")
```

iptables -t nat -A POSTROUTING -s  192.168.1.2 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/conf/all/forwarding

```

Add the following section your /etc/network/interfaces

```

iface eth0 inet static
 address 192.168.1.1
 netmask 255.255.255.0

auto eth0

```

Machine 2:

Add the following section your /etc/network/interfaces

```

iface eth0 inet static
 address 192.168.1.2
 netmask 255.255.255.0
 gateway 192.168.1.1

auto eth0

```

add the following lines to your /etc/resolv.conf
```

nameserver 208.67.220.220
nameserver 208.67.222.222

```

reboot both machines and you should be good to go.

Note that you will not see these connection in network manager while they are in /etc/network/interfaces

---

### Post by MarineMan215 on 2009-06-18
I restarted both computers and now the laptop still has wifi but now it's not recognizing the desktop.

Any ideas?
~MarineMan215

---

### Post by iponeverything on 2009-06-18
> **MarineMan215 said:**
> I restarted both computers and now the laptop still has wifi but now it's not recognizing the desktop.

Any ideas?
~MarineMan215

You have to work me a bit here. What do you mean by "not recognizing the desktop" ?

It can't ping it? What exactly are you doing to test it?

from a terminal try to ping the other machine.

---

### Post by MarineMan215 on 2009-06-18
It doesn't do anything when i plug in the cable to both computers. What do you mean by "pinging it". Tell me the command and maybe i can paste in the result to help you to help me =).

I wish it was as easy as checking "Share this internet connection" box in windows
~MarineMan215

---

### Post by iponeverything on 2009-06-18
On the machine with the wifi connection, run these commands and post the output:

ifconfig
route -n

---

### Post by MarineMan215 on 2009-06-18
Thanks for the speedy replies! Hold on a second my mom is using XP right now so i'll edit this post shortly...

EDIT:
marineman@MarineMan215-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:a5:95:2e  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fea5:952e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3723 (3.7 KB)
          Interrupt:11 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1088 (1.0 KB)  TX bytes:1088 (1.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:41:4c:ee:e2  
          inet addr:172.16.42.2  Bcast:172.16.42.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fe4c:eee2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:595 errors:0 dropped:0 overruns:0 frame:0
          TX packets:555 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:394404 (394.4 KB)  TX bytes:89680 (89.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0C-41-4C-EE-E2-65-65-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

marineman@MarineMan215-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
172.16.42.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         172.16.42.1     0.0.0.0         UG    0      0        0 wlan0

Does this help? I can't make heads nor tails of this (but then again, i'm not a network person)

---

### Post by iponeverything on 2009-06-19
```

marineman@MarineMan215-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:0b:db:a5:95:2e
inet addr:192.168.1.1 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::20b:dbff:fea5:952e/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
[COLOR="Red"]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/COLOR]
TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:3723 (3.7 KB)
Interrupt:11 Base address:0x8c00 

```


Can you verify that your X-over is good and that it is going directly from machine to machine and not through a switch. 

If you are going through a switch, use two straight through cables.

also post the output of:

sudo iptables -t nat -L -n 
sudo iptables -L -n

---

### Post by MarineMan215 on 2009-06-19
I'm pretty sure the cable is good (using it right now to use my grandparent's FiOS). I'm not at home but i'll edit when i can.

EDIT:

marineman@MarineMan215-laptop:~$ sudo iptables -t nat -L -n
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
marineman@MarineMan215-laptop:~$ sudo iptables -L -n
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  172.16.42.1          0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  172.16.42.1          0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        all  -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  172.16.42.2          172.16.42.1         tcp dpt:53 
ACCEPT     udp  --  172.16.42.2          172.16.42.1         udp dpt:53 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:9001 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           udp dpt:9001 
LSI        all  --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0      

~MarineMan215

---

### Post by iponeverything on 2009-06-21
Flush your firewall rules. It looks like you have firestarter installed that is keeping it from working.

```
sudo iptables -F

```

Then rerun these commands:

```

sudo iptables -t nat -A POSTROUTING -s  192.168.1.2 -j MASQUERADE
sudo echo 1 > /proc/sys/net/ipv4/conf/all/forwarding
```

---

### Post by MarineMan215 on 2009-06-21
I will try to do that today or maybe tomorrow because i'll be away due to father's day today. I'll edit when i can.

Thanks for working through this so far!
~MarineMan215

---

