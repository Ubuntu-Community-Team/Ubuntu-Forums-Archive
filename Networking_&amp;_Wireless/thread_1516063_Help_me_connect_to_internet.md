---
title: "Help me connect to internet"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by trikedX on 2010-06-23
I was able to connect normally with winXP then installed ubuntu and now am unable to connect.
I have a TW-EA510 ADSL modem router connected to ubuntu computer. How do i make it work :confused:

---

### Post by trikedX on 2010-06-23
B U M P
atleast post a link to this thread on #ubuntu channel someone must have like a step by step guide for a 5 year old or anything. this shouldn't be too difficult i am using version 10.04

---

### Post by dineshs on 2010-06-23
Is it connected via USB or ethernet?

---

### Post by Praveen30 on 2010-06-23
> **trikedX said:**
> I was able to connect normally with winXP then installed ubuntu and now am unable to connect.
I have a TW-EA510 ADSL modem router connected to ubuntu computer. How do i make it work :confused:

first of all make clear the medium via which you want to connect to internet?

---

### Post by trikedX on 2010-06-23
it is ethernet

---

### Post by dineshs on 2010-06-23
what is the output of
```
ifconfig -a
```

---

### Post by trikedX on 2010-06-23
Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:196 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:196 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:14448 (14.4 KB)  TX bytes:14448 (14.4 KB)

---

### Post by dineshs on 2010-06-23
Pl post the result of
```
sudo lshw -C network
```and let us wait for experts .I think your ethernet card is not detected

---

### Post by trikedX on 2010-06-23
it blinks "pci (sysfs)" or something like that and then clears the line

---

### Post by ghamilton on 2010-06-23
I think **dineshs** has it right.

Typical output for the *lshw -C network* command is something like this:
>   *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth2
       version: 02
       serial: 00:1c:c4:2d:4e:c5
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.3-0 ip=10.10.40.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:93200000-9321ffff memory:93224000-93224fff ioport:40e0(size=32)

So, if you're not seeing something along those lines, either you don't have a NIC, or your OS doesn't know about it.

****

---

### Post by trikedX on 2010-06-27
so... you people are saying that i might as well go ahead and  download a "patched" windows since no one can make this lousy OS work?

---

### Post by dineshs on 2010-06-28
I would try another ethernet card
Do you have a seperate ethernet card or the one integrated in your motherboard?

---

### Post by trikedX on 2010-06-28
yeah its the hardwares fault not the OS

though this works well in windows so you might as well mark this thread as solved
if anyone else asks just tell them to install windows or if possible any macOS that'll fix everything

---

### Post by BenjaminChile on 2010-06-28
Are you connecting from a laptop model???? or from a desktop model ?????   Let's see this firstly, so we can check your model specifications and Ethernet card. By the way did you try ubuntu 10.04 with the option Live Cd first before you installed it. If so, did your ethernet RJ-45 connection work out fine or did you just install it and so far you cannot connect to your ADSL provider?

Send some specific info please

---

