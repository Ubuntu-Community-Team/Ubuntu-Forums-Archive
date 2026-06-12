---
title: "No internet connection"
date: 2010-07-12
forum: Networking &amp; Wireless
---

### Post by ganewbie on 2010-07-12
> **DavorC said:**
> @Detonate: I thought NetworkManager is the preferred way of doing networking now. Using /etc/network/interfaces as a workaround is fine, but solving the problem in the network manager instead of uninstalling it is even better.
 I followed the information above by not knowing what could happen, now how do I install the Network manager again. Help PLEASE!

---

### Post by Detonate on 2010-07-12
> **ganewbie said:**
> I followed the information above by not knowing what could happen, now how do I install the Network manager again. Help PLEASE!

Do you have an internet connection?

---

### Post by ganewbie on 2010-07-12
No internet

---

### Post by Detonate on 2010-07-12
OK, run the following commands in a terminal and post the results.  We will go one step at a time.
```
ifconfig -a
```
```
cat /etc/network/interfaces
```

---

### Post by ganewbie on 2010-07-12
/etc/NetworkManager/NetworkManager.conf
[main] 
plugins=ifupdown,keyfile 
no-auto-default=6c:f0:49:b1:7b:85, 
[ifupdown] 
managed=false
************************************************** ********************************
sudo lshw -c network 
george@george-desktop:~$ 
[sudo] password for george: 
*-network DISABLED 
description: Ethernet interface 
product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 0 
bus info: pci@0000:02:00.0 
logical name: eth0 
version: 03 
serial: 6c:f0:49:b1:7b:85 
size: 100MB/s 
capacity: 1GB/s 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s 
resources: irq:26 ioport:de00(size=256) memory:fdaff000-fdafffff(prefetchable) memory:fdaf8000-fdafbfff(prefetchable) memory:fda00000-fda1ffff(prefetchable) 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;[/SIZE][/FONT]
[/SIZE][/FONT]george@george-desktop:~$ lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate 
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) 
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode] 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3c) 
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control 
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control 
01:05.0 VGA compatible controller: ATI Technologies Inc Device 9715 
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03) 
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;[/SIZE][/FONT]
[/SIZE][/FONT]george@george-desktop:~$ iwconfig 
lo no wireless extensions. 
eth0 no wireless extensions.

---

### Post by ganewbie on 2010-07-12
Here is more.
 
george@george-desktop:~$ ifconfig -a 
eth0 Link encap:Ethernet HWaddr 6c:f0:49:b1:7b:85 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:3 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:1240 (1.2 KB) TX bytes:0 (0.0 B) 
Interrupt:26 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]eth0:avahi Link encap:Ethernet HWaddr 6c:f0:49:b1:7b:85 
inet addr:169.254.9.27 Bcast:169.254.255.255 Mask:255.255.0.0 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
Interrupt:26 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B) 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]george@george-desktop:~$ cat /etc/network/interfaces 
auto lo 
iface lo inet loopback 
address 127.0.0.1 
netmask 255.0.0.0 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]# The primary network interface 
auto eth0 
iface eth0 inet dhcp

---

### Post by Detonate on 2010-07-12
OK, what happens when you run ```
/etc/init.d/networking start
```in a terminal?

---

### Post by ganewbie on 2010-07-12
george@george-desktop:~$ /etc/init.d/networking start 
Rather than invoking init scripts through /etc/init.d, use the service(8) 
utility, e.g. service networking start 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]Since the script you are attempting to invoke has been converted to an 
Upstart job, you may also use the start(8) utility, e.g. start networking 
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.59" (uid=1000 pid=2452 comm="start) interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

---

### Post by Detonate on 2010-07-12
My mistake.  Must be done as sudo.

Try```
sudo start networking
```

---

### Post by ganewbie on 2010-07-12
george@george-desktop:~$ sudo sart networking 
sudo: sart: command not found

---

### Post by Detonate on 2010-07-12
start not sart.

---

### Post by ganewbie on 2010-07-12
Sorry, here you are.
 
george@george-desktop:~$ sudo start networking 
networking stop/waiting

---

### Post by Detonate on 2010-07-12
Do you now have a connection?  What is the output of ```
ifconfig
```

---

### Post by ganewbie on 2010-07-12
No internet yet,
george@george-desktop:~$ ifconfig 
eth0 Link encap:Ethernet HWaddr 6c:f0:49:b1:7b:85 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:1540 (1.5 KB) TX bytes:0 (0.0 B) 
Interrupt:26 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]eth0:avahi Link encap:Ethernet HWaddr 6c:f0:49:b1:7b:85 
inet addr:169.254.9.27 Bcast:169.254.255.255 Mask:255.255.0.0 
UP BROADCAST MULTICAST MTU:1500 Metric:1 
Interrupt:26 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

---

### Post by Detonate on 2010-07-12
OK, try this.

```
sudo ifdown eth0
```

