---
title: "Installing patched wireless drivers problem"
date: 2012-03-24
forum: Networking &amp; Wireless
---

### Post by arielnmz on 2012-03-24
Okay, I've downloaded the latest "compat-wireless-2.6" source, and compiled it without any problems, but, when I get to the "make install" part, it doesn't seem to do anything, I mean, it just throws this:

> make -C /lib/modules/3.0.0-16-generic/build M=/home/ariel/compat/compat-wireless-2012-03-18 modules
make[1]: se ingresa al directorio «/usr/src/linux-headers-3.0.0-16-generic»

And remains the same for HOURS... it  doesn't continue or anything...

By the way, I applied the "-1 channel fix" patches..

I'm currently using Ubuntu 11.10 on Linux 3.0.0-16-generic...

I hope you can help me guys.. thanks!!

> EDIT: I've solved it, this is what happened:
As I was looking into the makefile, I found that the "make install" instruction actually does this: "make uninstall make install-modules make install-scripts" all at once, so I tried to execute each one individually... first the "make uninstall" then the "make install-modules" and that was where the installation "freezed", okay, I pressed Ctrl+C to cancel and continued with make "install-scripts" and everything went fine with that last "make", so I tried "make install" again and it now worked!!...

So, if anyone someday comes across the same problem (make install doesn't work) just run this: "make uninstall && make install-scripts && make install"

---

### Post by Bucky Ball on 2012-03-24
Welcome.

Did you:

```
*sudo* make install
```?

I have the compat wireless 2.6 already in my repositories without having to compile from source ...

I presume you are having problems with wireless. Have you tried plugging in a cable, getting online, getting updates then checking Additional Drivers? (or Hardware Drivers). If not, you should try it before going much further attempting to install manually. Could you please run this command and post back the result:

```
sudo lshw -C network
```

---

### Post by arielnmz on 2012-03-24
Okay, this is the output of the command you mention:

>  *-network               
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:22:68:99:c2:a5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.0.0-16-generic firmware=N/A ip=192.168.1.110 latency=0 link=yes multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:71300000-7130ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:8d:02:68
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:16 ioport:1000(size=256) memory:71200000-712000ff

The thing is, that I need to do this (patch the dirvers, then compile from source and install) in order to fix the negative one (-1) channel bug of the aircrack-ng suite... Which I've done several times with other linux kernels, but it seems that this one is having problems with that...

> EDIT: I've solved it, this is what happened:
As I was looking into the makefile, I found that the "make install" instruction actually does this: "make uninstall make install-modules make install-scripts" all at once, so I tried to execute each one individually... first the "make uninstall" then the "make install-modules" and that was where the installation "freezed", okay, I pressed Ctrl+C to cancel and continued with make "install-scripts" and everything went fine then with that last "make", so I tried "make install" again and it now worked!!...

So, if anyone someday comes across the same problem (make install doesn't work) just run this: "make uninstall && make install-scripts && make install"

---

