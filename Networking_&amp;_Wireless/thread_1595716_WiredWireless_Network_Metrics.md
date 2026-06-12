---
title: "Wired/Wireless Network Metrics"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by JR7 on 2010-10-13
Hi,

I'm tearing my hair out trying to set up networking on my PC running Ubuntu 10.04. I am connecting to the net via a wireless router, but I'm having problems setting up a connection to a NAS drive via ethernet. The settings are as follows:

wlan0
IP: 192.168.1.100
Gateway: 192.168.1.1

eth0
IP: 192.168.0.1
Gateway: 192.168.0.2

NAS
IP: 192.168.0.2
Gateway: 192.168.0.1

The PC connects fine to the NAS, but this cuts the wireless network off from accessing the internet. I have done some reading and found out this was to do with the metrics; eth0 should be higher than wlan0 so the PC accesses the internet via the wireless card. I have tried to alter the metric (to no avail) using the following methods:

1. sudo ifconfig eth0 metric 30

I received the message:
SIOCSIFMETRIC: Operation not supported

2. sudo ifmetric eth0 30

Command seemed to run okay, but when I checked using ifconfig, the metric for eth0 was still set to 1.

3. Editing the /etc/network/interfaces

I added the following lines:

iface eth0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.2
metric 30

Restarted my PC and the eth0 did not show in ifconfig, so I typed ifconfig eth0 up, but didn't get any of these settings loaded. Instead I received the following (on entering ifconfig eth0):

```

eth0    Link encap:Ethernet  HWaddr 00:12:3f:70:21:58  
          inet6 addr: fe80::212:3fff:fe70:2158/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:936 (936.0 B)

```Any ideas?

Many thanks.

---

### Post by JR7 on 2010-10-13
I've sorted it. Seems all I needed to do was add:

auto eth0

to the /etc/network/interface file

---

