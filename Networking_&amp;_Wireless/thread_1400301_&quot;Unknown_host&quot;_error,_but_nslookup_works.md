---
title: "&quot;Unknown host&quot; error, but nslookup works"
date: 2010-02-06
forum: Networking &amp; Wireless
---

### Post by geirgp on 2010-02-06
I have connected to our corporate network (OpenVPN) using the Networkmanager. I am able to connect to the internal servers by specifying IP addresses, but not by using host names. This works all good when connecting from a Windows client, so I did some investigation:

The corporate nameserver has been added to the top of the list in /etc/resolv.conf. Issuing commands like "nslookup server1.company.local" works well and returns the expected 10.0... address. However, when I try connecting to any of the servers using the hostname, I get "uknown host" errors. It makes no difference if I try running a simple "ping", or browsing the internal web servers. None of my applications are able to resolve the internal hostnames specified in the dns server.

I tried removing my LAN nameserver leaving only the corporate (from VPN) in /etc/resolv.conf, but that didn't help. It is able to resolve any public hostname though.

Example:

```
geir@ubuntu:~$ nslookup intra.company.local
Server:		10.0.80.1
Address:	10.0.80.1#53

Name:	intra.company.local
Address: 10.0.80.24

geir@ubuntu:~$ ping intra.company.local
ping: unknown host intra.company.local

geir@ubuntu:~$ ping 10.0.80.24
PING 10.0.80.24 (10.0.80.24) 56(84) bytes of data.
64 bytes from 10.0.80.24: icmp_seq=1 ttl=63 time=28.9 ms
64 bytes from 10.0.80.24: icmp_seq=2 ttl=63 time=31.6 ms


```

Any thoughts? I have a fresh Ubuntu installation, no dns cache installed or any other fancy modifications.

Thanks,

Geir

---

### Post by Basotang on 2010-02-25
Have you tried the solution here:

[https://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/140663](https://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/140663)

I have the exact same problem than you, and the above did not work for me, but it is still worth trying.

Seb.

---

