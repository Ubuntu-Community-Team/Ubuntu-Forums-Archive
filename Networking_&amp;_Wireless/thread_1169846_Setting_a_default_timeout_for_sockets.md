---
title: "Setting a default timeout for sockets"
date: 2009-05-25
forum: Networking &amp; Wireless
---

### Post by BruceBerry on 2009-05-25
Hi,

I have a problem with firefox: some sites don't respond and it takes more than 3 minutes for firefox to give up with a network error.
I wrote a thread in the mozilla forums but i didn't get any helpful hints.
I'm thinking it's a socket problem because i visit the same site with a python script using the socket library and using socket.settimeout actually sets the timeout for the connection.

The point is, if i cannot solve the problem in firefox, maybe there is a way to solve it upstream? What if there is a default timeout value for sockets which firefox would inherit?
Ideas?

thanks

---

### Post by puppywhacker on 2009-05-25
I bet these is a sysctl setting for the tcp timeout setting. I never used it, and posting it on a forum isn't a good idea, there will always be somebody who will copy-paste it.

---

### Post by BruceBerry on 2009-05-25
i tried to google for "linux sysctl tcp timeout" but i didn't came up with anything.

what's the problem with posting it here (if there is such setting, of course)?

---

### Post by superprash2003 on 2009-05-26
post output of ifconfig from the terminal

---

### Post by BruceBerry on 2009-05-26
```
eth3      Link encap:Ethernet  HWaddr 00:0c:29:6e:fa:3b  
          inet addr:172.16.20.129  Bcast:172.16.20.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe6e:fa3b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17602517 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17236584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4188555934 (4.1 GB)  TX bytes:594478915 (594.4 MB)
          Interrupt:18 Base address:0x2000 
```

---

### Post by superprash2003 on 2009-05-26
try these
1)disable ipv6
2)change MTU value
3)use opendns servers..

---

### Post by puppywhacker on 2009-05-27
If you really think it's a socket timeout problem make a network trace with tcpdump in a terminal or wireshark in a nice GUI.

If it really is a connection problem you can set the TCP time-outs with sysctl, google for "ipsysctl tutorial" to show how

What superprash is suggesting that your problem is most likely something completely different. He is talking about DNS not resolving some sites, and that may be a caused by firefox trying IPv6 first, although you don't have an global ipv6 address.

about:config
network.dns.disableIPv6 = true

---