```
sudo ifup --force eth0
```

```
sudo start networking
```

```
ifconfig
```

---

### Post by ganewbie on 2010-07-12
Excellent, it works like magic. I am not sure what happened yet. How do I get to work again and how do I get the Network manager back into the system.
 
Here is what you have asked for:
 
george@george-desktop:~$ sudo ifdown eth0 
[sudo] password for george: 
* Stopping the Firestarter firewall... 
...done. 
* Starting the Firestarter firewall... 
...fail! 
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2 
There is already a pid file /var/run/dhclient.eth0.pid with pid 1820 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [_[COLOR=#0000ff]https://www.isc.org/software/dhcp/_[/COLOR]]("https://www.isc.org/software/dhcp/") 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]Listening on LPF/eth0/6c:f0:49:b1:7b:85 
Sending on LPF/eth0/6c:f0:49:b1:7b:85 
Sending on Socket/fallback 
george@george-desktop:~$ sudo ifup --force eth0 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [_[COLOR=#0000ff]https://www.isc.org/software/dhcp/_[/COLOR]]("https://www.isc.org/software/dhcp/") 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]Listening on LPF/eth0/6c:f0:49:b1:7b:85 
Sending on LPF/eth0/6c:f0:49:b1:7b:85 
Sending on Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPOFFER of 192.168.2.101 from 192.168.2.1 
DHCPREQUEST of 192.168.2.101 on eth0 to 255.255.255.255 port 67 
DHCPACK of 192.168.2.101 from 192.168.2.1 
bound to 192.168.2.101 -- renewal in 3087 seconds. 
* Stopping the Firestarter firewall... 
...done. 
* Starting the Firestarter firewall... 
...done. 
george@george-desktop:~$ sudo start networking 
networking stop/waiting 
george@george-desktop:~$ ifconfig 
eth0 Link encap:Ethernet HWaddr 6c:f0:49:b1:7b:85 
inet addr:192.168.2.101 Bcast:192.168.2.255 Mask:255.255.255.0 
inet6 addr: fe80::6ef0:49ff:feb1:7b85/64 Scope:Link 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 
RX packets:22 errors:0 dropped:0 overruns:0 frame:0 
TX packets:22 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:3852 (3.8 KB) TX bytes:2422 (2.4 KB) 
Interrupt:26 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0 
inet6 addr: ::1/128 Scope:Host 
UP LOOPBACK RUNNING MTU:16436 Metric:1 
RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:0 
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

---

### Post by Detonate on 2010-07-12
Great.  You see, what was causing the problem was that eth0 already had a PID left over from when it was previously connected  and that was preventing it from obtaining a new DHCP IP address.  By using the ifup --force command we made it bring up eth0 and reconfigure it at the same time, therefor removing the old PID.  Then it was able to get a new DHCP IP from the router.

The way you are set up now, your computer will automatically connect every time you boot up.  You don't need network manager.  However if you feel you really want it you can merely enter
```
sudo apt-get install network-manager network-manager-gnome
```
in a terminal.  Of course, it may break what we just fixed.

---

### Post by ganewbie on 2010-07-12
Thanks again,
I have updated UBUNTU and got the Network Manager back but when reboot No internet again?
What do I need to do?

---

### Post by Detonate on 2010-07-12
I warned you.  Do it all over again.  First remove network-manager and do not reinstall it.  I'm going to bed.

---

### Post by ganewbie on 2010-07-13
Thanks again, You are right it stopped but when I did the command below it worked and then stopped after the first reboot. Now I have the network manager but cannot do much with it as I can add but never able to save have no clue why.
Here is the results below again what is the problem now? Sorry I am late after a long day at work and gonna go to bed too.
 
george@george-desktop:~$ sudo ifdown eth0
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
There is already a pid file /var/run/dhclient.eth0.pid with pid 3006[
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/6c:f0:49:b1:7b:85
Sending on   LPF/eth0/6c:f0:49:b1:7b:85
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.2.1 port 67
george@george-desktop:~$ sudo ifup --force eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [url]https://www.isc.org/software/dhcp/[/urlListening on LPF/eth0/6c:f0:49:b1:7b:85
Sending on   LPF/eth0/6c:f0:49:b1:7b:85
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 192.168.2.102 from 192.168.2.1
DHCPREQUEST of 192.168.2.102 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.2.102 from 192.168.2.1
bound to 192.168.2.102 -- renewal in 3289 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.
george@george-desktop:~$ sudo start networking
networking stop/waiting

george@george-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:b1:7b:85  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:feb1:7b85/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2672 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1451417 (1.4 MB)  TX bytes:284534 (284.5 KB)
          Interrupt:26 Base address:0xe000

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
]          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by Iowan on 2010-07-14
The original thread seems completely hijacked, so this can be a new thread. Mark it [[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you're done... ;)

Also, from the Code of Conduct:
> Please use color and font properties for highlighting portions of your text, and not for all of the text in your post.

---

