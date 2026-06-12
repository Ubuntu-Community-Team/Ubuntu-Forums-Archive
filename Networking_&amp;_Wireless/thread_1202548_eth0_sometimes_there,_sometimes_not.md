---
title: "eth0 sometimes there, sometimes not"
date: 2009-07-02
forum: Networking &amp; Wireless
---

### Post by claus on 2009-07-02
Hi,

since I upgraded from **Intrepid** to **Jaunty**, I'm experiencing some weird problem with my **eth0 connection**. After boot-up, *sometimes* it's there, sometimes not. In the latter case, I need to reboot at least once (sometimes even more often) to get the connection working (left-clicking on the icon and selecting **'Wired Network > eth0'** doesn't fix it). This is a complete mystery to me. Does anybody have a clue what could be the matter here and how I can fix this?

TIA,

Claus

---

### Post by Idefix82 on 2009-07-02
Can you open the terminal (Applications->Accessories->Terminal) and type in
```
lshw -C network
```
then paste the output here? This will tell us what ethernet card you have and what driver is handling it.

Are you dual booting with Windows?

---

### Post by claus on 2009-07-02
> **Idefix82 said:**
> Can you open the terminal (Applications->Accessories->Terminal) and type in
```
lshw -C network
```
then paste the output here? This will tell us what ethernet card you have and what driver is handling it.

claus@ubuntu:~$ sudo lshw -C network
[sudo] password for claus: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 10
       serial: 00:08:54:09:50:05
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.220.100 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: fa:66:9f:6f:4f:07
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

> **Idefix82 said:**
> Are you dual booting with Windows?

No, just Intrepid on a i386 machine. The eth0 connection goes to a **Samsung 3010 phone SL** router (VoIP/DSL).

Thanks for your response,

Claus

---

### Post by Idefix82 on 2009-07-02
What is the output from
```
ifconfig
```

It would be helpful if you could also post the output from the same commands when eth0 doesn't come up. Have you got a different computer from which you could then access the internet? Otherwise you can save the output and post it here once the internet comes up again.

---

### Post by superprash2003 on 2009-07-02
also post output of** sudo /etc/init.d/networking restart**

---

### Post by RyuKokoro on 2009-07-02
I'm having a similar problem. I'm dual-booting Ubuntu 9.04 and Windows XP Pro SP2. When I boot into Ubuntu, I cannot get it to connect to my wireless router (Belkin Wireless G.) To get it to work, I have to restart, boot WinXP, allow it to connect then reboot into Ubuntu. I have a New Link PCI wi-fi Card but that's obviously not where the problem lies as it works flawlessly in WinXP.

I don't know if it's relevant but my gf's Mac and my PS3 all connect fine. I used ndiswrapper to install the drivers from a CD that came with the PCI wi-fi card and lspci shows it in the list.

---

### Post by claus on 2009-07-02
**ifconfig:**

eth0      Link encap:Ethernet  HWaddr 00:08:54:09:50:05  
          inet addr:192.168.220.100  Bcast:192.168.220.255  Mask:255.255.255.0
          inet6 addr: fe80::208:54ff:fe09:5005/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:450 errors:1 dropped:0 overruns:0 frame:0
          TX packets:381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:538954 (538.9 KB)  TX bytes:45770 (45.7 KB)
          Interrupt:9 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:440 (440.0 B)  TX bytes:440 (440.0 B)

Claus

---

### Post by claus on 2009-07-02
> **superprash2003 said:**
> also post output of** sudo /etc/init.d/networking restart**

claus@ubuntu:~$ sudo /etc/init.d/networking restart
[sudo] password for claus: 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.

This came while eth0 was (luckily) up. Strange ...

Claus

---

### Post by superprash2003 on 2009-07-03
post output of /etc/network/interfaces file .. also post output of** lshw -C network** when you cannot find eth0

---

### Post by claus on 2009-07-04
> **superprash2003 said:**
> post output of /etc/network/interfaces file

auto lo
iface lo inet loopback

> **superprash2003 said:**
>  .. also post output of** lshw -C network** when you cannot find eth0

claus@ubuntu:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 10
       serial: 00:08:54:09:50:05
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 6a:4d:a4:ee:bb:73
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

TIA,

Claus

---

