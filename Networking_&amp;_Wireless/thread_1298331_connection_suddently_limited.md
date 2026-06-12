---
title: "connection suddently limited"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by sparkied on 2009-10-22
Hi peeps!

for two days I've been scanning the Internet for a plausible cause or one solution to a network problem I'm having. Yet I got sqwat... when I mean sqwat I mean deadly sqwat.

So here it is, hoping you can help me:

My wireless device use to work fine until two days ago when suddenly I had limited possibilities. Now I can access all assets of my subnet network either be it a computer, a router (which isn't my gateway) or an xbox but I can't access my primary router (gateway) and the Internet. The assets of my subnet can have access to my computer as I my share is available to other computers.

I'm the only one on the network to have the problem and ubuntu karmic koala 9.10. The problem is also present when I use a live ubuntu 8.10 intrepid version. Everyone else uses winXP. I don't think it's a hardware problem as I still have connectivity but who knows. One anomaly but not a biggy is that my wireless device is identified as eth1. My wired device is still eth0.

so here is my system's outputs:

```

user@computer:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:8a:b8:fd  
          inet6 addr: fe80::2c0:9fff:fe8a:b8fd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:8131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6143 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4241599 (4.2 MB)  TX bytes:1328683 (1.3 MB)
          Interrupt:6 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:c4:ba:24  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fec4:ba24/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3777 errors:11 dropped:11 overruns:0 frame:0
          TX packets:5850 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:949855 (949.8 KB)  TX bytes:364207 (364.2 KB)
          Interrupt:10 Base address:0x4000 Memory:e0202000-e0202fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2015 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:84852 (84.8 KB)  TX bytes:84852 (84.8 KB)

```

```

user@computer:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth1

```

```

user@computer:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"OTI"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:41:7D:69   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=88/100  Signal level=-41 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:11  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:27

```

```

user@computer:~$ dmesg | grep 02:04
[    0.373951] pci 0000:02:04.0: reg 10 32bit mmio: [0xe0202000-0xe0202fff]
[    0.373992] pci 0000:02:04.0: PME# supported from D0 D3hot D3cold
[    0.373997] pci 0000:02:04.0: PME# disabled
[   33.067237] ipw2200 0000:02:04.0: PCI INT A -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   33.067372] ipw2200 0000:02:04.0: firmware: requesting ipw2200-bss.fw

```

```

user@computer:~$ dmesg | grep eth1
[   43.812230] eth1: no IPv6 routers present

```

```

user@computer:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    computer
# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

if anyone need anything else to help me out let me know. Help is really appreciated.

---

