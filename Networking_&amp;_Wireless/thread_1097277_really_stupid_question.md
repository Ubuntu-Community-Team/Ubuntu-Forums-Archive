---
title: "really stupid question"
date: 2009-03-15
forum: Networking &amp; Wireless
---

### Post by shizumasa14 on 2009-03-15
Okay, so I got an Acer Aspire laptop PC.  It came with vista so what I did to connect to the internet was just select a network from a list and click connect.  Yesterday I wiped my hard drive and installed ubuntu.  How do I connect to a wireless network?

---

### Post by Iowan on 2009-03-15
Not a stupid question at all.  The answer may be a little complicated... I haven't yet installed Ubuntu on this laptop, but I read that wireless configuration can be tricky.  Fire up a terminal and check results of: **lshw -C network**That should tell you if the interface card has an alias. **ifconfig -a** should provide some other details about the interfaces.  Post results.

---

### Post by shizumasa14 on 2009-03-15
shizumasa14@shizumasa14-laptop:~$ ifconfig -a 
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:d7:2a:d8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:1017171668 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:219 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:404 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:27608 (27.6 KB)  TX bytes:27608 (27.6 KB) 

pan0      Link encap:Ethernet  HWaddr 32:0b:ee:f4:b7:d7  
          BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 








shizumasa14@shizumasa14-laptop:~$ lshw -C network 
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED     
       description: Network controller 
       product: RaLink 
       vendor: RaLink 
       physical id: 0 
       bus info: pci@0000:04:00.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
  *-network 
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1e:ec:d7:2a:d8 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 1 
       logical name: pan0 
       serial: 32:0b:ee:f4:b7:d7 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by shizumasa14 on 2009-03-16
Can someone help?

---

### Post by sgosnell on 2009-03-17
Have you clicked on the network icon in the panel to see networks?  If you see your network, have you clicked on it to try to connect?  You can also right-click on the network icon and select Edit Connections, add a new one with your parameters.  Or you can go to System/Administration/Network Tools.

You really haven't given enough information to even start helping you.

---

### Post by ugm6hr on 2009-03-17
A little more detail please.... See the wifi help? link below.

Specifically:
```
lspci
lsusb
```

Ralink wifi is generally well-supported in Linux, so there is hope.  The problem appears to be that you have no driver automatically installed.

---

