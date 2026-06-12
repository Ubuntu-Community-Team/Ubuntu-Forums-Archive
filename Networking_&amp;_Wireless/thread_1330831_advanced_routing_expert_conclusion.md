---
title: "advanced routing expert conclusion"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by badfiles on 2009-11-18
I would like to listen to an opinion of an expert in advanced routing (iproute2) area. 

I've been trying to dig into the subject for a week, but I get the same result on 9.10 32bit server system -- if second provider is isolated in alternate routing table, there is completely no way to initiate a connection through the second provider's gateway.

Tried rp_filter on all interfaces 0 and 1.
Tried starting routed and local sessions. 

I also made sure the second provider's network is able to serve mine, and I CAN work through it if I have the second provider as a specific or default route in main table.

The common direction to detect a problem for an expert is here

cat rt_tables
```
#
# reserved values
#
255	local
254	main
253	default
0	unspec
#
# local
#
#1	inr.ruhep

10 * * *isp2

```

ip rule list```

0:	from all lookup local 
32764:	from all fwmark 0xde lookup isp2 
32765:	from 92.105.39.245 lookup isp2 
32766:	from all lookup main 
32767:	from all lookup default

```
ip route list table main```

4.2.109.48/28 dev eth2.5 *scope link *src 4.2.109.51
10.10.15.0/24 dev tap0 *proto kernel *scope link *src 10.10.15.1 
10.10.10.0/24 dev eth2 *proto kernel *scope link *src 10.10.10.111 
10.10.11.0/24 dev eth2.2 *proto kernel *scope link *src 10.10.11.1 
92.105.36.0/22 dev eth3 *scope link *src 92.105.39.245 
default via 4.2.109.49 dev eth2.5 
```

ip route list table isp2 ```

4.2.109.48/28 dev eth2.5 *scope link *src 4.2.109.51 
10.10.10.0/24 dev eth2 *scope link 
92.105.36.0/22 dev eth3 *scope link *src 92.105.39.245 
127.0.0.0/8 dev lo *scope link 
default via 92.105.36.1 dev eth3 
```

Commands
#ping -i eth2.5 94.25.208.252
#ping -i eth3 94.25.208.252
both have correct output.


Now I demonstrate the router's ability to work through the second provider issuing  ```
#ip route add default via 92.105.36.1 dev eth3 
```
and I have correct transit and local sessions
transit```

10:05:06.135306 *In 00:13:d3:3c:8e:99 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 64, id 60334, offset 0, flags [DF], proto TCP (6), length 60)
 * *10.10.10.4.42914 > 94.25.208.252.443: Flags [S,], cksum 0xc0b4 (correct), seq 2007693559, win 5840, options [mss 1460,sackOK,TS val 4953 ecr 0,nop,wscale 6], length 0
10:05:06.135358 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 63, id 60334, offset 0, flags [DF], proto TCP (6), length 60)
 * *92.105.39.245.42914 > 94.25.208.252.443: Flags [S,], cksum 0x3e64 (correct), seq 2007693559, win 5840, options [mss 1460,sackOK,TS val 4953 ecr 0,nop,wscale 6], length 0
10:05:06.275763 *In 00:24:91:3c:0e:f5 ethertype IPv4 (0x0800), length 60: (tos 0x0, ttl 253, id 59969, offset 0, flags [DF], proto TCP (6), length 44)
 * *94.25.208.252.443 > 92.105.39.245.42914: Flags [S.], cksum 0x7895 (correct), seq 4225246341, ack 2007693560, win 8190, options [mss 1380], length 0
10:05:06.275797 Out 00:16:76:88:e5:30 ethertype IPv4 (0x0800), length 60: (tos 0x0, ttl 252, id 59969, offset 0, flags [DF], proto TCP (6), length 44)
 * *94.25.208.252.443 > 10.10.10.4.42914: Flags [S.], cksum 0xfae5 (correct), seq 4225246341, ack 2007693560, win 8190, options [mss 1380], length 0
10:05:06.275913 *In 00:13:d3:3c:8e:99 ethertype IPv4 (0x0800), length 62: (tos 0x10, ttl 64, id 60335, offset 0, flags [DF], proto TCP (6), length 40)
 * *10.10.10.4.42914 > 94.25.208.252.443: Flags [.], cksum 0x1b81 (correct), seq 1, ack 1, win 5840, length 0
10:05:06.275929 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 56: (tos 0x10, ttl 63, id 60335, offset 0, flags [DF], proto TCP (6), length 40)
 * *92.105.39.245.42914 > 94.25.208.252.443: Flags [.], cksum 0x9930 (correct), seq 1, ack 1, win 5840, length 0
