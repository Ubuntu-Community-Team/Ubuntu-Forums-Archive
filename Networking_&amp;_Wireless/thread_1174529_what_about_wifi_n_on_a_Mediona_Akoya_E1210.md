---
title: "what about wifi n on a Mediona Akoya E1210"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by dbourrion on 2009-05-31
Hi.
I'm using an medion akoya E1210 under Ubuntu 9.04 and it works perfectly except wifi n : I have a dlink - dir 635 wifi routeur which gives me 802.11n (and my macbook and my imac, connected too on my network, are working in 802.11n)

But the medion akoya under Linux goes only on 802.11g, which I can't understand because the wifi card in the Medion is an Ralink RT2860 which is an 802.11n one.

Should somebody give me some help ?
Thanks a lot

Best regards (and sorry for my bad english - I'm french)

---

### Post by superprash2003 on 2009-05-31
go to your terminal and type **lshw -C network** and post output here..

---

### Post by dbourrion on 2009-05-31
Here it is if it could help (ps : I've try to install the Native Ralink driver but I can't manage to make it work)

> root@daniel-laptop:~# lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:21:85:47:cd:67
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:15:af:ee:4a:d2
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2860 driverversion=1.53+Ralink Technology, Corp.,11 ip=192.168.0.197 latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g


---

### Post by superprash2003 on 2009-06-01
well your wifi card seems to be recognized and you seem to be getting an ip 192.168.0.197.. which is good..post output of the following
1)iwconfig
2)ifconfig

---

### Post by dbourrion on 2009-06-01
Well :

> root@daniel-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:85:47:cd:67  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:ee:4a:d2  
          inet addr:192.168.0.197  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:feee:4ad2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3804 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4556827 (4.5 MB)  TX bytes:697439 (697.4 KB)
          Interrupt:17 Memory:dfc00000-dfc10000 


> root@daniel-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"DetG"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:F0:B8:EF:D5   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:E411-16A0-7740-51B0-DAF9-06A8-0A6C-A6A3   Security mode:restricted
          Power Management:off
          Link Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@daniel-laptop:~# 


---

### Post by superprash2003 on 2009-06-01
well , all of this looks good..now post output of
1)ping 208.67.222.222
2)ping google.com

---

### Post by dbourrion on 2009-06-01
Everything looks normal :

> root@daniel-laptop:~# ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
64 bytes from 208.67.222.222: icmp_seq=1 ttl=51 time=116 ms
64 bytes from 208.67.222.222: icmp_seq=2 ttl=51 time=226 ms
64 bytes from 208.67.222.222: icmp_seq=3 ttl=51 time=45.3 ms
64 bytes from 208.67.222.222: icmp_seq=4 ttl=51 time=41.6 ms
64 bytes from 208.67.222.222: icmp_seq=5 ttl=51 time=165 ms
64 bytes from 208.67.222.222: icmp_seq=6 ttl=51 time=146 ms
64 bytes from 208.67.222.222: icmp_seq=7 ttl=51 time=201 ms
^C
--- 208.67.222.222 ping statistics ---
8 packets transmitted, 7 received, 12% packet loss, time 7004ms
rtt min/avg/max/mdev = 41.646/134.607/226.313/66.381 ms
root@daniel-laptop:~# ping google.com    
PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=54 time=368 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=8 ttl=54 time=682 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=13 ttl=54 time=330 ms
^C
--- google.com ping statistics ---
14 packets transmitted, 3 received, 78% packet loss, time 13164ms
rtt min/avg/max/mdev = 330.991/460.784/682.786/157.727 ms
root@daniel-laptop:~# 


---

