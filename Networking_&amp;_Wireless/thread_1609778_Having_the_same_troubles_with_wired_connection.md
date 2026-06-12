---
title: "Having the same troubles with wired connection"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by egkeat on 2010-10-30
I'm wondering why it is so hard for me to figure out how to stay connected to the internet?

I've asked this question over and over with no real answers. Went to Absolute Beginner Talk and it was helpful but no concrete answers to my issues.

Here I have

br@ubuntu:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:1e:8c:2b:06:8d 
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:28 Base address:0xe000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:84 errors:0 dropped:0 overruns:0 frame:0
TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:9553 (9.5 KB) TX bytes:9553 (9.5 KB)

vboxnet0 Link encap:Ethernet HWaddr 0a:00:27:00:00:00 
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

br@ubuntu:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
br@ubuntu:~$ ping -c3 4.2.2.1
connect: Network is unreachable

then this:
results for ifconfig:

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:82 errors:0 dropped:0 overruns:0 frame:0
TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:9409 (9.4 KB) TX bytes:9409 (9.4 KB)


network:

*-network DISABLED
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 02
serial: 00:1e:8c:2b:06:8d
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
resources: irq:28 ioport:e800(size=256) memory:febff000-febfffff memory:fdff0000-fdffffff(prefetchable) memory:febc0000-febdffff(prefetchable)
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: vboxnet0
serial: 0a:00:27:00:00:00
capabilities: ethernet physical
configuration: broadcast=yes multicast=yes

and this:
output eth0:
br@ubuntu:~$ sudo ifup eth0 
Ignoring unknown interface eth0=eth0.
br@ubuntu:~$ 

same thing eth1:
br@ubuntu:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.

Why ignoring unknown interface?
I also notice in the network manager there is Vboxnet or something like that, saying unknown interface. What is this?

also instructed to do this:


This is what I get with lspci

lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)

Why does my internet work in Vista but not Ubuntu?

---

### Post by chili555 on 2010-10-30
> Why ignoring unknown interface?Here is a quote from man ifup:```
The ifup and ifdown commands  may be used to configure (or, respectively, deconfigure) network interfaces based on interface  definitions in the file /etc/network/interfaces.
```Is eth0 listed in /etc/network/interfaces? Nope. Network Manager manages interfaces only if they are *not* listed in /etc/network/interfaces.

Let's see what the kernel messages tell us. Please post:```
dmesg | grep -e eth0 -e 816
```Thanks.

---

### Post by egkeat on 2010-10-30
Ok, so after going back once again....

dmesg | grep -e eth0 -e 816
[    0.816064] ahci 0000:00:1f.2: version 3.0
[    0.816076]   alloc irq_desc for 19 on node -1
[    0.816078]   alloc kstat_irqs on node -1
[    0.816083] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.816112]   alloc irq_desc for 26 on node -1
[    0.816113]   alloc kstat_irqs on node -1
[    0.816122] ahci 0000:00:1f.2: irq 26 for MSI/MSI-X
[    0.816174] ahci: SSS flag set, parallel bus scan disabled
[    0.816220] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    0.816223] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ems 
[    0.816228] ahci 0000:00:1f.2: setting latency timer to 64
[    3.874081] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.874116] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    3.874214] r8169 0000:02:00.0: setting latency timer to 64
[    3.874413] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    3.875028] eth0: RTL8168c/8111c at 0xf8250000, 00:1e:8c:2b:06:8d, XID 3c2000c0 IRQ 27
[    4.064816] usbcore: registered new interface driver usbhid
[   36.515604]  [<f82448a0>] rtl8169_rx_fill+0xa0/0x1c0 [r8169]
[   36.515610]  [<f8245148>] rtl8169_init_ring+0x58/0x90 [r8169]
[   36.515615]  [<f8245dd8>] rtl8169_open+0xc8/0x3c0 [r8169]

---

### Post by chili555 on 2010-10-30
> [ 36.515604] [<f82448a0>] rtl8169_rx_fill+0xa0/0x1c0 [r8169]
[ 36.515610] [<f8245148>] rtl8169_init_ring+0x58/0x90 [r8169]
[ 36.515615] [<f8245dd8>] rtl8169_open+0xc8/0x3c0 [r8169]This is evidently a known bug:

[https://bugzilla.redhat.com/show_bug.cgi?id=566389](https://bugzilla.redhat.com/show_bug.cgi?id=566389)

[https://bugzilla.kernel.org/show_bug.cgi?id=16441](https://bugzilla.kernel.org/show_bug.cgi?id=16441)

This one looks a bit similar:

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg478928.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg478928.html)

Can you get network connectivity back if you restart Network Manager?```
sudo /etc/init.d/network-manager restart
```Or by removing and re-loading the driver?```
sudo rmmod -f r8169
sudo modprobe r8169
```

---

### Post by egkeat on 2010-10-30
> **chili555 said:**
> This is evidently a known bug:

[https://bugzilla.redhat.com/show_bug.cgi?id=566389](https://bugzilla.redhat.com/show_bug.cgi?id=566389)

[https://bugzilla.kernel.org/show_bug.cgi?id=16441](https://bugzilla.kernel.org/show_bug.cgi?id=16441)

This one looks a bit similar:

[http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg478928.html](http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg478928.html)

Can you get network connectivity back if you restart Network Manager?```
sudo /etc/init.d/network-manager restart
```Or by removing and re-loading the driver?```
sudo rmmod -f r8169
sudo modprobe r8169
```


Thank you. Helpful information. I'll try what you said and return. All this is very new to me....trying to be patient but have already lost a full day's work messing around with it. What I'm hoping though is learning as much as I can over time (unlike the last try, gave up too quickly).

---

### Post by egkeat on 2010-10-31
I don't know how this happened. Somehow when I became frustrated and started going through the motions of checking and unchecking the enable box, (after loading and unloading network manager several times) it started working. I've since been able to upgrade to 10.4 from 9.10 and so far still working. Thanks for the help.

---