10:05:07.972521 *In 00:13:d3:3c:8e:99 ethertype IPv4 (0x0800), length 62: (tos 0x10, ttl 64, id 60336, offset 0, flags [DF], proto TCP (6), length 45)
 * *10.10.10.4.42914 > 94.25.208.252.443: Flags [P.], cksum 0x1581 (correct), seq 1:6, ack 1, win 5840, length 5
10:05:07.972553 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 61: (tos 0x10, ttl 63, id 60336, offset 0, flags [DF], proto TCP (6), length 45)
 * *92.105.39.245.42914 > 94.25.208.252.443: Flags [P.], cksum 0x9330 (correct), seq 1:6, ack 1, win 5840, length 5
10:05:08.084804 *In 00:24:91:3c:0e:f5 ethertype IPv4 (0x0800), length 56: (tos 0x0, ttl 253, id 33625, offset 0, flags [DF], proto TCP (6), length 40)
 * *94.25.208.252.443 > 92.105.39.245.42914: Flags [R], cksum 0x8999 (correct), seq 4225246342, win 9838, length 0
10:05:08.084824 Out 00:16:76:88:e5:30 ethertype IPv4 (0x0800), length 56: (tos 0x0, ttl 252, id 33625, offset 0, flags [DF], proto TCP (6), length 40)
 * *94.25.208.252.443 > 10.10.10.4.42914: Flags [R], cksum 0x0bea (correct), seq 4225246342, win 9838, length 0
```

local```

10:05:45.547493 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 64, id 2285, offset 0, flags [DF], proto TCP (6), length 60)
 * *92.105.39.245.52819 > 94.25.208.252.443: Flags [S,], cksum 0x515d (correct), seq 1409121486, win 5384, options [mss 1346,sackOK,TS val 127693859 ecr 0,nop,wscale 6], length 0
10:05:45.635793 *In 00:24:91:3c:0e:f5 ethertype IPv4 (0x0800), length 60: (tos 0x0, ttl 253, id 26917, offset 0, flags [DF], proto TCP (6), length 44)
 * *94.25.208.252.443 > 92.105.39.245.52819: Flags [S.], cksum 0x0d3f (correct), seq 2196275737, ack 1409121487, win 8190, options [mss 1340], length 0
10:05:45.635840 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 56: (tos 0x10, ttl 64, id 2286, offset 0, flags [DF], proto TCP (6), length 40)
 * *92.105.39.245.52819 > 94.25.208.252.443: Flags [.], cksum 0x2f7a (correct), seq 1, ack 1, win 5384, length 0
10:05:47.039652 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 61: (tos 0x10, ttl 64, id 2287, offset 0, flags [DF], proto TCP (6), length 45)
 * *92.105.39.245.52819 > 94.25.208.252.443: Flags [P.], cksum 0x297a (correct), seq 1:6, ack 1, win 5384, length 5
10:05:47.135857 *In 00:24:91:3c:0e:f5 ethertype IPv4 (0x0800), length 56: (tos 0x0, ttl 253, id 36147, offset 0, flags [DF], proto TCP (6), length 40)
 * *94.25.208.252.443 > 92.105.39.245.52819: Flags [R], cksum 0x1e1b (correct), seq 2196275738, win 9838, length 0
```
please note that RST-packets generated by CTRL-C in terminal and are not failures.

Now I remove the newly created default route and mark desired traffic with 
iptables
```

*mangle
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A PREROUTING -p tcp -m tcp -s 10.10.10.0/24 -i eth2 --dport 443 -j MARK --set-mark 222
COMMIT

```

now local session looks good and goes through the first provider as it should```

10:35:13.316249 Out 00:16:76:88:e5:30 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 64, id 1879, offset 0, flags [DF], proto TCP (6), length 60)
 * *4.2.109.51.38910 > 94.25.208.252.443: Flags [S,], cksum 0x701d (correct), seq 3348247853, win 5840, options [mss 1460,sackOK,TS val 128135802 ecr 0,nop,wscale 6], length 0
10:35:13.327820 *In 00:14:a8:b9:c2:dd ethertype IPv4 (0x0800), length 62: (tos 0x0, ttl 248, id 49784, offset 0, flags [DF], proto TCP (6), length 44)
 * *94.25.208.252.443 > 4.2.109.51.38910: Flags [S.], cksum 0x9a19 (correct), seq 1143608109, ack 3348247854, win 8190, options [mss 1380], length 0
