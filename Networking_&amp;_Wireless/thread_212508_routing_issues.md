---
title: "routing issues"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by capnquackenbush on 2006-07-10
first off, let it be known that i am a linux neophyte. please excuse my ignorance. i have plans to setup ipv6, but seeing as how i'm having troubles setting up ipv4 routing i may not follow through with that. i've been useing two different guides on how to set up ipv4 routing on a linux box. in spite of this, i can't seem to figure out what i'm supposed to put in my routing table. here is what i have in it so far. ```
obiwan@ipv6-router:~$ ip route show
192.168.1.0/24 dev eth2  proto kernel  scope link  src 192.168.1.1
70.178.79.0/24 dev eth0  proto kernel  scope link  src 70.178.79.12
default via 70.178.79.1 dev eth0

```
and ```
obiwan@ipv6-router:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:BD:1D:91:B6
          inet addr:70.178.79.12  Bcast:70.178.79.255  Mask:255.255.255.0
          inet6 addr: fe80::230:bdff:fe1d:91b6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11997 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:124 txqueuelen:1000
          RX bytes:1803118 (1.7 MiB)  TX bytes:297523 (290.5 KiB)
          Interrupt:9 Base address:0x2000

eth2      Link encap:Ethernet  HWaddr 00:E0:18:60:8F:1D
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe60:8f1d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:462 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:40291 (39.3 KiB)  TX bytes:6271 (6.1 KiB)
          Interrupt:9 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:872 (872.0 b)  TX bytes:872 (872.0 b)

```

any help would be greatly appreciated. lemme know if you need more info from me. i must slumber now.

---

### Post by mips on 2006-07-10
Not sure what you are trying to achieve, elaborate a bit.

Is IP forwarding enabled ? Looked at something like firestarter ?

---

### Post by capnquackenbush on 2006-07-11
so i had this bright idea. since windows vista has ipv6 enabled by default, i got the idea of taking an old computer and running linux on it to be a router. i got through about half of the ipv6 setup when it dawned on me that i hadn't done a thing about routing ipv4. so i switch gears towards getting that set up. the guides i was using to set up ipv4 routing left me confused about what to put into my routing table. i've two NICs, one receives an ip via dhcp from my cable modem. the other NIC has a static ip of 192.168.1.1
at that time, ip_forwarding was enabled. i installed firestarter, and it promptly hosed my network. i was pinging local ips and getting like 50% packet loss. so i just reinstalled ubuntu. maybe with a clean slate i can get this set up properly. lemme know what info you need from me. thanks

---

