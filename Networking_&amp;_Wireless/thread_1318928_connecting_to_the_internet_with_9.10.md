---
title: "connecting to the internet with 9.10"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by vendetta314 on 2009-11-08
i installed the driver for my netqork adapter and connected to my router but i  cant access the web. i open system moniter and i send 11.5 bytes pkts and recieve nothing. please help. ubuntu 9.10

---

### Post by Crafty Kisses on 2009-11-08
We need some more information, copy and paste these commands into the terminal **(Applications -> Accessories -> Terminal)**:
```
lspci
lsusb
lshw -C network
```
Make sure you put the /code brackets around the results so it's easier for others and I to see the results.

---

### Post by Cybie257 on 2009-11-08
Are you connecting via Wire, or Wireless? 

If it's wireless, you might have to setup your router with a wired connection first. 

-Cybie

---

### Post by vendetta314 on 2009-11-08
i did the codes and it detected my netgear wg311v2 with ndiswrapper driver installed. and even my linksys usb adapter that didnt need me to install a driver. and yes i did install the router.

---

### Post by vendetta314 on 2009-11-08
i can connect to someone elses network and it works but its unsecured and it goes away after like 5 minutes. it just has problems with mine. should i just put the disc that came with the router in?

---

### Post by vendetta314 on 2009-11-08
i ran...
    netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
10.42.43.0      *               255.255.255.0   U         0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 wlan0
darrell@darrell-desktop:~$ ping 10.42.43.1
PING 10.42.43.1 (10.42.43.1) 56(84) bytes of data.
64 bytes from 10.42.43.1: icmp_seq=1 ttl=64 time=0.087 ms
64 bytes from 10.42.43.1: icmp_seq=2 ttl=64 time=0.059 ms
64 bytes from 10.42.43.1: icmp_seq=3 ttl=64 time=0.065 ms
64 bytes from 10.42.43.1: icmp_seq=4 ttl=64 time=0.060 ms
64 bytes from 10.42.43.1: icmp_seq=5 ttl=64 time=0.068 ms
64 bytes from 10.42.43.1: icmp_seq=6 ttl=64 time=0.062 ms
64 bytes from 10.42.43.1: icmp_seq=7 ttl=64 time=0.059 ms
64 bytes from 10.42.43.1: icmp_seq=8 ttl=64 time=0.066 ms
64 bytes from 10.42.43.1: icmp_seq=9 ttl=64 time=0.066 ms
64 bytes from 10.42.43.1: icmp_seq=10 ttl=64 time=0.064 ms
64 bytes from 10.42.43.1: icmp_seq=11 ttl=64 time=0.065 ms
64 bytes from 10.42.43.1: icmp_seq=12 ttl=64 time=0.064 ms
64 bytes from 10.42.43.1: icmp_seq=13 ttl=64 time=0.065 ms
64 bytes from 10.42.43.1: icmp_seq=14 ttl=64 time=0.062 ms
64 bytes from 10.42.43.1: icmp_seq=15 ttl=64 time=0.065 ms

---

