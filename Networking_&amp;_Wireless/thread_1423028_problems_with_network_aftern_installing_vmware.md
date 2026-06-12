---
title: "problems with network aftern installing vmware"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by lavy on 2010-03-06
Hi,

I've encountered a problem after installing vmware, actually after reboot.
Something similar happened to me when I've installed VirtualBox, I found a workaround then see [http://ubuntuforums.org/showthread.php?t=966960](http://ubuntuforums.org/showthread.php?t=966960)

Back to the matter at hand. I installed VMware and, after a few days, I rebooted my computer. First thing I've noticed was the internet wasn't working :) Since I have quite a reliable ISP I start investigating the problem. I connected my laptop to my router using a cable and everything was working properly.

I started investigating so I typed:
~$ ifconfig
In the output among the devices I noticed:
vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08
          inet addr:192.168.1.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

That device was inserted by wmware and had the same IP as my eth0. So I typed:
sudo ifconfig vmnet8 192.168.10.1 netmask 255.255.255.0
This changed the IP address of vmware. Then I made right click on knetworkmanager (in task tray) and click on wirednetwork - which activated the eth0 interface.
After I rebooted I happened again :confused:. I did the same thing described above.
**My question is: how can I make the changes permanently?** 

I assume is something from vmware. I tried editing the network interface devices but vmnet8 was not in the devices ($ sudo kate /etc/network/interfaces).

I use ubuntu 8.10, kde 3.5.
Tx

---

