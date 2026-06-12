---
title: "Ubuntu 11.10 internet not working on Asus EEE PC 1001 PXD"
date: 2012-02-21
forum: Networking &amp; Wireless
---

### Post by Mentalhead on 2012-02-21
I'm running Live Ubuntu 11.10 from SD card on Asus EEE PC 1001 PXD.
My hard drive is corrupted, so I cannot install it, however that's not the problem.
After I've started live Ubuntu for the first time, both LAN and WiFi worked without any problems, but all of the sudden internet stopped working.
I manage to connect to wired or wireless network, but internet isn't working, so can anyone help me out?
I'm Ubuntu newbie, so please keep that in mind.

---

### Post by roelforg on 2012-02-21
May i ask why a corrupted HD is gonna prevent ubuntu from installing as it's gonna wipe the HD anyway?

---

### Post by Mentalhead on 2012-02-21
Tried it, continue button is unusable.
Anyway, I don't want to install it, I want to run it from my SD card, and it works great, however, internet has stopped working for some reason.

---

### Post by roelforg on 2012-02-21
Let me quote my guide:
> 
===== THE ONOFFICIAL GUIDE OF STUFF TO INCLUDE WHEN ASKING FOR HELP ON THE UBUNTU FORUMS =====

==== Networking ====

== No/Slow Internet
The output of (run from root console (sudo bash)):
```

ifconfig -a
cat /etc/network/interfaces
uname -a
cat /etc/resolv.conf
lshw -C network #this can take a while

```Anyway, on a HD ubuntu is way faster and, as you said yourself, the disk isn't working anyway so what's the loss?
I suggest using gparted to erase/wipe the HD, fill it with 1 partition and run the installer (also i think the installer won't work because you missed a setting, try youtube, there are a lot of video's regarding installing ubuntu).

FYI: it's a guide i wrote for myself so i have a list of things to ask people for when they're asking for help.

---

### Post by Mentalhead on 2012-02-21
gparted is only detecting my pen drive, or my SD card, so this probablyif means that my HDD is dead.

I ran the terminal, so here's my output:
```

ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 54:04:a6:05:b5:88  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:fe05:b588/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:10749 (10.7 KB)  TX bytes:41961 (41.9 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61296 (61.2 KB)  TX bytes:61296 (61.2 KB)

wlan0     Link encap:Ethernet  HWaddr 74:2f:68:8f:07:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
ubuntu@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Input/output error
ubuntu@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Input/output error
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:2f:68:8f:07:42
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 54:04:a6:05:b5:88
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.



```

---

### Post by roelforg on 2012-02-21
> **Mentalhead said:**
> gparted is only detecting my pen drive, or my SD card, so this probablyif means that my HDD is dead.

I ran the terminal, so here's my output:
```

ubuntu@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 54:04:a6:05:b5:88  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:fe05:b588/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:10749 (10.7 KB)  TX bytes:41961 (41.9 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:768 errors:0 dropped:0 overruns:0 frame:0
          TX packets:768 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:61296 (61.2 KB)  TX bytes:61296 (61.2 KB)

wlan0     Link encap:Ethernet  HWaddr 74:2f:68:8f:07:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux
ubuntu@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Input/output error
ubuntu@ubuntu:~$ cat /etc/resolv.conf
cat: /etc/resolv.conf: Input/output error
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:2f:68:8f:07:42
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 54:04:a6:05:b5:88
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.3 latency=0 multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128)
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.



```
Try again but first issue
```

sudo bash

```
before executing the commands.
Also, i'd try opening your pc up and checking the cables of the HD, check if they're connected properly;
My pc wouldn't detect my DVD-drive because the IDE cable got loose after moving it.

Gotta go, see ya tomorrow!

---

