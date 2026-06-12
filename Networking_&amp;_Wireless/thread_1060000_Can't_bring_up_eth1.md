---
title: "Can't bring up eth1"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by gene02 on 2009-02-04
After rebooting my machine yesterday (gutsy 7.10), my eth1 interface stopped working.  When I manually try 'ifup eth1', I get:

```
eth1: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.

```

The eth1 card is a RTL-8169 Gigabit Ethernet PCI card.  hwinfo reports this:
```

41: PCI 409.0: 0200 Ethernet controller
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_10ec_8169
  Unique ID: Emwg.oxSyVMMObW1
  Parent ID: 37TO._XJP+gD25h8
  SysFS ID: /devices/pci0000:00/0000:00:10.0/0000:04:09.0
  SysFS BusID: 0000:04:09.0
  Hardware Class: network
  Model: "Realtek RTL-8169 Gigabit Ethernet"  Vendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  Device: pci 0x8169 "RTL-8169 Gigabit Ethernet"
  SubVendor: pci 0x10ec "Realtek Semiconductor Co., Ltd."
  SubDevice: pci 0x8169 
  Revision: 0x10
  I/O Ports: 0x9c00-0x9cff (rw)
  Memory Range: 0xfdcff000-0xfdcff0ff (rw,non-prefetchable,disabled)
  Memory Range: 0xfdb00000-0xfdb1ffff (ro,prefetchable,disabled)
  IRQ: 10 (no events)
  Module Alias: "pci:v000010ECd00008169sv000010ECsd00008169bc02sc00i00"
  Driver Info #0:
    Driver Status: r8169 is active
    Driver Activation Cmd: "modprobe r8169"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #32 (PCI bridge)

```

I had recently updated the kernel from 2.6.22-14 to 2.6.22-16, but selecting the old kernel didn't seem to help.  I also tried recompiling the r8169 module, but that didn't help either.  Finally, I have a third ethernet interface, eth2, which I brought up and seems to be active, but I can't get the intranet working through it.  I'll describe that problem in a separate posting...


Thanks

---

### Post by Iowan on 2009-02-04
Try **lshw -C network** to see if that card actually gets aliased as eth1.

---

### Post by gene02 on 2009-02-04
The **lshw -C network** just prints out:

```

PCI (sysfs)

```

and sits there using 100% of the CPU.

---

### Post by Iowan on 2009-02-04
Interesting... My machine warns:```
WARNING: you should run this program as super-user.
CPUID 
```pauses for a couple of seconds, then spits out:```
  *-network               
       description: Ethernet interface
       product: 3c905B 100BaseTX [Cyclone]
       vendor: 3Com Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
      [COLOR="Red"] logical name: eth0[/COLOR]
       version: 64
       serial: 00:50:da:b0:f8:bd
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.1.11 latency=64 maxlatency=10 mingnt=10 module=3c59x multicast=yes

```

---

### Post by gene02 on 2009-02-05
I ran that command as root, by the way.

Anyway, after much playing around I did resolve the problem last night.  I tried choosing different options in the grub menu while booting and recovery mode gave me back my eth1 card.  I then saw that recovery mode had the **pci=noacpi** option in it, so I added that to the regular boot mode and my ethernet card was recognized again.

---

### Post by harrycool on 2010-08-16
I have a similar problem on a dell power edge 2950 box. It detects eth0  but not eth1. Here is the message when I restart the network. I checked  the configs on the /etc/network/interfaces file....it looks good.....

root@<server name>:~# /etc/init.d/networking restart
 *  Reconfiguring network  interfaces...                                                                                        eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.
Ignoring unknown interface bond0=bond0.


please help
I was able to see it before......I reimaged the box and then it disappeared.

---

