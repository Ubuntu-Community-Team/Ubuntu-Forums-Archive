---
title: "eth0 network disables wlan0 on laptop"
date: 2011-11-13
forum: Networking &amp; Wireless
---

### Post by fordcz on 2011-11-13
Hello, here's my **situation**:

In my home network I have two computers - desktop pc and laptop (both OS Ubuntu 10.04 LTS). The desktop pc has a wireless network adapter and is connected to my router (gateway to internet) via wlan0 interface. Obviously, the laptop is also connected to the router via wlan0 interface. That (in a certain matter) makes the two computer equal, right? Both computers can reach the internet. This is, when the /etc/network/interfaces file only contains loopback interface.

Here's the **deal**:

For a school project, I want to create a network between the two computers. Since I want to preserve the wlan0 interface (~ internet connection) for both computers, I decided to connect the computers by a cable.

Here's **what I did**:

1) I've connected the laptop with the desktop via patch cable.
2) I've appended eth0 interface setting to the desktop's /etc/network/interfaces file so now it looks like:
```
auto lo
iface lo inet loopback
# eth0
auto eth0
iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
```3) I've appended eth0 interface setting to the laptop's /etc/network/interfaces file so now it looks like:
```
auto lo
iface lo inet loopback
# eth0
auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
```4) I've rebooted both computers

Here's the **problem**:

On the desktop pc side, it seems to work. I can ping to the laptop (192.168.0.2). Internet connection (wlan0) is unaffected.

On the laptop side, I can ping to the desktop (192.168.0.1), however internet connection (~ wlan0) is somehow ... lost. The network indicator from the top-right panel completely disappeared. Here's the output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:1f:16:b1:f8:d6  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:16ff:feb1:f8d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93 errors:0 dropped:0 overruns:0 frame:0
          TX packets:118 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:13531 (13.5 KB)  TX bytes:16146 (16.1 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:fb:64:44:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Since the setting for each computer is basically the same, I would rather expect both machines working or both machines not-working, instead of one working while the other one not-working...
[B]
Questions[/B] are:

Is there anything generally wrong I am doing?
Why doesn't my configuration work? (the state "work" means that both wlan0 and eth0 are working correctly)

---

