---
title: "Wireless networks detected from Live cd , but fails to detect after installation"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by k.sanjith on 2009-04-27
Hello All,

I was able to connect to my wireless network using the live CD, but after a fresh installation I am not even able to detect the wireless networks.

My driver is ath9k and the chipset is atheros.

Please let me know if more information is required.

Thanks!

---

### Post by Sprut1 on 2009-04-27
System > Administration > Hardware Drivers

Try enabling proprietary drivers.

---

### Post by k.sanjith on 2009-04-27
I don't find any proprietary drivers in that section. It is blank.


Thanks!

---

### Post by Sprut1 on 2009-04-27
Okay, this sounds like a weird bug which maybe should be filed to devs directly, I have no clue why this happens to you.

Are there even any interfaces up? Have you tried using network manager to connect manually?

---

### Post by k.sanjith on 2009-04-27
I am a newbie to Linux, So Please let me know how to do that.


I did a wubi install of ubuntu from windows vista. Can that be causing this weird issues.


Thanks!

---

### Post by Sprut1 on 2009-04-27
> **k.sanjith said:**
> I am a newbie to Linux, So Please let me know how to do that.


I did a wubi install of ubuntu from windows vista. Can that be causing this weird issues.


Thanks!

It might be the cause, not sure though. And I have no experience with Wubi installs what so ever. To check if there are any interfaces up you simply use the command "iwconfig" in terminal.

---

### Post by k.sanjith on 2009-04-27
I dont .see any wlan0 or wmaster0 interfaces that i see when in live cd.

san@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:22:15:29:6c:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:247 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

pan0      Link encap:Ethernet  HWaddr de:c3:4f:f0:c3:85  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:22:15:29:6c:11
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: de:c3:4f:f0:c3:85
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



Thanks

---

