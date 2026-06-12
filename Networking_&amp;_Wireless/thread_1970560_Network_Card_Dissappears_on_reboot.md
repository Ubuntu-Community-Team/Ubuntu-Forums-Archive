---
title: "Network Card Dissappears on reboot"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by adaroqui on 2012-05-01
Hello,

I am having an issue with my 10.4 LTS installation in which my network card disappears on reboot and requires me to reinstall it. It has been this way since I first installed the system.

(By reinstalling, I basically:

make install the driver
sudo rmmod -f e1000e
sudo modprobe e1000e
sudo /etc/init.d/networking restart

and all is good ... until the next reboot.)

Any advice on stopping the issue is appreciated. Let me know if you need any additional information. 

anthony@anthony-desktop:~$ uname -a
Linux anthony-desktop 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:08:43 UTC 2012 i686 GNU/Linux

anthony@anthony-desktop:~$ dmesg | grep e1000e
[  483.412663] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[  483.412667] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[ 1228.477304] e1000e: Intel(R) PRO/1000 Network Driver - 1.2.20-NAPI
[ 1228.477307] e1000e: Copyright(c) 1999 - 2010 Intel Corporation.
[ 1228.477348] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 1228.477358] e1000e 0000:00:19.0: setting latency timer to 64
[ 1228.555931] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[ 1228.752279] e1000e 0000:00:19.0: eth1: (PCI Express:2.5GB/s:Width x1) 10:78:d2:fc:79:86
[ 1228.752281] e1000e 0000:00:19.0: eth1: Intel(R) PRO/1000 Network Connection
[ 1228.752344] e1000e 0000:00:19.0: eth1: MAC: 11, PHY: 11, PBA No: FFFFFF-0FF
[ 1228.914072] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[ 1228.969797] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[ 1244.770136] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 1244.770141] e1000e 0000:00:19.0: eth1: 10/100 speed: disabling TSO
[ 1423.723282] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[ 1423.779029] e1000e 0000:00:19.0: irq 27 for MSI/MSI-X
[ 1425.333260] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 1425.333265] e1000e 0000:00:19.0: eth1: 10/100 speed: disabling TSO

00:19.0 Ethernet controller: Intel Corporation Device 1503 (rev 05)
    Subsystem: Lenovo Device 3616
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at fe700000 (32-bit, non-prefetchable) [size=128K]
    Memory at fe728000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at f040 [size=32]
    Capabilities: [c8] Power Management version 2
    Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
    Capabilities: [e0] PCIe advanced features <?>
    Kernel driver in use: e1000e
    Kernel modules: e1000e

(before install)

anthony@anthony-desktop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=0
       resources: memory:fe700000-fe71ffff memory:fe728000-fe728fff ioport:f040(size=32)

(after install)

anthony@anthony-desktop:~$ sudo lshw -C network
[sudo] password for anthony: 
  *-network               
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 05
       serial: 10:78:d2:fc:79:86
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-NAPI duplex=full firmware=0.13-4 ip=192.168.0.116 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:fe700000-fe71ffff memory:fe728000-fe728fff ioport:f040(size=32)

---

### Post by chili555 on 2012-05-01
Please try this:```
sudo su
echo e1000e >> /etc/modules
exit
```Now does it work on boot?

---

### Post by adaroqui on 2012-05-01
Yup. It now works on boot.

Thanks.

---

### Post by chili555 on 2012-05-01
Good! Please use thread tools at the top and Mark Solved.

---

### Post by adaroqui on 2012-05-18
Chalk it up to not having to reboot Linux often I suppose... 

When I tested it two weeks ago, everything was fine, I had to reboot the machine today and the driver disappeared again.

Of course after reinstalling it was fine, and then a 2nd reboot to test didn't remove the driver... so I'm at a loss.

I'll reboot a bit more often and see if it occurs again unless anyone has any ideas.

---

