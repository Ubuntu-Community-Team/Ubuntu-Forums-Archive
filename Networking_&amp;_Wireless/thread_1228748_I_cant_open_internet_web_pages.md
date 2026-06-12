---
title: "I cant open internet web pages"
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by tirengarfio on 2009-08-01
Hi,

im connected to internet through a wireless router. 

When i type "ping 192.168.0.1" my computer reaches the router correctly, but i cant open internet web pages.

I have other computers connected to the same and with them i can browse internet correctly.

This is the error message:

```
Address Not Found

IceCat can't find the server at www.uah.es.

The browser could not find the host server for the provided address.

    * Did you make a mistake when typing the domain? (e.g. "ww.mozilla.org" instead of "www.mozilla.org")
    * Are you certain this domain address exists?  Its registration may have expired.
    * Are you unable to browse other sites?  Check your network connection and DNS server settings.
    * Is your computer or network protected by a firewall or proxy?  Incorrect settings can interfere with Web browsing.



```


This are the ping results:

```
$ ping 212.128.64.12
PING 212.128.64.12 (212.128.64.12) 56(84) bytes of data.
From 193.145.14.29 icmp_seq=2 Packet filtered
From 193.145.14.29 icmp_seq=4 Packet filtered
From 193.145.14.29 icmp_seq=6 Packet filtered
From 193.145.14.29 icmp_seq=8 Packet filtered
From 193.145.14.29 icmp_seq=9 Packet filtered

--- 212.128.64.12 ping statistics ---
9 packets transmitted, 0 received, +5 errors, 100% packet loss, time 7999ms

$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=1.62 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=0.723 ms
64 bytes from 192.168.0.1: icmp_seq=3 ttl=64 time=0.777 ms

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.723/1.041/1.624/0.413 ms
```


Any idea?

---

### Post by Brandon Williams on 2009-08-02
It looks like name resolution is failing. What is the content of your /etc/resolv.conf file? And how does it compare to resolv.conf on the machine that's working?

---

