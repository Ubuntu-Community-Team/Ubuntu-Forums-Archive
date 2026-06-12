---
title: "root non-root difference when ping localhost"
date: 2006-07-08
forum: Networking &amp; Wireless
---

### Post by tablespoon on 2006-07-08
Hi,

I have a little problem when trying to 'ping localhost' as a non-root user, but 'ping localhost' under sudo works. Non-root
can ping outside though. This prevents me from using any
X client on the Breezy server. I am new to Ubuntu, is there any security reason behind this? Thanks.

```
user@myhost:~$ ping localhost
ping: unknown host localhost
user@myhost:~$ sudo ping -c 1 localhost
PING localhost.localdomain (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost.localdomain (127.0.0.1): icmp_seq=1 ttl=64 time=0.027 ms
                                                                                                   
--- localhost.localdomain ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.027/0.027/0.027/0.000 ms
user@myhost:~$ cat -v /etc/hosts
127.0.0.1       localhost.localdomain   localhost myhost
                                                                                                   
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
user@myhost:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.99    0.0.0.0         UG    0      0        0 eth0
user@myhost:~$ uname -a
Linux myhost 2.6.12-10-amd64-k8-smp #1 SMP Mon Jun 12 21:11:10 UTC 2006 x86_64 GNU/Linux 
```

---

### Post by tablespoon on 2006-07-09
i figured it out. Some of the /etc files's permission  has been somehow screwed. It could be because i installed some application packages. Now it works consistently between root and non-root users. Thanks.

---

