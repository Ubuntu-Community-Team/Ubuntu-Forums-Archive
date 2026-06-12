---
title: "Can't connect to wired network"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by vlzk on 2013-05-21
I installed ubuntu 12.04 yesterday and can't connect to wired network, it tries several times and says "disconnected".
The cable itself should be fine since it works on xp without problems.
I'm a first time user of linux so explain like I'm five if you manage to find out the problem.

```

ifconfig

eth0    Link encap:Ethernet  HWaddr 00:13:d3:f3:44:46            inet6 addr: fe80::213:d3ff:fef3:4446/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:380 errors:0 dropped:0 overruns:0 frame:0
          TX packets:380 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43135 (43.1 KB)  TX bytes:43135 (43.1 KB)


usb0      Link encap:Ethernet  HWaddr f2:8c:e9:08:13:37  
          inet addr:192.168.42.208  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::f08c:e9ff:fe08:1337/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2312 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2327794 (2.3 MB)  TX bytes:234180 (234.1 KB)



```

```

lspci

00:00.0 Host bridge: Advanced Micro Devices [AMD] nee ATI RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI RS480 PCI-X Root Port
00:12.0 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 Serial ATA Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB2 Host Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: Advanced Micro Devices [AMD] nee ATI IXP SB400 IDE Controller
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [GeForce 9400 GT] (rev a1)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)



```

---

### Post by vlzk on 2013-05-21
forgot to say; during this post I connected my computer to internet trough my phone, so if that distorts the data tell me

---

### Post by Bucky Ball on 2013-05-21
Could you post the output of this, please (without the phone plugged):

```
sudo lshw -C network
```

---

### Post by vlzk on 2013-05-21
```

  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:f3:44:46
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:df00(size=256) memory:fdeff000-fdeff0ff memory:fdd00000-fdd0ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: f2:8c:e9:08:13:37
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.208 link=yes multicast=yes



```

---

### Post by SJR Dorset on 2013-05-21
It could be that there is no DCHP Server on you network so you computer cannot acquire an IP address.

---

### Post by vlzk on 2013-05-21
can I fix it somehow?

---

### Post by vlzk on 2013-05-21
> **Bucky Ball said:**
> Could you post the output of this, please (without the phone plugged):

```
sudo lshw -C network
```

sorry, heres the code w/out phone

```

 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:f3:44:46
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 ioport:df00(size=256) memory:fdeff000-fdeff0ff memory:fdd00000-fdd0ffff



```

---

### Post by Bucky Ball on 2013-05-21
Well that looks like the card is up and running. Probably another problem. 

```
broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=yes
```

You can set a static IP in Network Manager and see if that makes a difference. You'll need to know the IP of your router and gateway for this.

Right network icon>Wireless>Edit>IPv4 Settings. You can set up the static IP there. You might (will) find problems if your router (or ISP if you're not using one) is attempting to serve you an IP at the same time.

---

### Post by vlzk on 2013-05-21
I tried manually adding the IP and gateway etc. in every way possible. Everytime it says "connected" but I won't actually have internet connection

---

### Post by Bucky Ball on 2013-05-21
Well, if it's saying connected then sounds like it is and your problem is external to your computer, possibly the router. Is this router working fine for other machines?

Try pinging the router. For this you are going to need the router's IP then open a terminal and:

```
ping ***.***.***.***
```

Where '***.***.***.***' = the router's IP. If your machine says it is connected but you can't ping the router, then problem possibly with the router set up. You can have a look at how you have the router set up by putting its IP into a web browser. That should bring up the configuration page for the router and you can have a look if anything is amiss there. It is still possible you have successfully set a static IP on the local machine but the router is trying to serve you one at the same time. That will never end well.

Could you also supply the output of:

```
ifconfig
```

---

### Post by vlzk on 2013-05-23
> 
[COLOR=#000000]Well, if it's saying connected then sounds like it is and your problem is external to your computer, possibly the router. Is this router working fine for other machines?[/COLOR]


I think it says connected no matter what values I put in (but I tried everything I could think of just to make sure I didn't mess up with the adresses)
Every other computer, including this one, get connection without a problem, only with ubuntu I can't get connection (I use this same computer to run windows xp and ubuntu, in separate HDD)

This is w/ the router IP
```

ping 87.100.194.98
connect: Network is unreachable

```

And this is the gateway address, I wasn't sure which one I was supposed to use in this instance
```

ping 87.100.128.1
connect: Network is unreachable

```


I acquired both addresses with windows xp if it matters

```

ifconfig

eth0      Link encap:Ethernet  HWaddr 00:13:d3:f3:44:46  
          inet6 addr: fe80::213:d3ff:fef3:4446/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2642 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2642 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:212893 (212.8 KB)  TX bytes:212893 (212.8 KB)



```

I tried to access the router settings trough both, windows xp and ubuntu, but I couldn't, and I find this odd since XP does have connection to the router so it couldn't be about that.
I also tried to access with windows 7 laptop (wireless) without luck

I dont know if this helps but I did ```
 ping -r (1-9) www.google.com 
``` with windows XP and it timed out everytime

---

### Post by Bucky Ball on 2013-05-23
The router IP. 

Right click the network icon, edit connections, IPv4 tab and make sure 'Method' is 'Automatic (DHCP)'.

Anything acquired by XP has nothing whatever to do with the Ubuntu install. Never the twain shall meet. Nothing you do in one OS has any effect whatever on the other (unless you do something radical like wipe a partition/drive). They are two different OSs on separate partitions so they may as well be on different machines.

---

### Post by vlzk on 2013-05-24
> **Bucky Ball said:**
> The router IP. 

Right click the network icon, edit connections, IPv4 tab and make sure 'Method' is 'Automatic (DHCP)'.

Anything acquired by XP has nothing whatever to do with the Ubuntu install. Never the twain shall meet. Nothing you do in one OS has any effect whatever on the other (unless you do something radical like wipe a partition/drive). They are two different OSs on separate partitions so they may as well be on different machines.

yes the IPv4 is on "automatic", I have also tried to put them in manually with no luck. I know XP and ubuntu are a completely different thing, what I meant was that I used the XP console to get the router IP and gateway etc. since I can't get them with ubuntu because it cannot make any connection to the router. I hope the IP or gateway is not affected by witch OS I'm using.

---

### Post by Bucky Ball on 2013-05-24
No point putting static IP in the local machine as that will cause more confusion if the router is trying to serve you one via DHCP. The router it trying to send the local machine an IP and the local machine is trying to send its static IP to the router ... train wreck. Leave set to Automatic (as I presume there is no static IP set in Windows so you must be getting served one via DHCP by the router or your ISP possibly. 

Go ahead and access the router via Win or whatever. Makes no diff. ;)

---

### Post by vlzk on 2013-05-25
Yes, well that's the problem, ubuntu doesn't seem to be able to make the connection automatically, and I didn't succeed with adding the settings manually either.

---

