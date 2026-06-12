---
title: "Enable onboard lan to connect to net"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by ismoke101 on 2009-07-30
hi, i have a p4v800d-x motherboard and would like to ask if u know how to use my on board lan. im using this lan here in windows ever since i change my lan's ip im now able to use it, any help on how i can use it in linux ubuntu 8.4?if i "ifconfig" it only show the lo
and if i ifconfig eth0 or eth1 or eth2 it dosnt work

```
chico@chico-desktop:~$ sudo lshw -C Network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:c0:26:70:1e:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.57 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       version: 78
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=8 mingnt=3
chico@chico-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:26:70:1e:02  
          inet addr:192.168.0.57  Bcast:192.168.5.255  Mask:255.255.254.0
          inet6 addr: fe80::2c0:26ff:fe70:1e02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:712 errors:0 dropped:0 overruns:0 frame:0
          TX packets:311 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:77128 (75.3 KB)  TX bytes:66590 (65.0 KB)
          Interrupt:17 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46800 (45.7 KB)  TX bytes:46800 (45.7 KB)

chico@chico-desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:c0:26:70:1e:02  
          inet addr:192.168.0.57  Bcast:192.168.5.255  Mask:255.255.254.0
          inet6 addr: fe80::2c0:26ff:fe70:1e02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:728 errors:0 dropped:0 overruns:0 frame:0
          TX packets:314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78328 (76.4 KB)  TX bytes:66822 (65.2 KB)
          Interrupt:17 Base address:0xd800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:936 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46800 (45.7 KB)  TX bytes:46800 (45.7 KB)

chico@chico-desktop:~$ sudo lspci -nn | grep -i realtek
00:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
chico@chico-desktop:~$ dmesg | grep -e via -e eth0
[   40.540107] eth0: RealTek RTL8139 at 0xd800, 00:c0:26:70:1e:02, IRQ 17
[   40.540111] eth0:  Identified 8139 chip type 'RTL-8139C'
[   40.711215] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   40.713830] via-rhine: probe of 0000:00:12.0 failed with error -5
[   40.723207] pata_via 0000:00:0f.1: version 0.3.3
[   40.734562] scsi0 : pata_via
[   40.745130] scsi1 : pata_via
[   41.909340] sata_via 0000:00:0f.0: version 2.3
[   41.909429] sata_via 0000:00:0f.0: routed to hard irq line 10
[   41.911621] scsi2 : sata_via
[   41.912510] scsi3 : sata_via
[   55.699397] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   55.707318] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   55.715286] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   55.723222] ALSA /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/sound/alsa-driver/pci/via82xx.c:581: codec_read: codec 0 is not valid [0xfe0000]
[   78.827231] eth0: link down
[  105.851679] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  257.817314] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  257.817702] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  258.026383] eth0: link down
[  260.330052] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  260.330452] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  277.589386] eth0: no IPv6 routers present
[  359.580700] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  379.073798] eth0: no IPv6 routers present
[  507.389461] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[  523.748426] eth0: no IPv6 routers present
chico@chico-desktop:~$ 

``` 
i remove my realtek card coz im keep on hanging on windows,. help please

---

### Post by ismoke101 on 2009-07-30
help:confused:

---

### Post by ismoke101 on 2009-07-30
:confused:

---

### Post by martinbaselier on 2009-07-30
Is this the output after you removed the realtek card ? 

It shows there is no kernel module loaded for the onboard lan. 

**sudo modprobe via-rhine**
should load it.

After you've done so, please paste the output of:

sudo lspci -s 00:12.0 -v

and

ifconfig

---

### Post by ismoke101 on 2009-07-30
**martinbaselier**
thanks for the respond on this problem, here's the data you ask, 
```
chico@chico-desktop:~$ sudo modprobe via-rhine
chico@chico-desktop:~$ sudo lspci -s 00:12.0 -v
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
        Subsystem: ASUSTeK Computer Inc. Unknown device 80ed
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at b800 [size=256]
        Memory at fbefb800 (32-bit, non-prefetchable) [size=256]
        Capabilities: [40] Power Management version 2

chico@chico-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44300 (43.2 KB)  TX bytes:44300 (43.2 KB)

chico@chico-desktop:~$ 
```

