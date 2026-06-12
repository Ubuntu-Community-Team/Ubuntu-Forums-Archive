---
title: "Network eth0 doesn't receive IP from DHCP"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by rawandnet on 2009-03-27
Hi all,

to start Network service and getting IP address from DHCP, I do the following;

service network start
ifconfig eth0 up
dhclient


the interface comes up, but i don't get an ip address from DHCP server until I select the Network interface through GUI. Am i missing any commands:

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:30:F1:05:AC:E4  

          inet6 addr: fe80::230:f1ff:fe05:ace4/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:3578 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1707 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:1550411 (1.4 MiB)  TX bytes:374861 (366.0 KiB)

          Interrupt:19 Base address:0x4000

---

### Post by coutts99 on 2009-03-27
Whats the output of sudo dhclient eth0?

---

### Post by rawandnet on 2009-03-27
doesn't show any output?

---

### Post by coutts99 on 2009-03-30
None at all?

You are typing 'sudo dhclient eth0' in a console?

---

### Post by rawandnet on 2009-04-06
> **coutts99 said:**
> None at all?

You are typing 'sudo dhclient eth0' in a console?


thanks for your Help.

---

### Post by coutts99 on 2009-04-06
> **rawandnet said:**
> thanks for your Help.

Did you get it working?

---

