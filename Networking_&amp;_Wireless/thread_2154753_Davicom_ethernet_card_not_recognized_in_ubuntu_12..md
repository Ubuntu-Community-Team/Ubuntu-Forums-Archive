---
title: "Davicom ethernet card not recognized in ubuntu 12.04 lts and below"
date: 2013-06-15
forum: Networking &amp; Wireless
---

### Post by Jonathan Precise on 2013-06-15
Hello!

I have Ubuntu 12.04 LTS dual-booting with Windows 8. I also have a Davicom ethernet card model number DM9102F. However, Ubuntu doesn't have a driver for it. There is a driver for windows that I tried to install using a windows emulator, but that installation failed.

Windows allows the driver to be installed (from [http://www.davicom.com.tw/userfile/24247/D__Driver_Dm9009~1](http://www.davicom.com.tw/userfile/24247/D__Driver_Dm9009~1)[1].ZIP), and then successfully connects to the internet. Only ubuntu has that problem.

Also, [S]my computer cannot run a version of Ubuntu later than 12.04 LTS, due to insufficient memory.[/S] EDIT: Have roughly more than 1 GB RAM. Currently I have 14.04 LTS as only OS (ended up deleting windows as it was too much for my 1 GB machine)

Does anyone know where to find the driver for linux, or how to install the windows driver correctly on Ubuntu?

---

### Post by houstonbofh on 2013-06-15
Get a new nic.  Seriously, these have been crap cards since they were made by DEC, and called tulips.  Lots of OLD bugs, and no intentions to fix them.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435244](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/435244)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/819868](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/819868)
[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/31914](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/31914)

You can try the tulip driver, and doing ifdown and ifup commands a few times and see if it comes alive, but getting a new card will save you heartache...

---

### Post by Jonathan Precise on 2013-08-10
Got a new Ethernet card some time ago. Now it works!

Thread marked as solved.

Edit: marked as unsolved. See below post.

EDIT: Marked as solved again, and will move to a new thread.

---

### Post by Jonathan Precise on 2014-08-08
Hello Ubuntu forums community! Glad to see you all back.

[S]I now need to setup the same PC with two NICs and ubuntu 14.04 LTS. I only have the working D-Link NIC and the CNet (Davicom) NIC, and I'm not able to purchase a new NIC. I really need to fix this NIC, even if it will give headaches later. However, now the NIC isn't even recognized. Results from some commands:

```
ownerp@CASA-PROXY-SERVER-LINUX-UBUNTU:~$ sudo -i
[sudo] password for ownerp: 
root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# lshw -C network 
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c5:ed:5a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:b800(size=256) memory:dfeffc00-dfeffcff
root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:ba:c5:ed:5a  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec5:ed5a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22241 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17793 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26032088 (26.0 MB)  TX bytes:1938234 (1.9 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2274 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2274 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:228036 (228.0 KB)  TX bytes:228036 (228.0 KB)

root@CASA-PROXY-SERVER-LINUX-UBUNTU:~# 
```[/S]


[SIZE=1]Help... please...[/SIZE]



EDIT: I shall mark as solved again and create a new thread for this.

---

