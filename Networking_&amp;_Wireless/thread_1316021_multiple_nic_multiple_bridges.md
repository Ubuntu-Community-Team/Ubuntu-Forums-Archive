---
title: "multiple nic multiple bridges"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2009-11-05
I have 2 nic and want to setup bridges on them both
my network interfaces file is this. I know the last defined is the default
this current file does not seem to be working regarding eth3 and br1. I have 2 nic, primary is eth2 and secondary is eth3

I dont know if it is working. I have a media player dsm 320 attached to eth3 directly and had it working when the file had it defined with eth3 last.
and i am using ushare as the media server

> #originally just these next 2 lines were in here
#auto lo
#iface lo inet loopback


#ubuntu lets the last defined network be the default
#extra card bridge
auto eth3
iface eth3 inet manual

auto br1
iface br1 inet static
        address 192.168.2.100
        network 192.168.2.0
        netmask 255.255.255.0
        broadcast 192.168.2.255
        gateway 192.168.2.100
        bridge_ports eth3
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

#internet gateway router cox
auto eth2
iface eth2 inet manual

auto br0
iface br0 inet static
        address 192.168.1.100
        network 192.168.1.0
        netmask 255.255.255.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        bridge_ports eth2
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

ifconfig -a
> scott@scott-desktop:~$ ifconfig -a
br0       Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe54:faa6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3742 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3981531 (3.9 MB)  TX bytes:441129 (441.1 KB)

br1       Link encap:Ethernet  HWaddr ea:46:b8:e6:fe:d1  
          inet addr:192.168.2.100  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::e846:b8ff:fee6:fed1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:17112 (17.1 KB)

eth2      Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet6 addr: fe80::222:15ff:fe54:faa6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3747 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2883 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:4034323 (4.0 MB)  TX bytes:441565 (441.5 KB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11747 (11.7 KB)  TX bytes:11747 (11.7 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.43.1  Bcast:172.16.43.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.201.1  Bcast:192.168.201.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



---

### Post by sdowney717 on 2009-11-05
i can ping both adresses
the problem is the media player dsm 320 is not seeing the ushare server
on the second nic eth3

> scott@scott-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.787 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.744 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.742 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.734 ms
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=0.735 ms
^C
--- 192.168.1.1 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4002ms
rtt min/avg/max/mdev = 0.734/0.748/0.787/0.031 ms
scott@scott-desktop:~$ ping 192.168.2.100
PING 192.168.2.100 (192.168.2.100) 56(84) bytes of data.
64 bytes from 192.168.2.100: icmp_seq=1 ttl=64 time=0.017 ms
64 bytes from 192.168.2.100: icmp_seq=2 ttl=64 time=0.013 ms
64 bytes from 192.168.2.100: icmp_seq=3 ttl=64 time=0.016 ms
64 bytes from 192.168.2.100: icmp_seq=4 ttl=64 time=0.015 ms
^C
--- 192.168.2.100 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.013/0.015/0.017/0.003 ms
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2009-11-05
restarting network and it tells me eth3 does not exist?
so what is the other network card named?
the ping on 192.168.2.110 is the dsm 320 assignment

> scott@scott-desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for scott: 
 * Reconfiguring network interfaces...                                          eth3: ERROR while getting interface flags: No such device
RTNETLINK answers: No such process
interface eth3 does not exist!

Waiting for br1 to get ready (MAXWAIT is 20 seconds).

Waiting for br0 to get ready (MAXWAIT is 20 seconds).
                                                                         [ OK ]
scott@scott-desktop:~$ ping 192.168.2.110
PING 192.168.2.110 (192.168.2.110) 56(84) bytes of data.
From 192.168.2.100 icmp_seq=2 Destination Host Unreachable
From 192.168.2.100 icmp_seq=3 Destination Host Unreachable
From 192.168.2.100 icmp_seq=4 Destination Host Unreachable
^C
--- 192.168.2.110 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5009ms
, pipe 3
scott@scott-desktop:~$ 


---

### Post by sdowney717 on 2009-11-05
well i found out the nic card was having a resource problem
partly by running  nictools-pci
and by booting vista, the card could not function with the other ethernet card.

so i replaced with a 3com and that one works and it is eth4
still dont know how to set it up yet.

> scott@scott-desktop:~$ sudo vortex-diag 
[sudo] password for scott: 
vortex-diag.c:v2.16 1/12/2004 Donald Becker (becker@scyld.com)
 [http://www.scyld.com/diag/index.html](http://www.scyld.com/diag/index.html)
Index #1: Found a 3c905B Cyclone 100baseTx adapter at 0xec00.
 Station address 00:10:5a:73:c4:83.
  Receive mode is 0x07: Normal unicast and all multicast.
 Use '-a' or '-aa' to show device registers,
     '-e' to show EEPROM contents, -ee for parsed contents,
  or '-m' or '-mm' to show MII management registers.
scott@scott-desktop:~$ 



---

### Post by sdowney717 on 2009-11-05
I got it working with ushare
I had to temporarily use network manager to setup the cards.
The second card is working configured manually. By the way, network manager when you configure manual, you have to go to the ipv6 tab and say ignore. then after you input all your settings, the apply button is active

what i really want to do is setup bridge networking for the virtual machine.

---

