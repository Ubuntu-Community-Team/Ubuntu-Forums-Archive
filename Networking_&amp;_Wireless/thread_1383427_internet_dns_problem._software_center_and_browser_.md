---
title: "internet dns problem. software center and browser doesnt work, but telnet is ok"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by nfnm on 2010-01-17
Hi All,

after i've setuped the ubuntu 9.10 i've found that the internet connection working incorrectly. i can ping or even connect to the internet sites with the telnet and see the raw html pages, but when i ran the software center or mozilla i have timeout error message. as a proxy settings i've setuped the direct connection in both system and mozilla proxy configurations but it takes no reason. if i put the ip address instead of the domain name in the address bar of the mozilla browser then its loaded the web page correctly.

it looks like this problem is relative to some system configuration of X about network (cause telnet google.com 80 working right), could any one gives me a suggestions please?

i'm using the dhcp connection to the D-Link DSL-504T router.

Thanks.

---

### Post by alexfish on 2010-01-17
have you tried playing around with the preferences network settings in the browser

---

### Post by nfnm on 2010-01-17
> **alexfish said:**
> have you tried playing around with the preferences network settings in the browser

the mozilla browser have only proxy configuration on the connection settings page. there i select the 'no proxy' option.
on the System->Administration->Network Proxy Preferences i set the 'direct internet connection'.

my physical connection goes over dsl router which have dhcp server. i can ping and even connect to the http servers via telnet. the main problem is that the gui programs couldn't resolve the domain names correctly, when i put the ip address in the mozilla then i have the page loaded, but its loaded partially cause some images is mentioned with the domain name.

this thing is relative to the 'Software Center' and 'Package Manager'.

Thanks.

---

### Post by alexfish on 2010-01-17
I am shooting in the dark here

what info can you get from 

Code:

route -n

Code:

dig "name"

added ;forgot what method do you use for your connection, it could be a permissions problem

---

### Post by nfnm on 2010-01-17
> **alexfish said:**
> I am shooting in the dark here

what info can you get from 

Code:

route -n

Code:

dig "name"

added ;forgot what method do you use for your connection, it could be a permissions problem

i'm using ethernet autoconfigured via dhcp server.

there are results:

user@user-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:d0:98:54  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fed0:9854/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42196 (42.1 KB)  TX bytes:34365 (34.3 KB)
          Interrupt:10 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


user@user-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0


user@user-desktop:~$ dig "name"

; <<>> DiG 9.6.1-P1 <<>> name
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 8484
;; flags: qr rd ra; QUERY: 1, ANSWER: 0, AUTHORITY: 1, ADDITIONAL: 0

;; QUESTION SECTION:
;name.				IN	A

;; AUTHORITY SECTION:
name.			235	IN	SOA	a3.nstld.com. hostmaster.nic.name. 203112899 10800 300 1209600 300

;; Query time: 40 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Jan 17 07:01:10 2010
;; MSG SIZE  rcvd: 85


user@user-desktop:~$ dig "google.com"

; <<>> DiG 9.6.1-P1 <<>> google.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 47349
;; flags: qr rd; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0
;; WARNING: recursion requested but not available

;; QUESTION SECTION:
;google.com.			IN	A

;; ANSWER SECTION:
google.com.		10000	IN	A	74.125.87.103

;; Query time: 2 msec
;; SERVER: 192.168.1.1#53(192.168.1.1)
;; WHEN: Sun Jan 17 07:01:33 2010
;; MSG SIZE  rcvd: 44

Thanks.

---

### Post by alexfish on 2010-01-17
hi
the error " WARNING: recursion requested but not available"

**telnet ** may operate a server that does recursive lookups: { OP thinks this not the case }

The first thing that you should do is turn off recursion if you don't need it. One way to determine this is with **DIG** command

You can look here

**RE: Name Resolution - Verifying**

