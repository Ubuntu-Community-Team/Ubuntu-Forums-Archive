---
title: "Problems with network configuration in QDI Kudoz 7e/333"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by leillo1975 on 2012-05-31
Hello again

In my work we have a lot of old PC's that I take it for people to use them to see things on internet or use with office applications,  and I have trouble installing Ubuntu and variants (Mint, Xubuntu, Lubuntu, etc).

The problem is that the installation was done properly and everything seems to work fine, but the network don't work.

If I configure network with static IP (I don't try with DHCP because our network is static) don't connect.

Network cards in this CPU's are different (3com, OvisLink, dlink, etc) but happens to all the same. Changing all items of CPU (graphics, memory, etc) I get the same results.

I googled a bit, but noone seems to install linux on these machines or does not have the same problem. Let's see if we are lucky and someone can help me.

This is the configuration of the Computers:

Processor: AMD 1700 XP
Motherboard: QDI KudoZ 7e/333
Memory: 1.5 GB DDR
Hard drive: 60 GB
Soundcard: on-board
t.video: NVIDIA GeForce 2 MX200
t.red: 3COM ETEHERNET LINK
CD / DVD: LG DVD-RW + DVD LG

If I do a Ctrl + Alt + F1 I get this:

[[https://picasaweb.google.com/lh/photo/4OwCfhQMjkcjg33A6-o910gdcChfXRsD4hxF7Uj9JNo?feat=directlink](https://picasaweb.google.com/lh/photo/4OwCfhQMjkcjg33A6-o910gdcChfXRsD4hxF7Uj9JNo?feat=directlink)

I try to configure manualy in a Terminal, but I have the same results

This is my network configuration:

```
leo@MULTIMEDIA2-UB24:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:2e:f3:81:90  
          inet addr:192.168.0.194  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2eff:fef3:8190/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4486 (4.4 KB)  TX bytes:4486 (4.4 KB)
```

If I do:

```
leo@MULTIMEDIA2-UB24:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...  
```

If a use a USB Wifi Adapter I can connect....????

Sorry, my english is very bad

---

### Post by leillo1975 on 2012-05-31
I purge network-manager and install manually wicd, but the results are the same: no ethernet and usb-wifi working

---

### Post by leillo1975 on 2012-06-01
More information: I tryed with Fedora 17 and Knoppix 7, but I have the same problem

---

