---
title: "no route to host"
date: 2010-08-07
forum: Networking &amp; Wireless
---

### Post by carpman on 2010-08-07
Hello, ok trying to ssh working, have installed the ssh server, have disable ufw (temp) have added ALL: ALL to hosts.allow have added my ssh keys to .ssh/authorized_keys but still not joy connecting?

error is 

```
ssh user@192.168.1.38
ssh: connect to host 192.168.1.38 port 22: No route to host

```

ping also fails but traceroute works

```
ping -c3 192.168.1.38                                                                                                                                                           
PING 192.168.1.38 (192.168.1.38) 56(84) bytes of data.                                                                                                                                        
From 192.168.1.5 icmp_seq=1 Destination Host Unreachable                                                                                                                                      
From 192.168.1.5 icmp_seq=2 Destination Host Unreachable                                                                                                                                      
From 192.168.1.5 icmp_seq=3 Destination Host Unreachable                                                                                                                                      
                                                                                                                                                                                              
--- 192.168.1.38 ping statistics ---                                                                                                                                                          
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms                                                                                                                   
, pipe 3                                                                                                                                                                                      
hamlet .ssh # traceroute 192.168.1.38
traceroute to 192.168.1.38 (192.168.1.38), 30 hops max, 60 byte packets
 1  hamlet.home.co.uk (192.168.1.5)  3000.693 ms !H  3000.691 ms !H  3000.688 ms !H

```

I can access 192.168.1.5 (gentoo box) from 192.168.1.38 (ubuntu) but does not work the other way around?

Am at a loss as to what could be preventing access?

any ideas?

cheers

---

### Post by pat_bateman on 2010-08-10
Hi,

You have a routing problem.
Could you please paste the output of the following commands that you will run on the ubuntu and gentoo boxes?
```
ifconfig -a
```
```
netstat -nr
```

-Pat

---

### Post by ashishrevar on 2011-03-27
Hello there, I am using --addressing private in my instances,

I ran the following command...
ssh -i ~/.euca/mykey.priv ubuntu@172.19.1.2

So it says,
ssh: connect to host 172.19.1.2 port 22: No route to host

If I try to ping my instances,
ping 172.19.1.2

icmp_seq=1 Destination host unreachable
what is the problem?

---

