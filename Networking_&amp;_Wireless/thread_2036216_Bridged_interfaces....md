---
title: "Bridged interfaces..."
date: 2012-08-01
forum: Networking &amp; Wireless
---

### Post by eliotn on 2012-08-01
Hi all,

I have the following issue:
Server123 with 3x NICs:
eth0 - mgmt
eth1 - Router
eth2 - Wireless AP
br666 - Bridge eth1 eth2

I'm trying to bridge eth1 with eth2 with no IPs...The intention is to break the link between Router <---> Wireless AP, so Router is plugged in to eth1 and Wireless AP to eth2.

Purpose - real-time in-line IDS monitoring installed on the Server123

Ouput of ifconfig:

br666     Link encap:Ethernet  HWaddr xx
          inet6 addr: fe80::250:56ff:feb1:651/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:230 (230.0 B)  TX bytes:9704 (9.7 KB)

eth0      Link encap:Ethernet  HWaddr xx
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:feb1:4d3c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1099 errors:0 dropped:81 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:103833 (103.8 KB)  TX bytes:41881 (41.8 KB)
          Interrupt:18 Base address:0x2024

eth1      Link encap:Ethernet  HWaddr xx
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1481 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:198217 (198.2 KB)  TX bytes:27190 (27.1 KB)

eth2      Link encap:Ethernet  HWaddr xx
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1465 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4500 (4.5 KB)  TX bytes:178405 (178.4 KB)


Output of /etc/network/interfaces

auto lo eth0 eth1 eth2 br666
iface lo inet loopback

allow-hotplug eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.254
dns-nameservers 192.168.1.254 192.168.1.250

iface eth1 inet manual
iface eth2 inet manual

iface br666 inet manual
bridge_ports eth1 eth2
bridge_maxwait 0


Guess what? It doesnt work. There is no connectivity between the Router and Wireless AP. What am I doing wrong?

---

### Post by eliotn on 2012-08-01
Possibly I got it horrible wrong.

All I want to do is to pass traffic from eth1 ---> eth2 without IP addresses...

Is bridging what I should be using?

---

### Post by bakegoodz on 2012-08-02
Show me output of:
```
sudo brctl show
```

---

### Post by eliotn on 2012-08-02
```
bridge name     bridge id               STP enabled     interfaces
br666           8000.005056b10651       yes             eth1
                                                        eth2

```

---

### Post by bakegoodz on 2012-08-02
Interesting setup. I've always assigned IP to bridges. So your IDS software sniffs Ethernet frames? This is what I would do: I would monitor the traffic going across with the Ethernet analyser Wireshark, you would see if there is ethernet traffic and if there is a problem with the AP and router config you may be able to see that too.

```
sudo apt-get install tshark
sudo tshark -i br666
```

---

