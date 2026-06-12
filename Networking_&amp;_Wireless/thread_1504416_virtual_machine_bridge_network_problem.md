---
title: "virtual machine bridge network problem"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by hroitblat on 2010-06-08
I am using Ubuntu 10.04, 64-bit.  I am trying to set up a virtual  machine on it using vmbuilder.
As I understand, I need to set up bridging.  If I set up br0, then I  cannot get out of the machine.  Even a ping to 192.168.1.1 (my gateway)  comes back as network unreachable.  If I comment out #auto br0, then I  can get out (on eth0), but i get an error from libvirt. 

Any suggestions?


My /etc/network/interfaces file (eth0 networking works, but libvirt does  not):

#auto eth0
#iface eth0 inet dhcp

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.154
netmask 255.255.255.0
gateway 192.168.1.1
nameserver 192.168.1.1
network 192.168.1.0

#auto wlan0
iface wlan0 inet static
address 192.168.1.153
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.0

#auto br0
iface br0 inet static
address 192.168.1.160
netmask 255.255.255.0
gateway 192.168.1.1
network 192.168.1.0
bridge_ports eth0
bridge_stp off
bridge_fd 0
bridge_maxwait 0

In contrast, when I enable auto br0, ifconfig shows:

br0       Link encap:Ethernet  HWaddr a4:ba:db:f8:5f:db  
          inet addr:192.168.1.160  Bcast:192.168.1.255   Mask:255.255.255.0
          inet6 addr: fe80::a6ba:dbff:fef8:5fdb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:477806 (477.8 KB)  TX bytes:4422 (4.4 KB)

eth0      Link encap:Ethernet  HWaddr a4:ba:db:f8:5f:db  
          inet addr:192.168.1.154  Bcast:192.168.1.255   Mask:255.255.255.0
          inet6 addr: fe80::a6ba:dbff:fef8:5fdb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1884 errors:0 dropped:0 overruns:0 frame:0
          TX packets:183 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:511446 (511.4 KB)  TX bytes:24390 (24.3 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4462 (4.4 KB)  TX bytes:4462 (4.4 KB)

virbr0    Link encap:Ethernet  HWaddr 5e:df:8d:27:91:ab  
          inet addr:192.168.122.1  Bcast:192.168.122.255   Mask:255.255.255.0
          inet6 addr: fe80::5cdf:8dff:fe27:91ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:13546 (13.5 KB)

---

### Post by hroitblat on 2010-06-10
I got it to work by commenting out auto eth0 and uncommenting br0.
Thanks,
Herb

---

