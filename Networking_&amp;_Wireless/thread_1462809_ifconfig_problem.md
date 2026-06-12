---
title: "ifconfig problem"
date: 2010-04-26
forum: Networking &amp; Wireless
---

### Post by mosquetero on 2010-04-26
Hi

I just want to change my ethernet address to 10.0.0.1. I type:

```
sudo ifconfig eth0 add 10.0.0.1 netmask 255.255.255.0
```

but I get:

SIOCSIFNETMASK: Cannot assign requested address

Then, if I type ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:15:c5:57:53:56  
          inet6 addr: fe80::215:c5ff:fe57:5356/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:723 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:143736 (143.7 KB)  TX bytes:3325 (3.3 KB)
          Interrupt:18 

eth0:0    Link encap:Ethernet  HWaddr 00:15:c5:57:53:56  
          inet addr:10.0.0.1  Bcast:0.0.0.0  Mask:0.0.0.0
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          Interrupt:18 
```

:( Anyone knows what it is happening?

Thanks

---

### Post by mosquetero on 2010-04-26
Found it!

The right command is ```
ifconfig eth0 10.0.0.1 netmask 255.255.255.0
```

without the "add".

---

### Post by 98cwitr on 2010-04-26
or just use network manager? :?

---

### Post by SlugSlug on 2010-04-26
or edit 
/etc/network/interfaces

---

### Post by Iowan on 2010-04-26
> **mosquetero said:**
> Found it!

[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")? :)

---

