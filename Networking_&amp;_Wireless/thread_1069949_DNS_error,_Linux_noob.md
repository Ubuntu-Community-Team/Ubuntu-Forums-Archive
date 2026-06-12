---
title: "DNS error, Linux noob"
date: 2009-02-14
forum: Networking &amp; Wireless
---

### Post by cpufreak2589 on 2009-02-14
I connected to my school's wireless network a while back, named wireless.txstate.edu. I am back at home now on my wireless network, and I am trying to communicate with another box on the same network. I can obviously get online, but I seem to have some intranet networking errors. when I try to ping my second client (mythbox) I get this 
"mobo@entropy:~$ ping mythbox
PING mythbox.wireless.txstate.edu (208.69.36.132) 56(84) bytes of data.
64 bytes from hit-nxdomain.opendns.com (208.69.36.132): icmp_seq=1 ttl=55 time=52.4 ms"
 ....so it looks like my PC (entropy) is tryiing to lookup the hostname mythbox using my router, using opendns, but I see the txstate wireless stuff in there, and I'm unsure why it is even appearing in the first place. I can just ping the IP of mythbox, but I want to use hostnames.

---

### Post by cariboo on 2009-02-14
Just add the ip address of the other computer to your /etc/hosts file eg:

```
192.168.1.200   mythbox
```

change the ip address to match the ip address of mythbox.

Jim

---

### Post by cpufreak2589 on 2009-02-21
> **cariboo907 said:**
> Just add the ip address of the other computer to your /etc/hosts file eg:

```
192.168.1.200   mythbox
```

change the ip address to match the ip address of mythbox.

Jim

Been away, thanks. I'll try that when I get home. Can someone explain to me why my laptop was assigning the mythbox name to the wifi network name? Especially as I wasn't connected to it at the time.

---

