---
title: "Udev rule is ignored for eth devices"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by Zakhafr on 2010-06-03
Hello,

I'm trying to set my network interfaces so that they don't get random every boot.
*(eg assign **eth0** to a network interface with a given **MAC addr**, and **eth1** to the other one)*

I trew in a udev rule (in fact just modified the rules that was automatically generated and set the ethX in it) but _the system ignores my udev rule_.

What am I missing ?

Here is all the info :

```
$cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:18:f3:cd:83:2c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x11ab:0x4362 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:18:f3:cd:73:8c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:f3:cd:83:2c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:19 

eth1      Link encap:Ethernet  HWaddr 00:18:f3:cd:73:8c  
          inet adr:192.168.0.130  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::218:f3ff:fecd:738c/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:1101 erreurs:0 :0 overruns:0 frame:0
          TX packets:1156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:682128 (682.1 KB) Octets transmis:336863 (336.8 KB)
          Interruption:16
```
We see that het MAC addr 00:18:f3:cd:**83:2c** should have **eth1** according to udev, but in fact it gets eth0 :rolleyes:

udevadm info gets me nothing wrong about my rule:

```
$ udevadm info -a -p /sys/class/net/eth0

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/net/eth0':
    KERNEL=="eth0"
    SUBSYSTEM=="net"
    DRIVER==""
    ATTR{addr_len}=="6"
    ATTR{dev_id}=="0x0"
    ATTR{ifalias}==""
    ATTR{iflink}=="2"
    ATTR{ifindex}=="2"
    ATTR{features}=="0x109a3"
    ATTR{type}=="1"
    ATTR{link_mode}=="0"
    ATTR{address}=="00:18:f3:cd:83:2c"
    ATTR{broadcast}=="ff:ff:ff:ff:ff:ff"
    ATTR{carrier}=="0"
    ATTR{dormant}=="0"
    ATTR{operstate}=="down"
    ATTR{mtu}=="1500"
    ATTR{flags}=="0x1003"
    ATTR{tx_queue_len}=="1000"

  looking at parent device '/devices/pci0000:00/0000:00:1c.3/0000:04:00.0':
    KERNELS=="0000:04:00.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="sky2"
    ATTRS{vendor}=="0x11ab"
    ATTRS{device}=="0x4362"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x8142"
    ATTRS{class}=="0x020000"
    ATTRS{irq}=="30"
    ATTRS{local_cpus}=="00000000,00000003"
    ATTRS{local_cpulist}=="0-1"
    ATTRS{modalias}=="pci:v000011ABd00004362sv00001043sd00008142bc02sc00i00"
    ATTRS{numa_node}=="0"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""
```
I am on Karmic 64
```
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```
```
$ uname -a
Linux zakhar-desktop 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux
```
```
$ lspci
(.....)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
```
```
$dmesg
(...)
[    1.738451] sky2 driver version 1.23
[    1.738545] sky2 0000:04:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.738560] sky2 0000:04:00.0: setting latency timer to 64
[    1.738597] sky2 0000:04:00.0: Yukon-2 EC chip revision 2
[    1.738673]   alloc irq_desc for 30 on node 0
[    1.738676]   alloc kstat_irqs on node 0
[    1.738690] sky2 0000:04:00.0: irq 30 for MSI/MSI-X
[    1.739317] sky2 eth0: addr 00:18:f3:cd:83:2c
[    1.739381] sky2 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.739392] sky2 0000:03:00.0: setting latency timer to 64
[    1.739420] sky2 0000:03:00.0: Yukon-2 EC chip revision 2
[    1.739495]   alloc irq_desc for 31 on node 0
[    1.739497]   alloc kstat_irqs on node 0
[    1.739508] sky2 0000:03:00.0: irq 31 for MSI/MSI-X
[    1.740214] sky2 eth1: addr 00:18:f3:cd:73:8c
```
Here we see on dmesg that it does NOT care of what is in udev. It takes the first interface, which here is the one finishing by **83:2c**, and gives it **eth0** although udev says it should be  eth1

The problem is interfaces are presented randomly by the BIOS to the system according to the moment when they are ready. Yesterday, they were reversed, and thus got right... but it is just randomly right.

This is quite bad as this PC is also a router, and thus I have to know which interface is eth0 and which is eth1.

Dis I miss something?

Is my rule incorrect (it is just a modification of the auto-generated rule, where I specify the ethX)

Is it a known bug?

Many thanks in advance.

---

### Post by Zakhafr on 2010-06-04
Anyone on that ? ):P

---

### Post by Zakhafr on 2010-06-07
Still nobody on that?

Well, it might be real bug, so if nobody has any clue I'll take a chance posting a bug report on the Launchpad.

---

### Post by Zakhafr on 2010-06-12
So, it's now reported here as a bug:

[https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/592963]("https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/592963")

Feel free to contribute (here or on launchpad)!

---

