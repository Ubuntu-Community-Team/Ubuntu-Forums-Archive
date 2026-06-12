---
title: "Static ip For eth0 in different family than router ip breaks Internet Browsing"
date: 2012-12-27
forum: Networking &amp; Wireless
---

### Post by raja_s_patil on 2012-12-27
Hello,

I did a clean install of Kubuntu 12.04 on new Dell-15RSE.

First I gave static IP to wired connection as 192.168.1.124 and gateway as 192.168.1.1 and rebooted the system
At this point I am able to connect to internet and browse normally. Similarly ping to [www.google.co.in](www.google.co.in) also works.

Later We decided to use 10.66.1.* for development Lan and 10.66.2.* for office lan. For testcase we used this new Laptop and I tried to give static IP of 10.66.1.124 and gateway as 192.168.1.1 and rebooted the laptop.
At this point the Internet access is not possible and I cant ping to [www.google.co.in](www.google.co.in) but I can ping 192.168.1.1, 8.8.8.8, and another computer in lan with 10.66.1.248.
.

In both cases dns servers were given as 8.8.8.8 and 8.8.4.4 to wired connection in network-manager dialog.


Can somebody help me in this situation ?

the outputs of various commands are given below for reference.

Thanks and warm regards.

Raja Patil


[SIZE="2"][COLOR="RoyalBlue"]Case static ip 192.168.1.124 and gateway 192.168.1.1
[/COLOR][/SIZE]
```

rsp@DELL-15RSE:~$ ifconfig
	eth0      Link encap:Ethernet  HWaddr d4:be:d9:56:44:4e  
		inet addr:192.168.1.124  Bcast:192.168.1.255  Mask:255.255.255.0
		inet6 addr: fe80::d6be:d9ff:fe56:444e/64 Scope:Link
		UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
		RX packets:3205 errors:0 dropped:0 overruns:0 frame:0
		TX packets:2249 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000 
		RX bytes:1882551 (1.8 MB)  TX bytes:308310 (308.3 KB)
		Interrupt:43 

	lo        Link encap:Local Loopback  
		inet addr:127.0.0.1  Mask:255.0.0.0
		inet6 addr: ::1/128 Scope:Host
		UP LOOPBACK RUNNING  MTU:16436  Metric:1
		RX packets:274 errors:0 dropped:0 overruns:0 frame:0
		TX packets:274 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:0 
		RX bytes:23267 (23.2 KB)  TX bytes:23267 (23.2 KB)

	vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
		inet addr:10.1.1.1  Bcast:10.1.1.255  Mask:255.255.255.0
		inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link                                                
		UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                             
		RX packets:0 errors:0 dropped:0 overruns:0 frame:0
		TX packets:117 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000 
		RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

	vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
		inet addr:172.16.165.1  Bcast:172.16.165.255  Mask:255.255.255.0
		inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
		UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
		RX packets:0 errors:0 dropped:0 overruns:0 frame:0
		TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000 
		RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rsp@DELL-15RSE:~$ route

	Kernel IP routing table
	Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
	default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
	10.1.1.0        *               255.255.255.0   U     0      0        0 vmnet1
	link-local      *               255.255.0.0     U     1000   0        0 eth0
	172.16.165.0    *               255.255.255.0   U     0      0        0 vmnet8
	192.168.1.0     *               255.255.255.0   U     1      0        0 eth0

```

[SIZE="2"][COLOR="RoyalBlue"]Case static ip 10.66.1.124 and gateway 192.168.1.1[/COLOR][/SIZE]

