---
title: "wireless stopped working, says module ndiswrapper not found"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by untitledtv on 2009-06-24
Hello,

Ndiswrapper installing

 DWL-G122/D1 
    

 from Synaptic worked fine...till I needed to follow the forum instructions on Jaunty slowness with Intel.

After that, it stopped working:

When I type sudo modprobe ndiswrapper, I get this error:

<
```
timothy@timothy-laptop:~$ sudo modprobe ndiswrapper
[sudo] password for timothy: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.
```>

Here is the info from ndiswrapper-l

<
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
usb55n5x : driver installed
    device (07D1:3B01) present
>

I went through the troubleshooting guide and so did a removal and reinstall but it doesn't seem to have done anything.

I do not evven see a wrieless infrastructure when lshw -C Network:

```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 20
       serial: 00:02:3f:64:a8:7d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139cp driverversion=1.3 ip=192.168.1.65 latency=128 maxlatency=64 mingnt=32 module=8139cp multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ae:e5:72:eb:da:07
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

