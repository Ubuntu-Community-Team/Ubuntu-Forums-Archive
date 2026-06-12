---
title: "ubuntu with firestarter on can't access its vmware server's filesharing"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by gisk on 2009-01-09
Hello,

I read through many posts and still can't get this to work.

I have VMWare Server 2 with XP virtual machine installed on my Ubuntu 8.04 via NAT networking provided by VMWare. Now everything works fine with Firestarter disabled.

The moment I enable it, I can't connect from Ubuntu to my XP shares on virtual machine and logs throws these errors:
Jan  9 13:46:48 lab kernel: [ 4892.000067] Unknown OutputIN= OUT=vmnet8 SRC=192.168.218.1 DST=192.168.218.128 LEN=144 TOS=0x00 PREC=0x00 TTL=64 ID=40468 DF PROTO=TCP SPT=44568 DPT=445 WINDOW=65535 RES=0x00 ACK PSH URGP=0 
Jan  9 13:46:49 lab kernel: [ 4892.447681] Unknown OutputIN= OUT=vmnet8 SRC=192.168.218.1 DST=192.168.218.128 LEN=144 TOS=0x00 PREC=0x00 TTL=64 ID=40469 DF PROTO=TCP SPT=44568 DPT=445 WINDOW=65535 RES=0x00 ACK PSH URGP=0 

All filesharing connections from virtual machine to Ubuntu work fine even with Firestarter on, as I opened all the relevant ports.

I have these interfaces on my system:
root@lab:/etc/firestarter# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:c9:05:3d:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:54114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40950014 (39.0 MB)  TX bytes:40950014 (39.0 MB)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.218.1  Bcast:192.168.218.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:54:3a:6f  
          inet addr:192.168.22.102  Bcast:192.168.22.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:fe54:3a6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87440 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104145280 (99.3 MB)  TX bytes:6099920 (5.8 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-3C-54-3A-6F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Could someone please explain to me why does Firestarter block all outgoing traffic vmnet8 even though it is permissive by default?

Many Thanks.

---

