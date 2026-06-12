---
title: "Wired connection not working"
date: 2013-04-11
forum: Networking &amp; Wireless
---

### Post by pianist16 on 2013-04-11
Hello, I'm new here (and also to linux) and I think I have exactly the same problem
I have dual boot with Windows 8 alongside with Xubuntu (tried running ubuntu on live cd, same problem)
My ethernet connection works perfectly on Windows 8, but when I boot Xubuntu it simply can't recognize the wired connection.

The weirdest thing is that I had Ubuntu working normally before (alongisde with Windows), then, I formatted it and re-installed it in the same way it was before. Now only my Windows can recognize the wired connection.

Any ideas?

---

### Post by Iowan on 2013-04-11
[http://ubuntuforums.org/showthread.php?t=2134321]("http://ubuntuforums.org/showthread.php?t=2134321")
I moved your post to it's own thread so you can get personalized attention. You didn't mention if you had wireless or if it was working.

> **papibe said:**
> Hi perro68.

Could you post the results of these commands while trying to connect using your wired connection?
```
sudo lshw -C network

lspci -nnk | grep -iA3 eth

ifconfig

route -n

nslookup ubuntu.com

dig ubuntuforums.org
```
Regards.

---

### Post by pianist16 on 2013-04-11
Hi Iowan and thanks for your attention!
Nop, unfortunately I don't have a wireless card on my desktop: would be much easier to post the results.

Here it is:

sudo lshw -C network:
 
>   *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f4:6d:04:77:0e:9f
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168e-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:fbfff000-fbffffff memory:fbff8000-fbffbfff
 
 
lspci -nnk | grep -iA3 eth:
 
> 02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
            Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
            Kernel driver in use: r8169
            Kernel modules: r8169

ifconfig:
 
> eth0      Link encap:Ethernet  HWaddr f4:6d:04:77:0e:9f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)


route -n
 
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
 
 
nslookup ubuntu.com:
 
> connection timed out; no servers could be reached
 
 
 
dig ubuntuforums.org:
 
> ; <<>> DiG 9.8.1-P1 <<>> ubuntuforums.org
;; global options: +cmd
;; connection timed out; no servers could be reached
 

---

### Post by Iowan on 2013-04-11
I'm hoping one of the hardware gurus happens by... > duplex=half 
link=no
speed=10Mbit/s
These don't look promising, and > driver=r8169 looks like one that pops up frequently.

---

### Post by pianist16 on 2013-04-11
Well, I'll wait then.

---

### Post by pianist16 on 2013-04-15
Okay, now that's quite weird. Yesterday I turn it on and worked perfectly the entire day. Today I'm trying turning it on again and the network once again shows no sign of life.
I don't have any clue of what can this be, but I'm pretty sure it's not a hardware problem (at least not an irreversible one).

---

### Post by Iowan on 2013-04-15
I doubt the driver is changing, but...
If it happens to work again, grab the above information (again) - just to see if something did, if fact, change.

---

### Post by permittivity22 on 2013-04-16
can you by chance set the IP?
I think Iowan has the right idea though... driver issue.

But, eth0 is actually showing up.  

Can you do ifconfig eth0 192.168.1.3 and then ifconfig and see if the IP takes?

---

### Post by pianist16 on 2013-04-27
Ok, sorry for taking a bit long.
Right now, I'm connected to it and it's working perfectly, but if I shutdown it and turn on again, the problem returns.

[COLOR=#000000]sudo lshw -C network:
[/COLOR]
> *-network                      description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 06
       serial: f4:6d:04:77:0e:9f
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.3 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:e800(size=256) memory:fbfff000-fbffffff memory:fbff8000-fbffbfff




[COLOR=#000000]lspci -nnk | grep -iA3 eth:

> [/COLOR]02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)	Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
	Kernel driver in use: r8169
	Kernel modules: r8169


[COLOR=#000000]

[/COLOR][COLOR=#000000]ifconfig:

> [/COLOR]eth0      Link encap:Ethernet  HWaddr f4:6d:04:77:0e:9f            inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fe77:e9f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15240 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13634 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13313513 (13.3 MB)  TX bytes:1957180 (1.9 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1058 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1058 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98861 (98.8 KB)  TX bytes:98861 (98.8 KB)


[COLOR=#000000]

[/COLOR][COLOR=#000000]route -n:[/COLOR][COLOR=#000000]

> [/COLOR]Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


[COLOR=#000000]

[/COLOR][COLOR=#000000]nslookup ubuntu.com:
[/COLOR][COLOR=#000000]
> [/COLOR]Server:		127.0.1.1Address:	127.0.1.1#53


Non-authoritative answer:
Name:	ubuntu.com
Address: 91.189.94.156


[COLOR=#000000]

[/COLOR][COLOR=#000000]dig ubuntuforums.org:[/COLOR][COLOR=#000000]

> [/COLOR]; <<>> DiG 9.8.1-P1 <<>> ubuntuforums.org;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 50250
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 0, ADDITIONAL: 0


;; QUESTION SECTION:
;ubuntuforums.org.		IN	A


;; ANSWER SECTION:
ubuntuforums.org.	281	IN	A	91.189.94.12


;; Query time: 142 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sat Apr 27 11:24:56 2013
;; MSG SIZE  rcvd: 50


[COLOR=#000000]



[/COLOR]

---