10:35:13.327863 Out 00:16:76:88:e5:30 ethertype IPv4 (0x0800), length 56: (tos 0x10, ttl 64, id 1880, offset 0, flags [DF], proto TCP (6), length 40)
 * *4.2.109.51.38910 > 94.25.208.252.443: Flags [.], cksum 0xbab4 (correct), seq 1, ack 1, win 5840, length 0
10:35:15.519648 Out 00:16:76:88:e5:30 ethertype IPv4 (0x0800), length 61: (tos 0x10, ttl 64, id 1881, offset 0, flags [DF], proto TCP (6), length 45)
 * *4.2.109.51.38910 > 94.25.208.252.443: Flags [P.], cksum 0xb4b4 (correct), seq 1:6, ack 1, win 5840, length 5
10:35:15.530943 *In 00:14:a8:b9:c2:dd ethertype IPv4 (0x0800), length 62: (tos 0x0, ttl 248, id 42640, offset 0, flags [DF], proto TCP (6), length 40)
 * *94.25.208.252.443 > 4.2.109.51.38910: Flags [R], cksum 0xab1d (correct), seq 1143608110, win 9838, length 0
```

with transit session I have the described problem. The system continuously tries to initiate connection
```

10:34:27.739510 *In 00:13:d3:3c:8e:99 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 64, id 54853, offset 0, flags [DF], proto TCP (6), length 60)
 * *10.10.10.4.41405 > 94.25.208.252.443: Flags [S,], cksum 0x3d7a (correct), seq 3819744659, win 5840, options [mss 1460,sackOK,TS val 293846 ecr 0,nop,wscale 6], length 0
10:34:27.743881 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 63, id 54853, offset 0, flags [DF], proto TCP (6), length 60)
 * *92.105.39.245.41405 > 94.25.208.252.443: Flags [S,], cksum 0xbb29 (correct), seq 3819744659, win 5840, options [mss 1460,sackOK,TS val 293846 ecr 0,nop,wscale 6], length 0
10:34:27.981953 *In 00:24:91:3c:0e:f5 ethertype IPv4 (0x0800), length 60: (tos 0x0, ttl 253, id 45716, offset 0, flags [DF], proto TCP (6), length 44)
 * *94.25.208.252.443 > 92.105.39.245.41405: Flags [S.], cksum 0xb233 (correct), seq 2156546940, ack 3819744660, win 8190, options [mss 1380], length 0
10:34:30.738952 *In 00:13:d3:3c:8e:99 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 64, id 54854, offset 0, flags [DF], proto TCP (6), length 60)
 * *10.10.10.4.41405 > 94.25.208.252.443: Flags [S,], cksum 0x3a8c (correct), seq 3819744659, win 5840, options [mss 1460,sackOK,TS val 294596 ecr 0,nop,wscale 6], length 0
10:34:30.738975 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 63, id 54854, offset 0, flags [DF], proto TCP (6), length 60)
 * *92.105.39.245.41405 > 94.25.208.252.443: Flags [S,], cksum 0xb83b (correct), seq 3819744659, win 5840, options [mss 1460,sackOK,TS val 294596 ecr 0,nop,wscale 6], length 0
 *...........................................

```

Now I check what happens with local sessions, if put them through table isp2
```

*mangle
:FORWARD ACCEPT [0:0]
:INPUT ACCEPT [0:0]
:OUTPUT ACCEPT [0:0]
:PREROUTING ACCEPT [0:0]
:POSTROUTING ACCEPT [0:0]
-A PREROUTING -p tcp -m tcp -s 10.10.10.0/24 -i eth2 --dport 443 -j MARK *--set-mark 222
-A OUTPUT -p tcp -m tcp --dport 443 -j MARK --set-mark 222
```

Now I have a fault with local sessions too.
```

10:54:49.524716 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 64, id 38958, offset 0, flags [DF], proto TCP (6), length 60)
 * *92.105.39.245.50909 > 94.25.208.252.443: Flags [S,], cksum 0xa22f (correct), seq 318715696, win 5840, options [mss 1460,sackOK,TS val 128429854 ecr 0,nop,wscale 6], length 0
10:54:49.620363 *In 00:24:91:3c:0e:f5 ethertype IPv4 (0x0800), length 60: (tos 0x0, ttl 253, id 19614, offset 0, flags [DF], proto TCP (6), length 44)
 * *94.25.208.252.443 > 92.105.39.245.50909: Flags [S.], cksum 0x1f13 (correct), seq 2320037583, ack 318715697, win 8190, options [mss 1380], length 0
10:54:52.523577 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 64, id 38959, offset 0, flags [DF], proto TCP (6), length 60)
 * *92.105.39.245.50909 > 94.25.208.252.443: Flags [S,], cksum 0x9f41 (correct), seq 318715696, win 5840, options [mss 1460,sackOK,TS val 128430604 ecr 0,nop,wscale 6], length 0
