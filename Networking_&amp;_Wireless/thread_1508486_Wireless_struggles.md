---
title: "Wireless struggles"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by crispya on 2010-06-13
Hi

I'm fairly new to Ubuntu and I've been running Ubuntu 9.10 on my desktop and I have Windows Vista on my laptop.

I clicked on the "upgrade to 10.04" option without thinking too much about it and I am now having problems connecting to my router with my laptop. I can get on the internet with my desktop via the wired connection, but there is no wireless. I don't know if this is an Ubuntu problem or if it is the router. I have reinstalled 9.10 via disk but the same problem remains.

I'm getting really confused about what to do and I've followed some instructions on other threads and this is what Terminal is telling me:

:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82547EI Gigabit Ethernet Controller
        vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 00
       serial: 00:11:2f:56:67:74
       width: 32 bits
       clock: 66MHz
        capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A ip=192.168.1.64 latency=0 mingnt=255 multicast=yes
       resources: irq:18 memory:fe9e0000-fe9fffff ioport:cf80(size=32)
 
:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2f:56:67:74  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe56:6774/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4775 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
           RX bytes:5445777 (5.4 MB)  TX bytes:449501 (449.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
 
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

