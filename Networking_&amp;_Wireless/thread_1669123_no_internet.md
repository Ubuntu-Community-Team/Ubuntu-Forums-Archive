---
title: "no internet"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by sashwath on 2011-01-17
my net worx fine on win7.i copied the values of ip address,netmask and others to ubuntu.it connects but the page doesnt load.help!!!

---

### Post by dineshs on 2011-01-17
What do you get for ```
ping 4.2.2.1 -c3
``````
route -n
```and```
ifconfig -a
```

---

### Post by sashwath on 2011-01-18
on windows or ubuntu.if on ubuntu then where should i run it?

---

### Post by mick222 on 2011-01-18
copy and paste into terminal.
applications-> accessories-> terminal

post output here 
 Are you connecting via ethernet or wireless
Are you connected via a router  if so what security does it use.

---

### Post by sashwath on 2011-01-18
this is wat it shows when i run ifconfig

eth0      Link encap:Ethernet  HWaddr 70:71:bc:0e:57:a5  
          inet addr:  Bcast:  Mask:
          inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:782 (782.0 B)  TX bytes:7481 (7.4 KB)
          Interrupt:20 Memory:fb100000-fb120000 

lo        Link encap:Local Loopback  
          inet addr: Mask:
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by sashwath on 2011-01-18
i hav deleted the values of ip addr and others from the above msg for security reasons.

---

### Post by dineshs on 2011-01-18
It will be difficult for us to help you unless you post the output of all the commands.Can you ping 4.2.2.1  or 66.102.7.83 ?Do you see a gateway when route -n command is given?
> i hav deleted the values of ip addr and others from the above msg for security reasons.Is it a public IP?

---

### Post by mips on 2011-01-19
> **sashwath said:**
> i hav deleted the values of ip addr and others from the above msg for security reasons.

If it's not a public address they might help us determining the problem.

If the address starts with 192.168.xxx.xxx, 10.xxx.xxx.xxx, 169.254.xxx.xxx, 127.0.0.0, 172.16.0.0 – 172.31.255.255 it's safe to post here.

---

### Post by sashwath on 2011-01-19
ip addr is 192.168.1.101

---

### Post by mips on 2011-01-19
Post the output of the following commands here:
ifconfig -a
ip addr show
ip route show
netstat -nr
cat /etc/hosts
cat /etc/resolv.conf
sudo ethtool eth0 (Change eth0 to eth1 or whatever your lan port number is, you will have to install ethtool if not installed already with sudo apt-get install ethtool if not installed already)


What make & model cable router/modem are you using?
Who is your ISP and what service of theirs are you using, provide a link please?

---

### Post by sashwath on 2011-01-20
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 70:71:bc:0e:57:a5  
          inet addr:192.168.1.110  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:573 (573.0 B)  TX bytes:7240 (7.2 KB)
          Interrupt:20 Memory:fb100000-fb120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ip addr show:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 70:71:bc:0e:57:a5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.110/16 brd 192.168.255.255 scope global eth0
    inet6 fe80::7271:bcff:fe0e:57a5/64 scope link 
       valid_lft forever preferred_lft forever

ip route show:
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.1.110  metric 1 

netstat -nr:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0


cat /etc/hosts:
192.168.2.50    sashwath-desktop    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    sashwath-desktop    localhost6.localdomain6    localhost6
127.0.1.1    sashwath-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

cat /etc/resolv.conf:
# Generated by NetworkManager
search 208.67.222.222
nameserver 192.168.1.1

---

### Post by sashwath on 2011-01-20
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 70:71:bc:0e:57:a5  
          inet addr:192.168.1.110  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:573 (573.0 B)  TX bytes:7240 (7.2 KB)
          Interrupt:20 Memory:fb100000-fb120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ip addr show:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 70:71:bc:0e:57:a5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.110/16 brd 192.168.255.255 scope global eth0
    inet6 fe80::7271:bcff:fe0e:57a5/64 scope link 
       valid_lft forever preferred_lft forever

ip route show:
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.1.110  metric 1 

netstat -nr:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0


cat /etc/hosts:
192.168.2.50    sashwath-desktop    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    sashwath-desktop    localhost6.localdomain6    localhost6
127.0.1.1    sashwath-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

cat /etc/resolv.conf:
# Generated by NetworkManager
search 208.67.222.222
nameserver 192.168.1.1

---

### Post by sashwath on 2011-01-20
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 70:71:bc:0e:57:a5  
          inet addr:192.168.1.110  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:573 (573.0 B)  TX bytes:7240 (7.2 KB)
          Interrupt:20 Memory:fb100000-fb120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ip addr show:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 70:71:bc:0e:57:a5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.110/16 brd 192.168.255.255 scope global eth0
    inet6 fe80::7271:bcff:fe0e:57a5/64 scope link 
       valid_lft forever preferred_lft forever

