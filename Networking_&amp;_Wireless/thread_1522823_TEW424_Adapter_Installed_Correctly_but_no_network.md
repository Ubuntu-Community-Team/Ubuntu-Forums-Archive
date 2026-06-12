---
title: "TEW424 Adapter Installed Correctly but no network"
date: 2010-07-02
forum: Networking &amp; Wireless
---

### Post by Verenda on 2010-07-02
Hi,

A brand new ubuntu user here that just installed the latest ubuntu release. I have the TEW424 adapter and followed the ndiswrapper instructions for installing it. However, after a successful installation, I cannot access my wireless network at home (icon has a red X on it). I am at a complete loss as to what is the problem or how to fix it. 

When running lshw -C network:
>                       user@user-desktop:~$ lshw -C network
  
  WARNING: you should run this program as super-user.
  
    *-network               
  
         description: Ethernet interface
  
         product: 3c905C-TX/TX-M [Tornado]
  
         vendor: 3Com Corporation
  
         physical id: c
  
         bus info: pci@0000:02:0c.0
  
         logical name: eth0
  
         version: 78
  
         serial: 00:06:5b:a5:14:d2
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: bus_master cap_list rom ethernet physical
  
         configuration: broadcast=yes driver=3c59x latency=64 maxlatency=10 mingnt=10 multicast=yes
  
         resources: irq:18 ioport:dc00(size=128) memory:ff6efc00-ff6efc7f memory:18000000-1801ffff(prefetchable)
  
   
When running iwconfig:

>                    user@user-desktop:~$ iwconfig
    lo        no wireless extensions.
     
   
  eth0      no wireless extensions.
     When checking if the driver is working on ndiswrapper:

>                    user@user-desktop:~$ ndiswrapper -l
    WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
    sis163u : driver installed
     device (0457:0163) present
     

If anyone can help point me in the right direction, that'd be great

---

