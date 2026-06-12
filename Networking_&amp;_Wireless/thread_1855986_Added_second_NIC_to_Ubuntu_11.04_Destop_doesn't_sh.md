---
title: "Added second NIC to Ubuntu 11.04 Destop doesn't show in Network Manager"
date: 2011-10-07
forum: Networking &amp; Wireless
---

### Post by schapman43 on 2011-10-07
I've added a second NIC to my Ubuntu 11.04 box.  However, this second NIC isn't showing up in network manager.  lshw -C network shows the following.

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 48:5b:39:c3:dd:cb
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.10.2.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:b800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:fbaf0000-fbafffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:05:06.0
       version: 08
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=56 mingnt=8
       resources: memory:fbe00000-fbe00fff ioport:ec00(size=64) memory:fbd00000-fbdfffff memory:f0000000-f00fffff

```

The NIC that I added is the Intel NIC and is showing "UNCLAIMED".  

/etc/udev/rules.d/70-persistent-net.rules shows the following

```
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="48:5b:39:c3:dd:cb", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

lscpi | grep -Ethernet

```
lspci | grep -ethernet
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:06.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)

```

How do I got about getting this other card up and running?  Any help would be greatly appreciated.

---

### Post by vajorie on 2011-10-09
This will hopefully help: [http://ubuntuforums.org/showthread.php?t=1573396](http://ubuntuforums.org/showthread.php?t=1573396)

PS. Start with just a 

```

lsmod | grep e100
sudo modprobe e100 #if the output was empty to the previous command
sudo ifconfig -a #do you see it now? if not, see what that above link gives

```

---

### Post by schapman43 on 2011-10-10
> **vajorie said:**
> This will hopefully help: [http://ubuntuforums.org/showthread.php?t=1573396](http://ubuntuforums.org/showthread.php?t=1573396)

PS. Start with just a 

```

lsmod | grep e100
sudo modprobe e100 #if the output was empty to the previous command
sudo ifconfig -a #do you see it now? if not, see what that above link gives

```

```
lsmod | grep e100
e100                   40946  0 

```

Is that a good sign?

I'll check out the thread you posted.

Here is some additional info that may be helpfull.

```
dmesg | grep -e e100 -e eth
[    2.172101] i2c-core: driver [adp5520] using legacy suspend method
[    2.172103] i2c-core: driver [adp5520] using legacy resume method
[    2.675416] r8169 0000:02:00.0: eth0: RTL8168d/8111d at 0xffffc9001179c000, 48:5b:39:c3:dd:cb, XID 083000c0 IRQ 44
[    2.689130] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.689132] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.689475] e100 0000:05:06.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    2.795288] e100 0000:05:06.0: (unregistered net_device): EEPROM corrupted
[    2.795371] e100 0000:05:06.0: PCI INT A disabled
[    2.795396] e100: probe of 0000:05:06.0 failed with error -11
[   11.751976] r8169 0000:02:00.0: eth0: link down
[   11.751986] r8169 0000:02:00.0: eth0: link down
[   11.753348] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   13.470653] r8169 0000:02:00.0: eth0: link up
[   13.471352] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   23.610025] eth0: no IPv6 routers present

```

---

### Post by vajorie on 2011-10-10
I see this in your output

```

[    2.795288] e100 0000:05:06.0: (unregistered net_device): EEPROM corrupted

``` 

This is the same line [this user]("http://ubuntuforums.org/showthread.php?t=1573396") gets (liked in previous thread). I think it would be a good idea to follow the instructions there. 

S/he does two things: 

(1) Load the module with options (which can be made permanent if things work):

```
sudo rmmod e100
sudo modprobe e100 eeprom_bad_csum_allow=1

```

(2) Assign a mac address (in case you get the same error on the MAC address issue as well) once e100 starts to work:

```

rmmod e100
modprobe e100 eeprom_bad_csum_allow=1
ifconfig eth0 hw ether 00:00:00:00:00:00
ifconfig eth0 up

```

(1) Be careful, though: your interface is gonna be something other than eth0 in all likelyhood (you can find the interface using "ifconfig -a" once dmesg ("dmesg | tail" right after you loaded the module) reports that e100 is working ok.  

(2) The "hw ether ..." command spoofs your mac. It might be a better idea to use a more realistic mac address... Something like ```
00:24:D7:D4:33:9A
``` (generated [here]("http://www.macvendorlookup.com/") with a OUI for Intel --meaning that it starts with ```
00:24:D7
```).


PS. A side note: 
```

e100                   40946  0
```
I am not too sure, but the 0 in there means the module (driver) is loaded but not in use. Again, I'm not sure about this...

---

