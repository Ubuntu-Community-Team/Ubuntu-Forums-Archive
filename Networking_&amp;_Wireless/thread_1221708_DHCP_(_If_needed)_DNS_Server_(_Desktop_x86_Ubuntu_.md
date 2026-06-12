---
title: "DHCP ( If needed) DNS Server ( Desktop x86 Ubuntu )"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by Cpuboye11 on 2009-07-24
Hey guys.. I just recently lost my good old netgear router... Sad thing to.. It lasted for such a long time and then BOOM. It died.. Sad sad sad day...

Any ways.. Instead of me going out and buying new router or anything.. I was hoping you guys could help me with something. I have a 60% windows network going on.. ( parents... can't teach them anything )rest is ubuntu. I have a file server sitting here and I would like to turn that in to the server. Its running updated files of 9.04 or w/e... And I was wanting to know is there a way to turn this Desktop box in to a DHCP and issue IPs and share the internet? I know there is a DHCP server called something odd.. But i had no luck with it... I just couldn't figure it out. 

Could any one lead me in the right direction? Maybe throw out some hints, lol?

Thanks,
Kyle

---

### Post by jamest09 on 2009-07-24
```
apt-get install dhcp3-server
```

[http://www.lmgtfy.com/?q=dhcpd+howto](http://www.lmgtfy.com/?q=dhcpd+howto)

---

### Post by Iowan on 2009-07-24
You could also check **dnsmasq**.
[Here]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for internet sharing.

---

### Post by Cpuboye11 on 2009-07-24
Hey thanks for all the advice and stuff. Really- I got the server to allow statics and stuff but a little problem with DHCP.

Using the guide that Iowan submitted  [This!]("https://help.ubuntu.com/community/Internet/ConnectionSharing"). 

I get this after trying to start the DHCP DNS server: 

```
*Starting DNS forwarder and DHCP server dnsmasq
dnsmasq:failed to create listening socket: Address already in use

```


I'm not sure why or what to do at this point.

Kyle

---

### Post by Cpuboye11 on 2009-07-24
Update: Even trying it on a second ubuntu box that was a clean install- I got the same problem...

---

### Post by paulisdead on 2009-07-24
is dhcp3-server running already when you try to run dnsmasq?  If you're going with dnsmasq, get rid of dhcp3-server, since it can do dhcp.

I prefer bind/dhcp3 myself.  I ran into some issues with dnsmasq awhile ago, that weren't there with bind, but I can't recall what they were.  Bind's a bit more complicated, but I've found it to be more reliable, and robust if you later need it to support different views or something else.

---

### Post by Cpuboye11 on 2009-07-24
> **paulisdead said:**
> is dhcp3-server running already when you try to run dnsmasq?  If you're going with dnsmasq, get rid of dhcp3-server, since it can do dhcp.

I prefer bind/dhcp3 myself.  I ran into some issues with dnsmasq awhile ago, that weren't there with bind, but I can't recall what they were.  Bind's a bit more complicated, but I've found it to be more reliable, and robust if you later need it to support different views or something else.


Hey thanks for the reply. Hmm I'm not 100% sure what dhcp3-server is. I never installed it, unless it comes with ubuntu or this package.

*** Checking***

There was a package called dhcp3-client- i removed that... 

SWEET< THANK YOu!!! It works.. omg, thank you

---

### Post by Cpuboye11 on 2009-07-24
> **jamest09 said:**
> ```
apt-get install dhcp3-server
```

[http://www.lmgtfy.com/?q=dhcpd+howto](http://www.lmgtfy.com/?q=dhcpd+howto)

btw- like your link.

---

