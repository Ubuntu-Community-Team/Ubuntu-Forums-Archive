---
title: "unable to access internet from network computer"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by Despot Despondency on 2009-12-22
Hi,

I've just installed ubuntu 9.10 on my computer at university (which is on the network in my department) but I'm unable to access to internet.

I've obtained the following information

```

ping -c 5 www.google.com
ping: unknown host www.google.com

``` 

```

ping -c 5 66.249.80.104
PING 66.249.80.104 (66.249.80.104) 56(84) bytes of data.

--- 66.249.80.104 ping statistics ---
5 packets transmitted, 0 recieved, 100% packet loss, time 4032ms

```

My /etc/resolv.conf is blank. Any ideas what I should do? TAI

---

### Post by Despot Despondency on 2009-12-22
I've solved it. I needed to put the appropriate lines in the /etc/resolv.conf file.

---

