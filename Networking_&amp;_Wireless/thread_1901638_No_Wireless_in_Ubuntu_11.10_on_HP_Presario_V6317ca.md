---
title: "No Wireless in Ubuntu 11.10 on HP Presario V6317ca"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by n00l3 on 2011-12-29
I installed Ubuntu 11.10 alongside Windows Vista on my HP Presario V6317ca laptop.  When I try to choose Windows Vista /dev/sda1 from the boot menu (called grub?), it goes back to the menu, but I don't mind that for now, as I can still see the files in Ubuntu.  The wireless did work on that before I installed Ubuntu.   

I went to System Settings -> Additional Drivers and did activated Broadcom STA wireless drivers but yet I cannot detect wireless signals and the light on the laptop is still red.

lspci | grep Broadcom\ Corporation
```
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```sudo lshw -C network
```
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b6000000-b6003fff

```ipconfig
```
eth0      Link encap:Ethernet  HWaddr 00:16:36:cb:b7:d2  
          inet addr:192.168.1.80  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fecb:b7d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6696 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7909772 (7.9 MB)  TX bytes:1136871 (1.1 MB)
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

