---
title: "not able to connect  internet........."
date: 2009-06-05
forum: Networking &amp; Wireless
---

### Post by ashish_envy on 2009-06-05
hey i m a new user and i was not able to connect internet to my pc.
i hav installed ubuntu 8.04 , 8.10 and now 9.04 version into my pc 
and i was not able to connect to d net and due to which i was not able to download dependencies...........

i have type following commmand into d terminal and d following things happen........

ashish@ashish-desktop:~$ ping 192.168.1.1 

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data. 
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.821 ms 
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.733 ms 
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.722 ms 
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.676 ms 
^C 
--- 192.168.1.1 ping statistics --- 
4 packets transmitted, 4 received, 0% packet loss, time 3000ms 
rtt min/avg/max/mdev = 0.676/0.738/0.821/0.052 ms 






ashish@ashish-desktop:~$ mii-tool 

SIOCGMIIPHY on 'eth0' failed: Operation not permitted 
SIOCGMIIPHY on 'eth1' failed: Operation not permitted 
SIOCGMIIPHY on 'eth2' failed: Operation not permitted 
SIOCGMIIPHY on 'eth3' failed: Operation not permitted 
SIOCGMIIPHY on 'eth4' failed: Operation not permitted 
SIOCGMIIPHY on 'eth5' failed: Operation not permitted 
SIOCGMIIPHY on 'eth6' failed: Operation not permitted 
SIOCGMIIPHY on 'eth7' failed: Operation not permitted 
no MII interfaces found 




ashish@ashish-desktop:~$ ifconfig -a 

eth0      Link encap:Ethernet  HWaddr 00:e0:4d:84:be:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:18 Base address:0x1000 

eth1      Link encap:Ethernet  HWaddr 00:19:d1:13:4c:1f  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0 
          inet6 addr: fe80::219:d1ff:fe13:4c1f/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:39 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:3632 (3.6 KB)  TX bytes:7548 (7.5 KB) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:1072 (1.0 KB)  TX bytes:1072 (1.0 KB) 

pan0      Link encap:Ethernet  HWaddr 16:4d:07:bf:1a:a2  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 




ashish@ashish-desktop:~$ sudo lshw -c network 
[sudo] password for ashish: 

  *-network:0             
       description: Ethernet interface 
       product: RTL-8139/8139C/8139C+ 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 2 
       bus info: pci@0000:05:02.0 
       logical name: eth0 
       version: 10 
       serial: 00:e0:4d:84:be:e8 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s 
  *-network:1 
       description: Ethernet interface 
       product: 82801G (ICH7 Family) LAN Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:05:08.0 
       logical name: eth1 
       version: 01 
       serial: 00:19:d1:13:4c:1f 
       size: 100MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=32 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 16:4d:07:bf:1a:a2 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 


pls help me in this regard.......
pls help me 
pls help me
pls help me.......

---

### Post by 3rdalbum on 2009-06-05
It looks like you can ping your router okay.

What happens if you try to ping [www.google.com?](www.google.com?)

If that succeeds, then I'm out of ideas. You should be able to use Firefox to access the internet.

If it fails, try pinging 66.249.89.147 (which is an IP address that belongs to Google). If that fails, then the data is exiting your router and probably not reaching your ISP, or not getting past your ISP.

If it succeeds, then it looks like you need to specify a DNS server to Ubuntu. A DNS server will convert the names (like Google.com) into the numerical addresses you need.

Go to the network manager on your top panel. Right-click it and go to Edit Connections...  Click on your connection and click Edit. Go to the IPv4 Settings tab and change the method to Automatic (DHCP) Addresses Only. In the DNS field, type:

```
208.67.222.222, 208.67.220.220
```

That is the set of addresses for OpenDNS, a free DNS service.

You may need to turn networking off and back on again, or reboot.

Let us know how you go.

---

### Post by ashish_envy on 2009-06-05
hey thaks allot 
thanks you very much ***_"3rdalbum"_***

when i type ping 66.249.89.147
its pinging

now i do what u tell 
bt i don't knw why its happen ,
when i install ubuntu it must be by default ........
bt in d end its work thank u 
very much .........

now would you pls tell me 
where all the list of repostries saved in ubuntu 
like all the updates got install in var / cache .... apt folder 
so is dere is any folder where all the repostries list got saved .

---

