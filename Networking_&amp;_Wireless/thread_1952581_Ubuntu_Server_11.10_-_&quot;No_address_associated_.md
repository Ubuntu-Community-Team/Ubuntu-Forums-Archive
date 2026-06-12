---
title: "Ubuntu Server 11.10 - &quot;No address associated with hostname&quot;"
date: 2012-04-04
forum: Networking &amp; Wireless
---

### Post by charliearthur on 2012-04-04
I have seen this issue floating around the forums but none of the resolutions have worked for me.

I am able to SSH into the server fine and can ping out to local network IPs but unable to access any external IPs from the server via name or IP.


ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 00:14:22:52:0c:b1
          inet addr:10.247.49.110  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fe52:cb1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:444102 errors:0 dropped:4784 overruns:0 frame:0
          TX packets:9551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:38337499 (38.3 MB)  TX bytes:745064 (745.0 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:252742 (252.7 KB)  TX bytes:252742 (252.7 KB)
```traceroute 8.8.8.8

```
The program 'traceroute' is currently not installed.  You can install it by typing:
sudo apt-get install traceroute
administrator@itlocallamp:~$ sudo apt-get install traceroute
[sudo] password for administrator:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  traceroute
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 49.6 kB of archives.
After this operation, 176 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  traceroute
Install these packages without verification [y/N]? y
Err http://us.archive.ubuntu.com/ubuntu/ oneiric/universe traceroute i386 1:2.0.15-1
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/t/traceroute/traceroute_2.0.15-1_i386.deb  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```etc/hosts

```
127.0.0.1       localhost
127.0.1.1       itlocallamp

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
Let me know if any other commands need to be ran. Thanks!  ](*,)

---

### Post by charliearthur on 2012-04-05
Any help on this issue? Thanks.

---