ip route show:
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.1.110  metric 1 

netstat -nr:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0


cat /etc/hosts:
192.168.2.50    sashwath-desktop    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    sashwath-desktop    localhost6.localdomain6    localhost6
127.0.1.1    sashwath-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

cat /etc/resolv.conf:
# Generated by NetworkManager
search 208.67.222.222
nameserver 192.168.1.1

---

### Post by sashwath on 2011-01-20
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 70:71:bc:0e:57:a5  
          inet addr:192.168.1.110  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:573 (573.0 B)  TX bytes:7240 (7.2 KB)
          Interrupt:20 Memory:fb100000-fb120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ip addr show:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 70:71:bc:0e:57:a5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.110/16 brd 192.168.255.255 scope global eth0
    inet6 fe80::7271:bcff:fe0e:57a5/64 scope link 
       valid_lft forever preferred_lft forever

ip route show:
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.1.110  metric 1 

netstat -nr:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0


cat /etc/hosts:
192.168.2.50    sashwath-desktop    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    sashwath-desktop    localhost6.localdomain6    localhost6
127.0.1.1    sashwath-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

cat /etc/resolv.conf:
# Generated by NetworkManager
search 208.67.222.222
nameserver 192.168.1.1

---

### Post by sashwath on 2011-01-20
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 70:71:bc:0e:57:a5  
          inet addr:192.168.1.110  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:573 (573.0 B)  TX bytes:7240 (7.2 KB)
          Interrupt:20 Memory:fb100000-fb120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0


          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ip addr show:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 70:71:bc:0e:57:a5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.110/16 brd 192.168.255.255 scope global eth0
    inet6 fe80::7271:bcff:fe0e:57a5/64 scope link 
       valid_lft forever preferred_lft forever

ip route show:
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.1.110  metric 1 

netstat -nr:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0


cat /etc/hosts:
192.168.2.50    sashwath-desktop    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    sashwath-desktop    localhost6.localdomain6    localhost6
127.0.1.1    sashwath-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

cat /etc/resolv.conf:
# Generated by NetworkManager
search 208.67.222.222
nameserver 192.168.1.1

sterlite smartax mt882 modem.
 isp:bsnl

---

### Post by sashwath on 2011-01-20
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 70:71:bc:0e:57:a5  
          inet addr:192.168.1.110  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:573 (573.0 B)  TX bytes:7240 (7.2 KB)
          Interrupt:20 Memory:fb100000-fb120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0


          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ip addr show:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 70:71:bc:0e:57:a5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.110/16 brd 192.168.255.255 scope global eth0
    inet6 fe80::7271:bcff:fe0e:57a5/64 scope link 
       valid_lft forever preferred_lft forever

ip route show:
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.1.110  metric 1 

netstat -nr:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0


cat /etc/hosts:
192.168.2.50    sashwath-desktop    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    sashwath-desktop    localhost6.localdomain6    localhost6
127.0.1.1    sashwath-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

cat /etc/resolv.conf:
# Generated by NetworkManager
search 208.67.222.222
nameserver 192.168.1.1

sterlite smartax mt882 modem.
 isp:bsnl

---

### Post by sashwath on 2011-01-20
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 70:71:bc:0e:57:a5  
          inet addr:192.168.1.110  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:573 (573.0 B)  TX bytes:7240 (7.2 KB)
          Interrupt:20 Memory:fb100000-fb120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0


          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ip addr show:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 70:71:bc:0e:57:a5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.110/16 brd 192.168.255.255 scope global eth0
    inet6 fe80::7271:bcff:fe0e:57a5/64 scope link 
       valid_lft forever preferred_lft forever

ip route show:
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.1.110  metric 1 

netstat -nr:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0


cat /etc/hosts:
192.168.2.50    sashwath-desktop    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    sashwath-desktop    localhost6.localdomain6    localhost6
127.0.1.1    sashwath-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

cat /etc/resolv.conf:
# Generated by NetworkManager
search 208.67.222.222
nameserver 192.168.1.1

sterlite smartax mt882 modem.
 isp:bsnl

---

### Post by sashwath on 2011-01-20
ifconfig -a:
eth0      Link encap:Ethernet  HWaddr 70:71:bc:0e:57:a5  
          inet addr:192.168.1.110  Bcast:192.168.255.255  Mask:255.255.0.0
          inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:573 (573.0 B)  TX bytes:7240 (7.2 KB)
          Interrupt:20 Memory:fb100000-fb120000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0


          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ip addr show:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether 70:71:bc:0e:57:a5 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.110/16 brd 192.168.255.255 scope global eth0
    inet6 fe80::7271:bcff:fe0e:57a5/64 scope link 
       valid_lft forever preferred_lft forever

