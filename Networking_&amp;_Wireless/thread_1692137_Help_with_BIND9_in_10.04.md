---
title: "Help with BIND9 in 10.04"
date: 2011-02-21
forum: Networking &amp; Wireless
---

### Post by killbuddy on 2011-02-21
A couple of nights ago I got DNS working on Ubuntu 10.04 with the help of youtube videos made by cgermany77.  I don't know linux very well but want to learn.  I want this for my internal network.  I am currently using this to forward DNS queries to the internet if the IP does not exist on my network.  I have DNS working to where I can resolve IP's when using hostnames, but cannot resolve hostnames to IP's.

Here is my reverse lookup file contents:

rev.0.0.10.in-addr.arpa

```
$TTL
@ IN SOA dns01.hoins.local. admin.hoins.local. (
2007031001;
28800;
3600;
604800;
38400
);

                   IN        NS        dns01.hoins.local.
30                 IN        PTR       dns01.hoins.local.
9                  IN        PTR       PC1.hoins.local.
8                  IN        PTR       PC2.hoins.local.
20                 IN        PTR       PC3.hoins.local.
```


and my forward lookup file:

hoins.local.db

```
$TTL 3D
@ IN SOA dns01.hoins.local. admin.hoins.local. (
2007031001;
28800;
3600;
604800;
38400
);

hoins.local.     IN    NS      dns01.hoins.local.
dns01            IN    A       10.0.0.30
PC1              IN    A       10.0.0.9
PC2              IN    A       10.0.0.8
PC3              IN    A       10.0.0.20
```

What I get when I run nslookup

```

root@dns01:/etc/bind/zones$ nslookup 10.0.0.8
Server:         10.0.0.30
Address:        10.0.0.30#53

** server can't find 8.0.0.10.in-addr.arpa: SERVFAIL

```


Any help would be appreciated.

Thanks for the help in advance.

---