```

rsp@DELL-15RSE:~$ ifconfig
	eth0      Link encap:Ethernet  HWaddr d4:be:d9:56:44:4e  
		inet addr:10.66.1.124  Bcast:10.66.1.255  Mask:255.255.255.0
		inet6 addr: fe80::d6be:d9ff:fe56:444e/64 Scope:Link
		UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
		RX packets:40 errors:0 dropped:0 overruns:0 frame:0
		TX packets:132 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000 
		RX bytes:4068 (4.0 KB)  TX bytes:18002 (18.0 KB)
		Interrupt:43 

	lo        Link encap:Local Loopback  
		inet addr:127.0.0.1  Mask:255.0.0.0
		inet6 addr: ::1/128 Scope:Host
		UP LOOPBACK RUNNING  MTU:16436  Metric:1
		RX packets:69 errors:0 dropped:0 overruns:0 frame:0
		TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:0 
		RX bytes:4422 (4.4 KB)  TX bytes:4422 (4.4 KB)

	vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
		inet addr:10.1.1.1  Bcast:10.1.1.255  Mask:255.255.255.0
		inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
		UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
		RX packets:0 errors:0 dropped:0 overruns:0 frame:0
		TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000 
		RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

	vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
		inet addr:172.16.165.1  Bcast:172.16.165.255  Mask:255.255.255.0
		inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link                                                
		UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                             
		RX packets:0 errors:0 dropped:0 overruns:0 frame:0
		TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
		collisions:0 txqueuelen:1000 
		RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rsp@DELL-15RSE:~$ route
	Kernel IP routing table
	Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
	default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
	10.1.1.0        *               255.255.255.0   U     0      0        0 vmnet1
	10.66.1.0       *               255.255.255.0   U     1      0        0 eth0
	link-local      *               255.255.0.0     U     1000   0        0 eth0
	172.16.165.0    *               255.255.255.0   U     0      0        0 vmnet8
	192.168.1.1     *               255.255.255.255 UH    0      0        0 eth0

rsp@DELL-15RSE:~$ ping www.google.co.in
	ping: unknown host www.google.co.in

```

[SIZE="2"][COLOR="RoyalBlue"]output of lspci
[/COLOR][/SIZE]
```

rsp@DELL-15RSE:~$ lspci
	00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
	00:01.0 PCI bridge: Intel Corporation Ivy Bridge PCI Express Root Port (rev 09)
	00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
	00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
	00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
	00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
	00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
	00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
	00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
	00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
	00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
	00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
	00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
	01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 682f
	07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 07)
	08:00.0 Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)

```

---

### Post by chadk5utc on 2012-12-28
you can not ping them because they are on a different network. The only way that you can make them talk is through the use of routers one for each network unless you have a router that is capable of running more than one. Most off the shelf routers Linksys, Netgear etc will only handle one. Correction one internal network and one external network. You can configure a second router for the second network 10.66.1.124 and leave the 192.168.* on the first

---

### Post by lykwydchykyn on 2012-12-28
Unless the world has changed since I took my Network+ exam, your gateway generally has to be on the same subnet as your IP.

---

### Post by raja_s_patil on 2012-12-28
> **lykwydchykyn said:**
> Unless the world has changed since I took my Network+ exam, your gateway generally has to be on the same subnet as your IP.

well I have limited knowledge on networking but would like to read few books on it. If you dont mind can you suggest few basic books for reading, I will be gratefull to you. Normally I work in System Design and Database Applications and do java, flex, delphi coding.

However can you suggest a way out so that we can use 10.66.1.* and 10.66.2.* networks for development and office, still using 192.168.1.1 router ?

with my limited knowledge I feel that we can give alternate address to same etho and configure route on front end machines for both networks. For other machines we can Gateway as Front end Machines which will route traffic to Internet Router in 192* family address.

can you comment on this idea ?

Thanks and warm regards.

Raja Patil

---

### Post by chadk5utc on 2012-12-28
Raja the best thing I can suggest is learning hands on by doing and working through problems as they occur. The other thing I can suggest is to use google a lot. Many of us have been doing this for years and it can take a little time to get a solid understanding of networking both wired, wireless and other types. If you run into a problem the best way to learn is to work through it try google first read all you can find and ask questions.

---

### Post by lykwydchykyn on 2012-12-28
> **raja_s_patil said:**
> well I have limited knowledge on networking but would like to read few books on it. If you dont mind can you suggest few basic books for reading, I will be gratefull to you. Normally I work in System Design and Database Applications and do java, flex, delphi coding.

I'd recommend any text aimed at prepping someone for the Network+ exam (COMPTIA).  It will cover all the basics.
> 
However can you suggest a way out so that we can use 10.66.1.* and 10.66.2.* networks for development and office, still using 192.168.1.1 router ?

Why would you want to do this?  Do you have any other routers, or spare systems you can commit to being routers?
> 

with my limited knowledge I feel that we can give alternate address to same etho and configure route on front end machines for both networks. For other machines we can Gateway as Front end Machines which will route traffic to Internet Router in 192* family address.

can you comment on this idea ?


That might work; I've never tried such an approach, but it works with two interfaces on separate networks, so it may work with one.  Basically, you're turning that machine into a router.

---

### Post by raja_s_patil on 2012-12-28
thanks to all contributed.

I did a quick study of network fundamentals, it seems that it is not technically possible. So we are sticking to good old 192.168.1.* network timebeing and deploy applications.

I am closing this topic but if anybody feels that the above requirement can be satisfied please do post suggestions I will be visiting this thread occasionally.

Thanks once again and warm regards.

Raja Patil

---