ip route show:
169.254.0.0/16 dev eth0  scope link  metric 1000 
192.168.0.0/16 dev eth0  proto kernel  scope link  src 192.168.1.110  metric 1 

netstat -nr:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0


cat /etc/hosts:
192.168.2.50    sashwath-desktop    # Added by NetworkManager
127.0.0.1    localhost.localdomain    localhost
::1    sashwath-desktop    localhost6.localdomain6    localhost6
127.0.1.1    sashwath-desktop

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

cat /etc/resolv.conf:
# Generated by NetworkManager
search 208.67.222.222
nameserver 192.168.1.1

sterlite smartax mt882 modem.
 isp:bsnl

---

### Post by sashwath on 2011-01-20
ifconfig -a:
eth0 Link encap:Ethernet HWaddr 70:71:bc:0e:57:a5
inet addr:192.168.1.110 Bcast:192.168.255.255 Mask:255.255.0.0
inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:573 (573.0 B) TX bytes:7240 (7.2 KB)
Interrupt:20 Memory:fb100000-fb120000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0


TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

ip addr show:
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN
link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
inet 127.0.0.1/8 scope host lo
inet6 ::1/128 scope host
valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
link/ether 70:71:bc:0e:57:a5 brd ff:ff:ff:ff:ff:ff
inet 192.168.1.110/16 brd 192.168.255.255 scope global eth0
inet6 fe80::7271:bcff:fe0e:57a5/64 scope link
valid_lft forever preferred_lft forever

---

### Post by sashwath on 2011-01-20
eth0 Link encap:Ethernet HWaddr 70:71:bc:0e:57:a5
inet addr:192.168.1.110 Bcast:192.168.255.255 Mask:255.255.0.0
inet6 addr: fe80::7271:bcff:fe0e:57a5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:5 errors:0 dropped:0 overruns:0 frame:0
TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:573 (573.0 B) TX bytes:7240 (7.2 KB)
Interrupt:20 Memory:fb100000-fb120000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0


TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

---

### Post by sashwath on 2011-01-20
sorry for quoting so many times.didnt realise it went to page 2 and thought it was an eroor.

---

### Post by dineshs on 2011-01-20
> my net worx fine on win7.i copied the values of ip address,netmask and others to ubuntu.it connects but the page doesnt load.help!!!
While configuring the connection via network manager you should hit [COLOR="Red"]enter[/COLOR] after assigning gateway .The exact procedure is [here]("http://ubuntuforums.org/showpost.php?p=9467538&postcount=5")
If the connection still doesnt work please post the result of ```
ping -c3 192.168.1.1
```and ```
ping -c3 4.2.2.1
```(Hope your gateway is 192.168.1.1

---

### Post by sashwath on 2011-01-21
ping -c3 192.168.1.1:
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=128 time=5.62 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=128 time=0.516 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=128 time=0.479 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.479/2.206/5.625/2.417 ms

ping -c3 4.2.2.1:
sashwath@sashwath-desktop:~$ ping -c3 4.2.2.1
connect: Network is unreachable

---

### Post by ripat on 2011-01-21
You have no route to your gateway. First try this:
```
$ sudo ip route add default via 192.168.1.1
```

If it works (i.e. you are connected to internet) we will see why the route is not automatically build when you request an ip.

---

### Post by mips on 2011-01-21
> **sashwath said:**
> 
netstat -nr:
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
192.168.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0

You have no default gateway.
You should have another line that reads:
0.0.0.0         192.168.0.1     0.0.0.0         UG        0 0          0 eth0

---

### Post by dineshs on 2011-01-21
> .i copied the values of ip address,netmask and others to ubuntu.How did you do that?via network manager?or by editing /etc/network/interfaces?Did you do what I suggested ie hit enter after giving gateway IP? 
What is the output of ```
route -n
```now?Do you use a PPPoE dialler in windows?

---

### Post by ripat on 2011-01-21
@dineshs routing tables have been posted (several) times above. (S)He has not route to the gateway.

@ OP Just try to add that route as I suggested above, and then we will see why the route is not build as it should.

---

### Post by dineshs on 2011-01-21
yeah I understand.I was suggesting how to assign gateway.(ie The reason for not showing gateway)There is a problem with network manager that if you do not hit Enter after typing gateway then it wont work.eg [http://ubuntuforums.org/showthread.php?t=1555373&highlight=gateway](http://ubuntuforums.org/showthread.php?t=1555373&highlight=gateway)

---

