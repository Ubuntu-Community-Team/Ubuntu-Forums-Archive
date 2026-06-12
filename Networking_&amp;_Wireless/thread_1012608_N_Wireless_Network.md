---
title: "N Wireless Network"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by chudder on 2008-12-16
Hi all,

I have a unique problem or at least this is what I think the problem is and I want some verification.  

I have two laptops, one of them runs complete ubuntu (feisty fawn) and has worked great but the computer itself is showing signs of age and so I got a new one.  I moved into a new apartment about the same time and there is an N Wireless router and the old ubuntu laptop recognizes the signal but nothing comes through.  I wonder if it's the N network being too new for the computer because it picks up wireless everywhere else.  My new laptop that has [groan] vista on it picks up the N network fine.  That's why I have been hesitant to install Ibex on the new laptop.  I'm not sure if the internet is a linux problem or a network problem.

Any guidance would be greatly appreciated.  If someone has already made a thread like this then just forward me where I need to go.

Thanx!
:confused:

---

### Post by Peter09 on 2008-12-16
Can you post the output of the terminal command

```
ifconfig
```

---

### Post by chudder on 2008-12-16
> **Peter09 said:**
> Can you post the output of the terminal command

```
ifconfig
```

```

eth1      Link encap:Ethernet  HWaddr 00:13:02:81:07:FF  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:350 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:18 Base address:0x6000 Memory:da000000-da000fff 

eth1:avah Link encap:Ethernet  HWaddr 00:13:02:81:07:FF  
          inet addr:169.254.6.178  Bcast:169.254.255.255  Mask:255.255.0.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Interrupt:18 Base address:0x6000 Memory:da000000-da000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:2196 (2.1 KiB)  TX bytes:2196 (2.1 KiB) 

```

It should be noted that for some reason now, the computer doesn't even connect to the network, if it does, I will post the output.

thanx for the help

---

### Post by Peter09 on 2008-12-16
According to the ifconfig you have an ip address, which I guess is allocated by DHCP.
Can you post the output of

```
route -n
```

---

### Post by rlj1965 on 2008-12-16
> **chudder said:**
> Hi all,

I have a unique problem or at least this is what I think the problem is and I want some verification.  

I have two laptops, one of them runs complete ubuntu (feisty fawn) and has worked great but the computer itself is showing signs of age and so I got a new one.  I moved into a new apartment about the same time and there is an N Wireless router and the old ubuntu laptop recognizes the signal but nothing comes through.  I wonder if it's the N network being too new for the computer because it picks up wireless everywhere else.  My new laptop that has [groan] vista on it picks up the N network fine.  That's why I have been hesitant to install Ibex on the new laptop.  I'm not sure if the internet is a linux problem or a network problem.

Any guidance would be greatly appreciated.  If someone has already made a thread like this then just forward me where I need to go.

Thanx!
:confused:


Just a thought. Have you checked if the router is in stable "N" or Mixed Mode ("B, G, N")? The old laptop probably does not have a "N" capable NIC card, but should be able to use the router if it is in b, g or mixed mode.

---

### Post by chudder on 2008-12-19
Hi, 

sorry I've been away.  I think I figured out the solution, I've been using Feisty until today which was only WEP encryption equipped but now I upgraded and it seems to work.  thank you all for your help and time.

---

