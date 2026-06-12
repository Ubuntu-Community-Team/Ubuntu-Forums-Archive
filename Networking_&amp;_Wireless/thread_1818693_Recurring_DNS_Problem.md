---
title: "Recurring DNS Problem"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by linuxyogi on 2011-08-05
Hi,

I have configured opendns on my adsl router. So 192.168.1.1 was the first nameserver in Network Manager

but I often faced name resolution issues, so I configured 4.2.2.1 as the first 

nameserver, 4.2.2.2 as the second & 192.168.1.1 as the third.

Problem is with the above configuration everything works well for a few days then again name 

resolution stalls. And again I change the sequence of the nameservers or insert a new one & 

again it works for a few days. 

I am tired of doing that again & again.

Please someone explain, what is going wrong & suggest a permanent fix.

---

### Post by dineshs on 2011-08-05
If you are using network manager to configure devices (and not /etc/network/interfaces) try to give DNS entries via network manager 
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)

---

### Post by linuxyogi on 2011-08-05
> **dineshs said:**
> If you are using network manager to configure devices (and not /etc/network/interfaces) try to give DNS entries via network manager 
[http://ubuntuforums.org/showpost.php?p=9467538&postcount=5](http://ubuntuforums.org/showpost.php?p=9467538&postcount=5)

Yes, that's how I have configured the connection. Manually, using Network Manager.

---

### Post by linuxyogi on 2011-08-08
Bump :confused:

---

### Post by cbruce8 on 2011-08-08
When it is failing, what does nslookup tell you?

-c

---

### Post by linuxyogi on 2011-08-08
> **cbruce8 said:**
> When it is failing, what does nslookup tell you?

-c

nslookup takes a long time to complete. 

I will paste the result of nslookup here the next time this issue occurs.

---

### Post by linuxyogi on 2011-08-09
@cbruce8

It just happened again. nslookup prints ....

```
$ nslookup ubuntu.com
;; connection timed out; no servers could be reached

```But there is still connectivity .......

```

$ ping 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.
64 bytes from 4.2.2.1: icmp_seq=1 ttl=56 time=244 ms
64 bytes from 4.2.2.1: icmp_seq=2 ttl=56 time=243 ms
64 bytes from 4.2.2.1: icmp_seq=3 ttl=56 time=242 ms
64 bytes from 4.2.2.1: icmp_seq=4 ttl=56 time=243 ms
64 bytes from 4.2.2.1: icmp_seq=5 ttl=56 time=242 ms

```

---

### Post by dineshs on 2011-08-09
Did you try the following?
Run```
gksudo nautilus /etc/NetworkManager/system-connections
```Ensure that the file corresponding to the device you are using(say eth0) has the correct DNS entry.
Have you tried other DNSs such as 8.8.8.8 and 8.8.4.4 ?

---

### Post by linuxyogi on 2011-08-09
> **dineshs said:**
> Did you try the following?
Run```
gksudo nautilus /etc/NetworkManager/system-connections
```Ensure that the file corresponding to the device you are using(say eth0) has the correct DNS entry.
Have you tried other DNSs such as 8.8.8.8 and 8.8.4.4 ?



```
[connection]
id=Auto eth0
uuid=385ffa59-dfea-449d-8046-3e422095e095
type=802-3-ethernet
autoconnect=true
timestamp=0

[ipv4]
method=auto
dns=8.8.8.8;8.8.4.4;192.168.1.1;
ignore-auto-routes=false
ignore-auto-dns=true
dhcp-send-hostname=false
never-default=false

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=40:61:86:bd:3c:a2
mtu=0

[ipv6]
method=ignore
ignore-auto-routes=false
ignore-auto-dns=false
never-default=false
```

I am using Google DNS atm. But the problem is all works well with a particular DNS configuration for a few days & then name resolution fails.

---

