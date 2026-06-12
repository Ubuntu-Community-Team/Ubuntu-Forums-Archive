---
title: "host name resolution broken"
date: 2009-03-26
forum: Networking &amp; Wireless
---

### Post by djshaw on 2009-03-26
Hey,

I have three computers in my network. Two running ubuntu (culsu and chaos), one running windows (halphas). On my windows box, I can ssh into chaos or culsu just fine. However, on culsu, I cannot ssh into chaos and on chaos, I cannot ssh into culsu.

On the windows box, when I ping chaos I get 
> 
$ ping chaos

Pinging chaos [192.168.1.109] with 32 bytes of data:

Reply from 192.168.1.109: bytes=32 time<1ms TTL=64


and when I ping culsu I get
> 
$ ping culsu

Pinging culsu [192.168.1.139] with 32 bytes of data:

Reply from 192.168.1.139: bytes=32 time=38ms TTL=64


However, when culsu pings chaos, it resolves the wrong ip address
> 
djshaw@culsu:~$ ping chaos
PING chaos (8.15.7.107) 56(84) bytes of data.


chaos cannot ping culsu
> 
djshaw@chaos:~$ ping culsu
PING culsu (8.15.7.107) 56(84) bytes of data.


In fact, whenever chaos or culsu trys to ping any box, it resolves the host ip address to 8.15.7.107.

I think that [this]("http://forums.somethingawful.com/showthread.php?threadid=2907018") might have something to do with it.

Does anyone know what's going on here?

---

### Post by superprash2003 on 2009-03-27
do you have multiple interfaces on your computer.  in your terminal type** ifconfig** and post output

---

### Post by djshaw on 2009-03-27
> **superprash2003 said:**
> do you have multiple interfaces on your computer.  in your terminal type** ifconfig** and post output
.
> 
djshaw@culsu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0e:a6:46:0e:6d
          inet addr:192.168.1.139  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fe46:e6d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7184185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5556887 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4161361142 (4.1 GB)  TX bytes:2393657842 (2.3 GB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:40460 (40.4 KB)  TX bytes:40460 (40.4 KB)


---

### Post by Iowan on 2009-03-27
On culsu, what is in /etc/hosts, and /etc/resolv.conf?

---

### Post by djshaw on 2009-03-27
> **Iowan said:**
> On culsu, what is in /etc/hosts, and /etc/resolv.conf?

The issue has seems to have resolved itself. pinging chaos from culsu and pinging culsu from chaos works now. I do not know why 

For completeness, 

> 
djshaw@culsu:~$ cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       culsu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
djshaw@culsu:~$ cat /etc/resolv.conf
nameserver 192.168.1.1



Thanks for the help.

---

### Post by djshaw on 2009-04-13
So the same problem started to occur again.

I took a look at /etc/resolv.conf and found:
> 
domain phub.net.cable.rogers.com
search phub.net.cable.rogers.com
nameserver 192.168.1.1


What I think I need to do is remove the first two lines. I removed the two lines and then everything appeared to work properly. Does anyone know how I can prevent the domain and search addresses from appearing?

---

### Post by Iowan on 2009-04-14
Static IP addresses or DHCP?
 If DHCP, there's a PREPEND line in */etc/dhcp3/dhclient.conf* that ***should*** at least make your nameserver first.

---

### Post by djshaw on 2009-04-14
> **Iowan said:**
> Static IP addresses or DHCP?
 If DHCP, there's a PREPEND line in */etc/dhcp3/dhclient.conf* that ***should*** at least make your nameserver first.

I've added "prepend domain-name-servers 192.168.1.1;" to my dhclient.conf file. Do I need to restart any services? Will the change be picked the next time the dhcp client renews the lease on its ip address?

---

### Post by Iowan on 2009-04-14
It *should* pick it up next time the machine fires up... or you could try ```
/etc/init.d/networking restart
``` for a more immediate test.

---

### Post by djshaw on 2009-04-14
Cool, thanks.

---

