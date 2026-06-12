---
title: "DNS kinda working (9.04)"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by mudcow007 on 2009-12-02
hello all just installed 9.04 configured static IP 
setup our internal DNS servers in the resolv.conf

i can ping [www.google.com](www.google.com) 

but if i try to ping one of our servers it cant find it, although it can ping an ip address on the network.

also the server is using Tomcat to publish internal sites i cant reach the sites by using the servers name, but if i use the servers IP the site is reachable.

what have i missed?

thanks

**edit** 

results from ```
dmesg | grep eth0
```

```
[    3.137340] 0000:06:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1c:c0:2e:e5:0f
[    3.137343] 0000:06:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.137413] 0000:06:00.0: eth0: MAC: 2, PHY: 2, PBA No: ffffff-0ff
[   11.195347] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.900941] 0000:06:00.0: eth0: Link is Up 1000 Mbps Full Duplex, Flow Control: None
[   13.901568] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   24.480006] eth0: no IPv6 routers present
[83493.822067] ADDRCONF(NETDEV_UP): eth0: link is not ready
[83496.480953] 0000:06:00.0: eth0: Link is Up 1000 Mbps Full Duplex, Flow Control: None
[83496.481825] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[83507.400005] eth0: no IPv6 routers present
```

---

### Post by snkiz on 2009-12-02
Here this got me up and running with a caching dns server that does local name resolution. hope it helps. :) 
[http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html]("http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html")

---

### Post by mudcow007 on 2009-12-04
thanks for the reply

Do i really need to install Bind if i already have a dns server on the my network?

i would of thought setting the dns server infomation in the ubuntu box should enable local dns resolution to work correctly?

i maybe wrong though (i normally am ;))

---

### Post by snkiz on 2009-12-04
Sorry I misunderstood you, I thought you were trying to setup a dns server. Well if you have access to your dns servers you can troubleshoot them with that. So What you are saying is you have a connection to the internet and you can ping ip's but not not hostnames on your local network? Are you using the network manager on the desktop? check to make sure the dns servers are listed there. um you also could add the the machines you want to /etc/hosts. I've never done that so I'm no sure how you would write the file, but it would work.

More info: you can also set your static ip dns and gateway from /etc/network/interfaces anyway you chose to go resolv.conf and interfaces should  have matching ip's for dns.

---

### Post by mudcow007 on 2009-12-09
hi sorry i aint replied first chance to get to work on the ubuntu box for a week!!

ok im looking at system > preferences > network connections

all of the connections are empty (wired, wireless, VPN and DSL)

where are dns servers set??

---

### Post by mudcow007 on 2009-12-10
hello all

right really racking my brains trying to get our Ubuntu 9.04 server to use our networks dns (our domain is server 2000 with XP hosts)

we have a feisty fawn server which is able to use dns fine.

my resolv.conf contains

```
domain HFT
      search HFT
nameserver 192.168.1.193
nameserver 192.168.1.25
```

HFT is our domain name.

192.168.1.193 is our DNS server
192.168.1.25 is a gateway

does anything look amiss there??

if i run ```
nslookup
```

i receive the following error

```
root@pbx-2:~# nslookup
> server1
;; Got recursion not available from 192.168.1.193, trying next server
;; Got SERVFAIL reply from 192.168.1.193, trying next server
Server:		192.168.1.25
Address:	192.168.1.25#53

** server can't find server1: NXDOMAIN 
```

ok **quick update** i have reinstalled 9.04 to make sure it wasnt anything i had done to mess up DNS. i can ping google.com successfully.

is it because i have our gateway as a dns server in resolv.conf?

---

### Post by mudcow007 on 2009-12-14
im officially stupid...thats ok i can say it ;)

i hadnt set the fully qualified domain name in the resolv.conf grrr!!

i had missed off the .ds

---

