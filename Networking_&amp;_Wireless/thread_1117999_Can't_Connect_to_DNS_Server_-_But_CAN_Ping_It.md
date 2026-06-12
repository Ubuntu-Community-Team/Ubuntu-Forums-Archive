---
title: "Can't Connect to DNS Server - But CAN Ping It"
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by dgbauer on 2009-04-06
Hello all!  I have been fighting with this problem for a few weeks now, and I'm finally at the stumping point so I'm hoping someone out there can help me out.  I recently installed a server on our company's intranet and put it in a /29 network.  After fighting with the IP settings the server finally came online and was visible to the machines it needed to be, and it could ping the machines it needed to ping using their IP address.

The problem?  When I try to ping anything using the machine's DNS name, I get an 'unknown host' error.  I can ping my DNS servers and I have verified that my network configuration is correct...  But still no dice on resolving DNS names.  In the example below, test-server.corp.mycompany.com has an IP of 192.168.28.19
```

root@atom:~# ping test-server.corp.mycompany.com
ping: unknown host test-server.corp.mycompany.com

root@atom:~# ping -c 4 192.168.28.19
PING 192.168.28.19 (192.168.28.19) 56(84) bytes of data.
64 bytes from 192.168.28.19: icmp_seq=1 ttl=247 time=1.61 ms
64 bytes from 192.168.28.19: icmp_seq=2 ttl=247 time=1.67 ms
64 bytes from 192.168.28.19: icmp_seq=3 ttl=247 time=1.69 ms
64 bytes from 192.168.28.19: icmp_seq=4 ttl=247 time=1.42 ms

--- 192.168.28.19 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 1.423/1.601/1.697/0.118 ms

```I am using Ubuntu 8.04 LTS Server with the resolvconf package.

My /etc/network/interfaces file:
```

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 172.16.67.122
        netmask 255.255.255.248
        network 172.16.67.120/29
        broadcast 172.16.67.127
        gateway 172.16.67.121
        dns-nameservers 192.168.92.4 192.168.107.65
        dns-search corp.mycompany.com

```Ping responsese on nameserver IPs:
```

root@atom:~# ping -c 4 192.168.107.65
PING 192.168.107.65 (192.168.107.65) 56(84) bytes of data.
64 bytes from 192.168.107.65: icmp_seq=1 ttl=120 time=3.29 ms
64 bytes from 192.168.107.65: icmp_seq=2 ttl=120 time=4.63 ms
64 bytes from 192.168.107.65: icmp_seq=3 ttl=120 time=3.39 ms
64 bytes from 192.168.107.65: icmp_seq=4 ttl=120 time=3.40 ms

--- 192.168.107.65 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 3.294/3.680/4.632/0.554 ms

root@atom:~# ping -c 4 192.168.92.4
PING 192.168.92.4 (192.168.92.4) 56(84) bytes of data.
64 bytes from 192.168.92.4: icmp_seq=1 ttl=120 time=1.58 ms
64 bytes from 192.168.92.4: icmp_seq=2 ttl=120 time=1.54 ms
64 bytes from 192.168.92.4: icmp_seq=3 ttl=120 time=4.19 ms
64 bytes from 192.168.92.4: icmp_seq=4 ttl=120 time=1.42 ms

--- 192.168.92.4 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 1.427/2.188/4.198/1.162 ms

```When I try the dig command on either IP I get this:
```

root@atom:~# dig . ns @192.168.107.65

; <<>> DiG 9.4.2 <<>> . ns @192.168.107.65
;; global options:  printcmd
;; connection timed out; no servers could be reached

root@atom:~# dig . ns @192.168.92.4

; <<>> DiG 9.4.2 <<>> . ns @192.168.92.4
;; global options:  printcmd
;; connection timed out; no servers could be reached


```Anyone out there able to help me out?

---

### Post by dgbauer on 2009-04-22
I have resolved this issue.  UDP traffic on port 53 was blocked on the corporate firewall.  I discovered this using IPTraf and attempting to use nslookup on various domain names.

---

