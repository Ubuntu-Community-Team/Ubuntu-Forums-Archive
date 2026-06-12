---
title: "Wireless does not work (gets connected to network successfully though)"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by dineshbabumm on 2010-06-10
Hello Every one,

I just upgraded to 10.04 from 9.10 and I ran into few issues.
Laptop - Dell Vostro 1520
OS - Ubuntu 10.04 64 bit

Issue - My wifi connects to the network properly and shows connection established. But I am not able to browse. I tried ping and I didn't got any response. But I was able to get response when I use ethernet (wired connection) and I am able to browse. No issues with wifi card as my wifi is working properly from Windows and with the same network.

I did a complete update again before posting this and it is yet to be resolved.

Here are the output of some commonly asked outputs with wifi enabled and connected:

1. sudo lshw -C network
>   *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:dd:f2:c7
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.4 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:30 ioport:3000(size=256) memory:f6004000-f6004fff(prefetchable) memory:f6000000-f6003fff(prefetchable) memory:f6020000-f603ffff(prefetchable)
  *-network
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth1
       version: 01
       serial: 0c:60:76:09:29:6e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 ip=192.168.1.2 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:fa000000-fa003fff


2. ifconfig
> 
eth0      Link encap:Ethernet  HWaddr 00:24:e8:dd:f2:c7  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fedd:f2c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23121 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16021 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32073593 (32.0 MB)  TX bytes:1713363 (1.7 MB)
          Interrupt:30 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 0c:60:76:09:29:6e  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe09:296e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:17266
          TX packets:32 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2196 (2.1 KB)  TX bytes:7917 (7.9 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


3. iwconfig
> 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:235  Noise level:164
          Rx invalid nwid:0  invalid crypt:2  invalid misc:0


4. lspci -nn

> 08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
0e:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)


5. dmesg | grep 816
> [    1.003173] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.003196] r8169 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.003241] r8169 0000:08:00.0: setting latency timer to 64
[    1.003314] r8169 0000:08:00.0: irq 30 for MSI/MSI-X
[    1.003792] eth0: RTL8168d/8111d at 0xffffc90000676000, 00:24:e8:dd:f2:c7, XID 081000c0 IRQ 30
[   16.838727] r8169: eth0: link up
[   16.838735] r8169: eth0: link up



Any suggestions how to get rid of this problem is highly appreciated. Thanks a lot for patiently reading till this and hope that I can get some help in resolving this. :)

---

### Post by gordintoronto on 2010-06-10
Are you using a static IP address or DHCP? What appears when you enter this Terminal command:
cat /etc/resolv.conf

Mine shows the two DNS servers I use.

---

### Post by dineshbabumm on 2010-06-14
> **gordintoronto said:**
> Are you using a static IP address or DHCP? What appears when you enter this Terminal command:
cat /etc/resolv.conf

Mine shows the two DNS servers I use.

Hi, thanks a lot for replying and I apologize for delayed response. This is the output I got:

dinesh@dinesh-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
nameserver 192.168.1.1

I have my wired connection hooked up while I typed that command in my terminal.

Thanks.

---

### Post by Iowan on 2010-06-14
What does **route -n** reveal? Having both interfaces in the same subnet will (probably) play havoc with routing...

---

### Post by gordintoronto on 2010-06-14
The file you displayed is generated "on the fly" during bootup/logon. If you look at it when you are not wired to the router, it might help get a solution.

---

### Post by dineshbabumm on 2010-06-15
> **gordintoronto said:**
> The file you displayed is generated "on the fly" during bootup/logon. If you look at it when you are not wired to the router, it might help get a solution.

This is the response when I entered the command with only my wireless on.

> dinesh@dinesh-laptop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1


I think internet is working. I did the driver update. I am getting reply in ping. Also google.com loads very slowly. I guess it is just that internet is too slow. This seems to be a common problem as I saw many threads on the same issue without any solution.

The response for ping:

> dinesh@dinesh-laptop:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (72.14.204.104) 56(84) bytes of data.
64 bytes from 72.14.204.104: icmp_seq=8 ttl=54 time=28.5 ms
64 bytes from 72.14.204.104: icmp_seq=57 ttl=54 time=28.4 ms
64 bytes from 72.14.204.104: icmp_seq=58 ttl=54 time=125 ms
64 bytes from 72.14.204.104: icmp_seq=59 ttl=54 time=2011 ms
64 bytes from iad04s01-in-f104.1e100.net (72.14.204.104): icmp_seq=60 ttl=54 time=1013 ms
64 bytes from iad04s01-in-f104.1e100.net (72.14.204.104): icmp_seq=61 ttl=54 time=40.1 ms
64 bytes from 72.14.204.104: icmp_seq=63 ttl=54 time=1064 ms
64 bytes from iad04s01-in-f104.1e100.net (72.14.204.104): icmp_seq=65 ttl=54 time=1001 ms
64 bytes from iad04s01-in-f104.1e100.net (72.14.204.104): icmp_seq=66 ttl=54 time=404 ms


If any one knows any solution kindly let me know.

Thanks!

---

### Post by dineshbabumm on 2010-06-16
> **Iowan said:**
> What does **route -n** reveal? Having both interfaces in the same subnet will (probably) play havoc with routing...
I am very sorry to have missed your post in the middle. This is the output I got for route -n:

> dinesh@dinesh-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1


I once again apologize for missing this out. Thanks!

---

### Post by Iowan on 2010-06-16
Curious - looks like everything is going through eth1.

---

### Post by dineshbabumm on 2010-06-16
> **Iowan said:**
> Curious - looks like everything is going through eth1.

I didn't had my wired net connection on when I typed that command. Also it looks like my wireless internet is working. I did a driver update for my wifi driver. I am getting response for ping. But it is way too slow. gmail does not load and google.com takes a long time to load. I guess many are facing this problem as I saw several unsolved threads on the same issue.

---

### Post by Iowan on 2010-06-16
> **dineshbabumm said:**
>  I am getting response for ping. But it is way too slow.  That would be fodder for a new thread. Glad to hear wireless is working. If it STAYS working, consider marking the thread [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"). :)

---

