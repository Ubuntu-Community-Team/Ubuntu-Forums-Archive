---
title: "Proxychains dns server problem"
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by anishtain4 on 2012-06-15
I'm trying to use proxychains in order to connect to a http server, my proxychains.conf file is as:
```

strict_chain
proxy_dns
tcp_read_time_out 15000
tcp_connect_time_out 8000
[ProxyList]
https   sg1.1000vpn4.com 433 user pass

```
but when I run on terminal "proxychains firefox", it returns this:
```

|DNS-request| forum.ubuntu.ir 
|DNS-response|: forum.ubuntu.ir is not exist

```
What is wrong with the proxychains I have?

---

### Post by poolet on 2012-06-15
You may change the DNS server in the script at [B] [I]"/usr/lib/proxychains'version etc3'/proxyresolv"

[/I][/B]DNS_SERVER=156.154.70.22 //*example*//

now you need to find out your dns server, also try to replace 
the last line with the following:: 

```
http 31.7.61.107 433 user pass
```**or **
```
http sg1.1000vpn4.com 433 user pass
```

---

### Post by anishtain4 on 2012-06-15
ok, I found my dns server with:
$ cat /etc/resolv.conf
it is 192.168.1.2
and replaced that with 4.2.2.2 in proxyresolve as you said, but now I get another error say:
ERROR: ld.so: object 'libproxychains.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libproxychains.so.3' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libproxychains.so.3' from LD_PRELOAD cannot be preloaded: ignored.
I'm afraid this is a software problem right? like the proxychains is not complete
(I did corrected the https to http)

---

### Post by poolet on 2012-06-16
Ok. Please read the following articles before you be able to continue.
First of all a these are all private networks::      
10.0.0.0/8 (255.0.0.0) - > 10.0.0.0 &#8211; 10.255.255.255
172.16.0.0/12 (255.240.0.0)  - >172.16.0.0 &#8211; 172.31.255.255
192.168.0.0/16 (255.255.0.0)  - >  192.168.0.0 &#8211; 192.168.255.255

so probably  192.168.1.2 is an internal ip address of some of your computers..
(possible default gateway 192.168.1.1) try to reach 192.168.1.1 via browser...

**What's DNS ??**
[http://en.wikipedia.org/wiki/Domain_Name_System](http://en.wikipedia.org/wiki/Domain_Name_System)
**Ip address?? **
[http://en.wikipedia.org/wiki/IP_address](http://en.wikipedia.org/wiki/IP_address)
**Private networks??**
[http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network)

You can contact with your ISP provider for your DNS as from the proxy, email at tech support they may able to give you some kind of tutorial (usually) to fixed your problem...

---

### Post by anishtain4 on 2012-06-17
Well, yes, that is the local address. but tech support won't be of any help because they are opposed to proxychains. I live in Iran and I'm trying to pass the filtering we have

---

### Post by anishtain4 on 2012-06-17
Well, yes, that is the local address. but tech support won't be of any help because they are opposed to proxychains. I live in Iran and I'm trying to pass the filtering we have

---

