---
title: "Strange behavior when pinging local devices by FQDN"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by dergringo on 2009-05-26
Hi.

I have got 4 clients here in a LAN. They are all in the same network and share the same netmask and they are all connected to the same switch and are served by a DHCP server.
Two of the clients have Jaunty installed. The other two have Debain Lenny on it and they don't have that problem!

Now please have a look at this. Why does the first ping command not work on ubuntu machines?

```
philipp@pc:~$ ping gateway.home.local
ping: unknown host gateway.home.local


philipp@pc:~$ nslookup gateway.home.local
Server:		192.168.23.254
Address:	192.168.23.254#53

Name:	gateway.home.local
Address: 192.168.23.254


philipp@pc:~$ ping 192.168.23.254
PING 192.168.23.254 (192.168.23.254) 56(84) bytes of data.
64 bytes from 192.168.23.254: icmp_seq=1 ttl=64 time=2.63 ms
64 bytes from 192.168.23.254: icmp_seq=2 ttl=64 time=0.524 ms
64 bytes from 192.168.23.254: icmp_seq=3 ttl=64 time=0.538 ms
...
```

EDIT: I was able to get it solved.
In /etc/nsswitch.conf changed the line
hosts:         files mdns4_minimal [NOTFOUND=return] dns mdns4
to
hosts:         files dns

---

