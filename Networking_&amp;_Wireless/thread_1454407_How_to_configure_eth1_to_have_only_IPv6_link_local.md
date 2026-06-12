---
title: "How to configure eth1 to have only IPv6 link local?"
date: 2010-04-14
forum: Networking &amp; Wireless
---

### Post by Skaperen on 2010-04-14
This is with the server edition of Ubuntu 9.10.  I want to bring up eth1 with ONLY the link-local IPv6 address, and nothing more than that.  I tried this:```
fermat/root/x0 /root 10# cat /etc/network/interfaces
# fermat:/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 172.30.16.5
        netmask 255.255.0.0
        network 172.30.0.0
        broadcast 172.30.255.255
        metric 1

auto eth1
iface eth1 inet6 static

fermat/root/x0 /root 11# ifup eth1
Don't seem to be have all the variables for eth1/inet6.
Failed to bring up eth1.
fermat/root/x0 /root 12# 
```What else is needed?  I also tried it with "static" omitted and got this error:```
/etc/network/interfaces:15: too few parameters for iface line
ifup: couldn't read interfaces file "/etc/network/interfaces"
```The "manual" option just didn't bring the interface up at all (I didn't really expect it to, but tried, anyway, because I've run across many things that don't do what is obvious).

The end result I want is for the interface to be UP and having a link-local address like this:```
eth1      Link encap:Ethernet  HWaddr 00:15:17:da:e0:29  
          inet6 addr: fe80::215:17ff:feda:e029/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10192 (10.1 KB)  TX bytes:726 (726.0 B)
          Memory:ba800000-ba820000 
```

---

### Post by roemer2201 on 2012-02-24
```
auto eth1
iface eth1 inet manual
 up /sbin/ifconfig eth1 0.0.0.0
```

---

### Post by lemming465 on 2012-02-25
Perhaps tell eth1 not to accept ICMPv6 router advertisements?
```
sudo sysctl -w net.ipv6.conf.eth1.accept_ra=0
```

---

