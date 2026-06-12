---
title: "Share internet from wireless to wired"
date: 2011-02-26
forum: Networking &amp; Wireless
---

### Post by agkbill on 2011-02-26
Hi,

I have a small Aaeon-6850 with Ubutnu 11.04.

It have three network interfaces, 

- Wireless that is connected to my router and out to internet.
- eth0
- eth1

Wireless is working great.

I would like to connect another computer to eth0 and get it in contact with my router and get connected with automatic DHCP.


How I tried to do.

- open and edited eth0:
  - enable connect automatically
  - under IPv4 Settings I selected "Share to outher computers"

If I understod right the would share my connection to eth0 and start a DHCP server there.

But what happen when I connect eth0 to my switch is that in never get a connection. It alter between connected and disconnected all the time,

Any idea what I made wrong?

Thank you for a great forum!

Best regards,

/Christer

---

### Post by agkbill on 2011-02-26
Output from "ifconfig"


eth0      Link encap:Ethernet  HWaddr 00:07:32:06:b6:87  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::207:32ff:fe06:b687/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:383 errors:0 dropped:0 overruns:0 frame:0
          TX packets:761 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:28352 (28.3 KB)  TX bytes:82344 (82.3 KB)

eth1      Link encap:Ethernet  HWaddr 00:07:32:06:66:7a  
          inet6 addr: fe80::207:32ff:fe06:667a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4719 (4.7 KB)  TX bytes:3917 (3.9 KB)
          Interrupt:16 Base address:0xd100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74595 (74.5 KB)  TX bytes:74595 (74.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:6b:c0:ff:5a  
          inet addr:192.168.1.144  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:6bff:fec0:ff5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20184 errors:0 dropped:2639 overruns:0 frame:0
          TX packets:17395 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19712141 (19.7 MB)  TX bytes:3229228301 (3.2 GB)

---

### Post by inobe on 2011-02-26
i have this setup and it's working flawlessly.

though i am using kubuntu and knetwork manager is much different.

what kind of router do you have, also is eth0 plugged into port 1 on that router, and has everything been restarted including the router?

---

### Post by agkbill on 2011-02-26
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.42.43.0      0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

---

### Post by agkbill on 2011-02-26
I tried it on a laptop I have with UBUNTU 10.10 and it work OK there.

So maybe it have to do with UBUNTU 11.04?

I installed because my wireless REALTEK RTL8188SU did not work under 10.10 but without problem 11.04.

/Christer

---

### Post by agkbill on 2011-02-26
I do not have a router like that.

The computer Aaeon-6850 I use have two nic eth0, eth1 and wireless.

/Christer

---

### Post by inobe on 2011-02-26
> **agkbill said:**
> I do not have a router like that.

The computer Aaeon-6850 I use have two nic eth0, eth1 and wireless.

/Christer

please put as much information in one post, this will avoid any confusion.

give me the model of your router, or switch.

also 11.04 will not be stable and i suggest filing a bug report.

---

### Post by agkbill on 2011-02-26
Dear inobe,

Thank you for reply.

My router is a "Netgear WNR3500L Open Source Router", using "Tomato Firmware v1.28.9050 MIPSR2-beta20 K26 USB Ext".

My connection is:

Netgear WNR3500L --> wireless to wlan0

I then whant to use "Share to outher computers" --> eth0 --> wire --> next computer.


/Christer

---

### Post by inobe on 2011-02-26
> **agkbill said:**
> Dear inobe,

Thank you for reply.

My router is a "Netgear WNR3500L Open Source Router", using "Tomato Firmware v1.28.9050 MIPSR2-beta20 K26 USB Ext".

My connection is:

Netgear WNR3500L --> wireless to wlan0

I then whant to use "Share to outher computers" --> eth0 --> wire --> next computer.


/Christer


thanks for working with me on this and giving me your router information, that said the solution is simple.

you need an additional switch.

edit: --> eth0 --> wire --> switch/ router --> next computer.

---

### Post by agkbill on 2011-02-26
Dear inobe,

Sorry, my mistake, the setup I have is:

eth0 --> wire --> switch/ router --> next computer. 


If I want to go eth0 --> wire --> next computer. I need another type of wire.

Sorry for my mistake in explaining my setup.

What make me think it is a 11.04 thing is that as soon as I connect
eth0 --> switch I get the connected/disconnected every second behavior at once.
That is not the case on my laptop with ubuntu 10.10 there it works fine.

/Christer

---

### Post by inobe on 2011-02-26
> **agkbill said:**
> Dear inobe,

What make me think it is a 11.04 thing is that as soon as I connect
eth0 --> switch I get the connected/disconnected every second behavior at once.
That is not the case on my laptop with ubuntu 10.10 there it works fine.

/Christer

lets try to rule out 11.04 being the problem, tell me about the switch, the make and model.

---

### Post by agkbill on 2011-03-04
Dear inobe,


Thank you for your effort to help with the network problems.

I decided to go back to 10.10 because I had a working setup there when I got the wireless up and running.

Possible that the problem is not at all 11.04 but I fell that it is not worth the effort to pinpoint the problem when I got a working solution.


The switch I use is a NETGEAR ProSafe GS105E.


Thank you,


Best regards,
/Christer

---

