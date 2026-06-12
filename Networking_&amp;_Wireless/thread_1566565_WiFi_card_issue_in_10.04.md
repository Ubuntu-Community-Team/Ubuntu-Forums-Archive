---
title: "WiFi card issue in 10.04"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by shalako on 2010-09-02
I have a common problem that is near resolution and I need a push to the finish line.

Installed 10.04 on Compaq Presario 2700 with Netgear WN511B wireless adapter.
I cannot get the system to recognize this card. I can however establish a wired connection and have activated the Broadcom B43 wireless driver suggested (fwcutter tool).

Here is some info:

chipset- BCM43XG
PCI-ID - 14e4:4329

```
justin@justin-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:a5:6c:98:a5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

justin@justin-laptop:~$ 

```

---

### Post by Jammerton on 2010-09-02
what is the readout from "lspci"? does the system recognize it at all?  did you check proprietary drivers? furthermore are you certain the wireless card is functional?

---

