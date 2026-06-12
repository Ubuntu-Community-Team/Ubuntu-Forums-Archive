---
title: "Networking issue (ssh access but no internet)"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by tredrex on 2009-12-02
Hello Everyone,

**Summary: **

I cannot connect to the internet from my machine through a wired connection. I can,  however, SSH into it from a remote machine.  

**Environment:** 
[LIST=1]
[*]* Karmic - upgraded a week ago and it had been working fine. 
[*]* Static ip 
[*]* Connects to the internet through a Linksys WRGT router via a WIRED connection
[/LIST]

**Diagnosis: **

Here are the outputs of several commands that I used to diagnose the issue (without much success)

IFCONFIG 
[HTML]
developer@www:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:90:b8:01:00  
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:feb8:100/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:927164 (927.1 KB)  TX bytes:123018 (123.0 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
[/HTML]

NETSTAT
[HTML]
developer@www:~$ netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0
[/HTML]

MTR
[HTML]
developer@www:~$ mtr -n -c3 -r 4.4.4.4
No nameservers defined.
[/HTML]

Content of /etc/hosts
[HTML]
127.0.0.1       www.domainname.com    localhost.localdomain   localhost
127.0.1.1       www.domainname.com    domainname.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/HTML]

LSHW
[HTML]
developer@www:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801G (ICH7 Family) LAN Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 01
       serial: 00:1e:90:b8:01:00
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.250 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:febfe000-febfefff ioport:e880(size=64)
[/HTML]

Content of /etc/network/interfaces
[HTML]
auto eth0
iface eth0 inet static 
address 192.168.1.250
netmask 255.255.255.0
gateway 192.168.1.1
[/HTML]

Notes:
* A week after upgrading to karmic I seem to have run into some networking issues (its more likely something I did rather than the upgrade).
* I'm guessing its not a firewall issue seeing as how I can connect to it from a remote machine.


Any pointers/help would be greatly appreciated.

Thank you

---

### Post by RedSingularity on 2009-12-03
Well since you can SSH to it that means the connection is working.  Try to ping google with the following commands.

ping -c 5 [www.google.com](www.google.com)

ping -c 5 66.249.80.104

See if any of those work.

---

### Post by Iowan on 2009-12-03
> **tredrex said:**
> developer@www:~$ mtr -n -c3 -r 4.4.4.4
No nameservers defined.
Not a command I'm familiar with - but "No nameservers defined" sounds like a problem. Verify that by checking **/etc/resolv.conf**. If no nameservers there, the pings will probably succeed by IP address, but fail by name.

---

### Post by tredrex on 2009-12-03
Looks like that is the issue. Any ideas on how to resolve it. 

/etc/resolv.conf is empty 

[HTML]
developer@www:~$ ping -c 5 www.google.com
ping: unknown host www.google.com
developer@www:~$ ping -c 5 66.249.80.104
PING 66.249.80.104 (66.249.80.104) 56(84) bytes of data.
64 bytes from 66.249.80.104: icmp_seq=1 ttl=54 time=16.0 ms
64 bytes from 66.249.80.104: icmp_seq=2 ttl=54 time=15.5 ms
64 bytes from 66.249.80.104: icmp_seq=3 ttl=54 time=16.3 ms
64 bytes from 66.249.80.104: icmp_seq=4 ttl=54 time=16.6 ms
64 bytes from 66.249.80.104: icmp_seq=5 ttl=54 time=16.1 ms

--- 66.249.80.104 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 15.512/16.148/16.612/0.389 ms
[/HTML]

Thanks for helping me figure this out.

---

### Post by tredrex on 2009-12-03
The google tells me its this [openvpn bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/96260"). Makes sense because I was trying to install openvpn when I lost the network connection.

Still don't know how to resolve it though.

---

### Post by tredrex on 2009-12-03
Aha .. resolv.conf contains the nameservers. Usually this is set by resolvconf when it runs and it overrides any manual changes. 

I added the following line to /etc/network/interfaces
[HTML]
dns-nameservers xxx.xxx.xxx.xxx yyy.yyy.yyy.yyy
[/HTML]
where x and y are the addresses of the nameservers and this resolved the issue. 

I can connect to the interweb's tubes again. 

Thanks for you help guys.

---

