---
title: "Internet dead after reinstalling 11.04 /w VMWare Player"
date: 2011-10-02
forum: Networking &amp; Wireless
---

### Post by TitusPullo on 2011-10-02
Hi, I have a Windows 7 machine and I installed Ubuntu 11.04 using VMWare Player.

The first install worked great, and Internet was working automatically, connecting to Auto.eth0, under "wired" even though my PC is connected to a wireless network.

I was trying to make Ubuntu access my Windows 7 hard drive partitions, when it froze. Trying to relaunch the Ubuntu guest OS using VMWare Player just resulted in the Player hanging when trying to load the Ubuntu OS.

So I reinstalled Ubuntu, same way as before, via VMWare and the ISO.

Now Internet WILL NOT WORK no matter what I do. I thought it was a MAC address problem, but the ifconfig -a command lists the same MAC address in the VMX config file, and it's the same MAC in the network connections box when you click the network icon in the front panel.

This is not a driver problem, as Ubuntu appears to detect it fine. Here are the results of ifconfig -a:

eth0      Link encap:Ethernet  HWaddr 00:0c:29:53:9d:6c  
          inet6 addr: fe80::20c:29ff:fe53:9d6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:61 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5770 (5.7 KB)  TX bytes:6665 (6.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8544 (8.5 KB)  TX bytes:8544 (8.5 KB)

I also tried "sudo dhclient" but this does nothing from the terminal. Just asks my password, then gives me a blank prompt like I did nothing.

WTF... I am at my wit's end.

---