10:54:52.615771 *In 00:24:91:3c:0e:f5 ethertype IPv4 (0x0800), length 60: (tos 0x0, ttl 253, id 48056, offset 0, flags [DF], proto TCP (6), length 44)
 * *94.25.208.252.443 > 92.105.39.245.50909: Flags [S.], cksum 0x1f13 (correct), seq 2320037583, ack 318715697, win 8190, options [mss 1380], length 0
10:54:58.523605 Out 00:24:91:3c:0e:f4 ethertype IPv4 (0x0800), length 76: (tos 0x10, ttl 64, id 38960, offset 0, flags [DF], proto TCP (6), length 60)
 * *92.105.39.245.50909 > 94.25.208.252.443: Flags [S,], cksum 0x9965 (correct), seq 318715696, win 5840, options [mss 1460,sackOK,TS val 128432104 ecr 0,nop,wscale 6], length 0
10:54:58.620907 *In 00:24:91:3c:0e:f5 ethertype IPv4 (0x0800), length 60: (tos 0x0, ttl 253, id 25609, offset 0, flags [DF], proto TCP (6), length 44)
 * *94.25.208.252.443 > 92.105.39.245.50909: Flags [S.], cksum 0x1f13 (correct), seq 2320037583, ack 318715697, win 8190, options [mss 1380], length 0
..............................................................................

```

In addition, I tried to switch providers. The results also switched.
Just copying default route from isp2 into main makes the second provider work quite well, but then of course the first stops working.

---

### Post by Eguiguren on 2010-09-16
I have the same problem. SYN packets are marked correctly and goes throught the alternate table gateway, SYN/ACK returns and reach the external router's interface and disappears. Looks like if the router shouldn't know how to follow the SYN/ACK to the client's LAN. 

I wanna send SSH and FTP traffic thorugh the 10.10.2.254 gateway while the rest should go out through the 10.10.1.254 gw. 

rt_table includes:
```
20 sshftp
```This same script works on Debian 5.06 as is ](*,)

The script I use is the following:
```
#!/bin/bash -x

case $1 in 
        start)
                $0 stop  
                iptables -A PREROUTING -t mangle -p tcp --dport 22 -m state --state NEW,RELATED,ESTABLISHED -j MARK --set-mark 1
                iptables -A PREROUTING -t mangle -p tcp --dport 21 -m state --state NEW,RELATED,ESTABLISHED -j MARK --set-mark 2
                iptables -A OUTPUT -t mangle -p tcp --dport 22 -j MARK --set-mark 1
                iptables -A OUTPUT -t mangle -p tcp --dport 21 -j MARK --set-mark 1

                while read line ; do
                        test -z "${line##default*}" && continue
                        test -z "${line##nexthop*}" && continue
                        ip route add $line table sshftp
                done < \
                <(/sbin/ip route ls table main)

                /sbin/ip route add default via 10.10.2.254 dev eth1 table sshftp

                ip rule add fwmark 1 table sshftp
                ip rule add fwmark 2 table sshftp
                ip route flush cache
        ;;

        stop)
                ip route flush table sshftp
                ip route flush table back
                ip rule del fwmark 1 table sshftp
                ip rule del fwmark 2 table sshftp
                iptables -D PREROUTING -t mangle -p tcp --dport 22 -m state --state NEW,RELATED,ESTABLISHED -j MARK --set-mark 1
                iptables -D PREROUTING -t mangle -p tcp --dport 21 -m state --state NEW,RELATED,ESTABLISHED -j MARK --set-mark 2
                iptables -D OUTPUT 1
                iptables -D OUTPUT 1
                
        ;;
        *) 
                $0 start
        ;;

esac
```Tried to use Ubuntu 10.04 lucid and iproute deb version is 20091226-1. This is the faulty one.

In Debian 5.06 iproute deb version is 20080725-2 worked OK.

Hope anybody knows something about it. I'm still seeking at iproute manteiners' lists.

Regards ):P

---

### Post by Eguiguren on 2010-09-17
I've found [http://www.linuxforums.org/forum/linux-networking/153506-solved-iproute2-rule-based-multi-homed-snat-problem.html ]("http://www.linuxforums.org/forum/linux-networking/153506-solved-iproute2-rule-based-multi-homed-snat-problem.html")

I've set in /etc/sysctl.conf to 0:
```
net.ipv4.conf.default.rp_filter=0
net.ipv4.conf.all.rp_filter=0

```

Run ```
# sysctl -p
``` to refresh with the new configuration and it worked

---