---

### Post by martinbaselier on 2009-07-30
It seems your card is not recognized by the kernel module. 

Please post the output of:
lspci -s 00:12.0 -x

---

### Post by ismoke101 on 2009-07-30
here it is:

```
chico@chico-desktop:~$ lspci -s 00:12.0 -x
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00: 06 11 65 30 17 01 10 02 78 00 00 02 08 40 00 00
10: 01 b8 00 00 00 b8 ef fb 00 00 00 00 00 00 00 00
20: 00 00 00 00 00 00 00 00 00 00 00 00 43 10 ed 80
30: 00 00 00 00 40 00 00 00 00 00 00 00 05 01 03 08

chico@chico-desktop:~$ 
```

should download a driver for this?

---

### Post by martinbaselier on 2009-07-30
You already have a driver, it's the via-rhine.

**modinfo via-rhine | grep alias**
alias:          pci:v00001106d00003053sv*sd*bc*sc*i*
alias:          pci:v00001106d00003106sv*sd*bc*sc*i*
alias:          pci:v0000**1106**d0000**3065**sv*sd*bc*sc*i*
alias:          pci:v00001106d00003043sv*sd*bc*sc*i*

On the third line it shows the id of your card. Something must be going wrong when loading the kernel module. (that is the driver)

What does
**dmesg | grep via-rhine**
show?

---

### Post by ismoke101 on 2009-07-30
just an additional: before i use this lan, its mac add is different, accord. to the asus forum i should use a diiferent mac, and i used my old realtek mac. i change it thru the registry here in windows. il post the dmesg | grep via-rhine

---

### Post by ismoke101 on 2009-07-30
```
chico@chico-desktop:~$ dmesg | grep via-rhine
[   43.527431] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[   45.193854] via-rhine: probe of 0000:00:12.0 failed with error -5
chico@chico-desktop:~$ 
```

---

### Post by martinbaselier on 2009-07-30
In the windows registry you can not change the hardware address of the NIC, only the mac -address as it appears to the router under windows. 

It seems there is a problem with your card in the current kernel.

Try this one:
[http://packages.ubuntu.com/intrepid/any/linux-image-2.6.27-9-generic](http://packages.ubuntu.com/intrepid/any/linux-image-2.6.27-9-generic)

Install it, check if it works (press esc when booting to enter the grub boot menu) select 2.6.27-9. If it works fine, change the default in /boot/grub/menu.lst.

sudo gedit /boot/grub/menu.lst
Search for default and change the number.

---

### Post by ismoke101 on 2009-07-30
doesnt work. ifconfig stil stay the same, except this

```
chico@chico-desktop:~$ dmesg | grep via-rhine
[    4.652352] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    6.373451] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    6.373533] via-rhine: probe of 0000:00:12.0 failed with error -5
chico@chico-desktop:~$ 
```

---

### Post by ismoke101 on 2009-07-30
i follwd a thread [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/267779")and do this 

Create file /etc/pm/config.d/local with content:

SUSPEND_MODULES="via_rhine"

and try suspend/resume.

---

### Post by ismoke101 on 2009-07-30
:confused::confused:

---

### Post by ismoke101 on 2009-08-01
:(

---

### Post by ismoke101 on 2009-08-04
help please

---

### Post by P4man on 2009-08-06
edit (see next post)

---

### Post by P4man on 2009-08-06
scratch the above. have a look here:

[http://lkml.indiana.edu/hypermail/linux/kernel/0407.1/0937.html](http://lkml.indiana.edu/hypermail/linux/kernel/0407.1/0937.html)

> > I get the following from the kernels that break:
> > Invalid MAC address for card #0
> > via-rhine: probe of 0000:00:09.0 failed with error -5

Seems the -5 error is indeed related to an invalid MAC address that you tried changing on windows. Can you reset it somehow?

---