[http://www.netadmintools.com/art592.html](http://www.netadmintools.com/art592.html)



**Note of interest :Verizon operates a well known server that does recursive lookups**

---

### Post by nfnm on 2010-01-17
could you please see this tcpdump logs
this is done with the telnet google.com 80

```
listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
08:38:49.689538 IP user-desktop.local.60407 > mygateway1.ar7.domain: 4847+ AAAA? google.com. (28)
08:38:49.691184 IP mygateway1.ar7.domain > user-desktop.local.60407: 4847- 1/0/0 (28)
08:38:49.691402 IP user-desktop.local.49996 > mygateway1.ar7.domain: 29412+ PTR? 1.1.168.192.in-addr.arpa. (42)
08:38:49.691663 IP user-desktop.local.55289 > mygateway1.ar7.domain: 14023+ A? google.com. (28)
08:38:49.693125 IP mygateway1.ar7.domain > user-desktop.local.49996: 29412- 1/0/0 (70)
08:38:49.694243 IP mygateway1.ar7.domain > user-desktop.local.55289: 14023- 1/0/0 A 74.125.87.104 (44)
08:38:49.707156 IP user-desktop.local.47819 > mygateway1.ar7.domain: 946+ PTR? 3.1.168.192.in-addr.arpa. (42)
08:38:49.707598 IP user-desktop.local.58117 > google.com.www: Flags [S], seq 695623124, win 5840, options [mss 1460,sackOK,TS val 1638582 ecr 0,nop,wscale 4], length 0
08:38:49.872890 IP google.com.www > user-desktop.local.58117: Flags [S.], seq 1357205349, ack 695623125, win 5672, options [mss 1360,sackOK,TS val 2521585303 ecr 1638582,nop,wscale 6], length 0
08:38:49.872994 IP user-desktop.local.58117 > google.com.www: Flags [.], ack 1, win 365, options [nop,nop,TS val 1638623 ecr 2521585303], length 0
08:38:53.602656 IP user-desktop.local.58117 > google.com.www: Flags [P.], seq 1:4, ack 1, win 365, options [nop,nop,TS val 1639556 ecr 2521585303], length 3
08:38:53.761278 IP google.com.www > user-desktop.local.58117: Flags [.], ack 4, win 89, options [nop,nop,TS val 2521589190 ecr 1639556], length 0
08:38:53.766634 IP google.com.www > user-desktop.local.58117: Flags [P.], seq 1:204, ack 4, win 89, options [nop,nop,TS val 2521589190 ecr 1639556], length 203
08:38:53.766670 IP user-desktop.local.58117 > google.com.www: Flags [.], ack 204, win 432, options [nop,nop,TS val 1639597 ecr 2521589190], length 0
08:38:53.772170 IP google.com.www > user-desktop.local.58117: Flags [.], seq 204:1552, ack 4, win 89, options [nop,nop,TS val 2521589192 ecr 1639556], length 1348
08:38:53.772190 IP user-desktop.local.58117 > google.com.www: Flags [.], ack 1552, win 613, options [nop,nop,TS val 1639598 ecr 2521589192], length 0
08:38:53.777009 IP google.com.www > user-desktop.local.58117: Flags [P.], seq 1552:1554, ack 4, win 89, options [nop,nop,TS val 2521589192 ecr 1639556], length 2
08:38:53.777039 IP user-desktop.local.58117 > google.com.www: Flags [.], ack 1554, win 613, options [nop,nop,TS val 1639599 ecr 2521589192], length 0
08:38:53.777741 IP google.com.www > user-desktop.local.58117: Flags [F.], seq 1554, ack 4, win 89, options [nop,nop,TS val 2521589192 ecr 1639556], length 0
08:38:53.777840 IP user-desktop.local.58117 > google.com.www: Flags [F.], seq 4, ack 1555, win 613, options [nop,nop,TS val 1639599 ecr 2521589192], length 0
08:38:53.937707 IP google.com.www > user-desktop.local.58117: Flags [.], ack 5, win 89, options [nop,nop,TS val 2521589366 ecr 1639599], length 0
08:38:54.712314 IP user-desktop.local.47819 > mygateway1.ar7.domain: 946+ PTR? 3.1.168.192.in-addr.arpa. (42)
08:38:59.719269 IP user-desktop.local.38588 > mygateway1.ar7.domain: 38747+ PTR? 104.87.125.74.in-addr.arpa. (44)
08:38:59.721027 IP mygateway1.ar7.domain > user-desktop.local.38588: 38747- 1/0/0 (68)
```

---

### Post by nfnm on 2010-01-17
and this is captured when i use the mozilla

```

listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes
08:42:20.230663 IP user-desktop.local.53628 > mygateway1.ar7.domain: 31883+ AAAA? fxfeeds.mozilla.com. (37)
08:42:20.232459 IP user-desktop.local.42667 > mygateway1.ar7.domain: 20660+ PTR? 1.1.168.192.in-addr.arpa. (42)
08:42:20.235075 IP mygateway1.ar7.domain > user-desktop.local.42667: 20660- 1/0/0 (70)
08:42:20.236492 IP user-desktop.local.39892 > mygateway1.ar7.domain: 54888+ PTR? 3.1.168.192.in-addr.arpa. (42)
08:42:20.271547 IP mygateway1.ar7.domain > user-desktop.local.53628: 31883 1/1/0 (119)
08:42:20.272109 IP user-desktop.local.54695 > mygateway1.ar7.domain: 46232+ A? fxfeeds.mozilla.com. (37)
08:42:20.273895 IP mygateway1.ar7.domain > user-desktop.local.54695: 46232- 1/0/0 (53)
08:42:25.228212 ARP, Request who-has user-desktop.local tell mygateway1.ar7, length 46
08:42:25.228254 ARP, Reply user-desktop.local is-at 00:e0:4c:d0:98:54 (oui Unknown), length 28
08:42:25.241487 IP user-desktop.local.39892 > mygateway1.ar7.domain: 54888+ PTR? 3.1.168.192.in-addr.arpa. (42)
08:42:30.238492 ARP, Request who-has mygateway1.ar7 tell user-desktop.local, length 28
08:42:30.238793 ARP, Reply mygateway1.ar7 is-at 00:11:95:d6:db:59 (oui Unknown), length 46
08:42:30.353543 IP user-desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 3.1.168.192.in-addr.arpa. (42)
08:42:30.353837 IP user-desktop.local.mdns > 224.0.0.251.mdns: 0*- [0q] 1/0/0 (Cache flush) PTR[|domain]
08:42:30.355133 IP user-desktop.local.41825 > mygateway1.ar7.domain: 57964+ PTR? 251.0.0.224.in-addr.arpa. (42)
08:42:31.204215 IP user-desktop.local.38000 > mygateway1.ar7.domain: 20110+ AAAA? google.com. (28)
08:42:31.242238 IP mygateway1.ar7.domain > user-desktop.local.38000: 20110 0/1/0 (78)
08:42:31.246791 IP user-desktop.local.42058 > mygateway1.ar7.domain: 10787+ AAAA? google.com. (28)
08:42:31.248737 IP mygateway1.ar7.domain > user-desktop.local.42058: 10787- 1/0/0 (28)
08:42:31.262789 IP user-desktop.local.46525 > mygateway1.ar7.domain: 53718+ A? google.com. (28)
08:42:31.264629 IP mygateway1.ar7.domain > user-desktop.local.46525: 53718- 1/0/0 A 1.0.0.0 (44)
08:42:31.307052 IP user-desktop.local.34327 > mygateway1.ar7.domain: 16972+ AAAA? www.google.com. (32)
08:42:31.347240 IP mygateway1.ar7.domain > user-desktop.local.34327: 16972 1/1/0 CNAME[|domain]
08:42:31.347551 IP user-desktop.local.52809 > mygateway1.ar7.domain: 58441+ A? www.google.com. (32)
08:42:31.351209 IP mygateway1.ar7.domain > user-desktop.local.52809: 58441- 1/0/0 A 1.0.0.0 (48)
08:42:31.351528 IP user-desktop.local.56866 > 1.0.0.0.www: Flags [S], seq 4179224101, win 5840, options [mss 1460,sackOK,TS val 1693993 ecr 0,nop,wscale 4], length 0
08:42:32.349694 IP mygateway1.ar7.domain > user-desktop.local.39892: 54888 ServFail- 0/0/0 (42)
08:42:32.349783 IP user-desktop.local > mygateway1.ar7: ICMP user-desktop.local udp port 39892 unreachable, length 78
08:42:34.350478 IP user-desktop.local.56866 > 1.0.0.0.www: Flags [S], seq 4179224101, win 5840, options [mss 1460,sackOK,TS val 1694743 ecr 0,nop,wscale 4], length 0
08:42:35.360296 IP user-desktop.local.41825 > mygateway1.ar7.domain: 57964+ PTR? 251.0.0.224.in-addr.arpa. (42)
08:42:40.350476 IP user-desktop.local.56866 > 1.0.0.0.www: Flags [S], seq 4179224101, win 5840, options [mss 1460,sackOK,TS val 1696243 ecr 0,nop,wscale 4], length 0
08:42:40.465453 IP user-desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
08:42:41.467238 IP user-desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
08:42:42.448477 IP mygateway1.ar7.domain > user-desktop.local.41825: 57964 ServFail- 0/0/0 (42)
08:42:42.448563 IP user-desktop.local > mygateway1.ar7: ICMP user-desktop.local udp port 41825 unreachable, length 78
08:42:43.472963 IP user-desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 251.0.0.224.in-addr.arpa. (42)
08:42:45.368277 IP user-desktop.local.55114 > mygateway1.ar7.domain: 10879+ PTR? 0.0.0.1.in-addr.arpa. (38)
08:42:50.373445 IP user-desktop.local.55114 > mygateway1.ar7.domain: 10879+ PTR? 0.0.0.1.in-addr.arpa. (38)
08:42:52.350456 IP user-desktop.local.56866 > 1.0.0.0.www: Flags [S], seq 4179224101, win 5840, options [mss 1460,sackOK,TS val 1699243 ecr 0,nop,wscale 4], length 0
08:42:55.370457 ARP, Request who-has mygateway1.ar7 tell user-desktop.local, length 28
08:42:55.370775 ARP, Reply mygateway1.ar7 is-at 00:11:95:d6:db:59 (oui Unknown), length 46
08:42:55.479332 IP user-desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 0.0.0.1.in-addr.arpa. (38)
08:42:56.428286 IP mygateway1.ar7.domain > user-desktop.local.55114: 10879 ServFail- 0/0/0 (38)
08:42:56.428372 IP user-desktop.local > mygateway1.ar7: ICMP user-desktop.local udp port 55114 unreachable, length 74
08:42:56.481084 IP user-desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 0.0.0.1.in-addr.arpa. (38)
08:42:58.483803 IP user-desktop.local.mdns > 224.0.0.251.mdns: 0 PTR (QM)? 0.0.0.1.in-addr.arpa. (38)
08:43:08.852514 IP user-desktop.local.40285 > mygateway1.ar7.domain: 50650+ AAAA? sb-ssl.google.com. (35)
08:43:08.892283 IP mygateway1.ar7.domain > user-desktop.local.40285: 50650 1/1/0 CNAME[|domain]
08:43:08.894804 IP user-desktop.local.45995 > mygateway1.ar7.domain: 52507+ A? sb-ssl.google.com. (35)
08:43:08.896424 IP mygateway1.ar7.domain > user-desktop.local.45995: 52507- 1/0/0 A[|domain]
08:43:08.898654 IP user-desktop.local.40404 > 1.0.0.0.https: Flags [S], seq 462489953, win 5840, options [mss 1460,sackOK,TS val 1703380 ecr 0,nop,wscale 4], length 0
08:43:11.898454 IP user-desktop.local.40404 > 1.0.0.0.https: Flags [S], seq 462489953, win 5840, options [mss 1460,sackOK,TS val 1704130 ecr 0,nop,wscale 4], length 0

```

---

### Post by nfnm on 2010-01-18
Alex,

finally i've found that if i change my namserver in /etc/resolv.conf from 192.168.1.1 (my router) to my isp dns server then the mozilla and all other applications begans to work.

i think this problem should be related to ubuntu 9.10, cause i have no this problem with other OS's.

Thanks.

---

