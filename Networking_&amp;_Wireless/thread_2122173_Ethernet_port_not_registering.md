---
title: "Ethernet port not registering"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by ShadowVegan on 2013-03-04
I just got a new laptop. The ethernet port worked in Windows before I installed Ubuntu (no longer have Windows installed) but it's not working in Ubuntu. ifconfig returns nothing for ethernet, only lo and usb0 (I'm connected to Internet via USB tether to my phone). lspci -v returns the following:

03:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device 14c7
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f7c00000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at e000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [c0] MSI: Enable- Count=1/16 Maskable+ 64bit+
    Capabilities: [d8] MSI-X: Enable- Count=16 Masked-
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number ff-93-03-a3-08-60-6e-ff


My modem is on and connection to my computer and I tried two ethernet cables. I'm thinking it might be an issue in the BIOS but I couldn't find anything to enable ethernet when I looked around the BIOS. Or perhaps I need an update, because that was the solution to someone else's [similar problem]("http://www.dslreports.com/forum/r26923454-ethernet-port-not-working-on-Ubuntu-11.10"). (They had to download and install driver r8168-8.028.00)

Thanks!

---

### Post by chili555 on 2013-03-04
We need just a bit more information before we can propose a solution:```
lspci -nn
uname -r
```Thanks.

---

### Post by ShadowVegan on 2013-03-04
```
administrator@X55A:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Ivy Bridge DRAM Controller [8086:0154] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Ivy Bridge Graphics Controller [8086:0156] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Panther Point USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Panther Point MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Panther Point High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.1 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 2 [8086:1e12] (rev c4)
00:1c.3 PCI bridge [0604]: Intel Corporation Panther Point PCI Express Root Port 4 [8086:1e16] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation Panther Point USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Panther Point LPC Controller [8086:1e5e] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Panther Point SMBus Controller [8086:1e22] (rev 04)
02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
```


```
administrator@X55A:~$ uname -r
3.5.0-23-generic
```

Thanks.

---

### Post by chili555 on 2013-03-04
The driver for your relatively new device is called *alx*. It is included by default in kernel version 3.5.0-25 but not in -23 which you are using. I believe it's as easy as downloading and installing the latest linux-image on a USB stick or similar, dropping it on your desktop and installing it. After a reboot, you should be all set. Please get the latest linux-image here. [http://packages.ubuntu.com/quantal/linux-image-3.5.0-25-generic](http://packages.ubuntu.com/quantal/linux-image-3.5.0-25-generic)

Be sure to get either the 32- or 64-bit package as appropriate; find which you need with:```
arch
```If it returns i686, then you need 32-bit, known on the download page as i386 (yeah, I know!)

Drag and drop it on your desktop. Install from the terminal with:```
sudo dpkg -i Desktop/linux-image*.deb
```Reboot and let us hear your report.

---

### Post by SoCalChris on 2013-03-04
I'm having the same issue, but with a desktop. Gigabyte H77M-DH3 motherboard.

I'm using kernel 3.5.0-25-generic.

lspci-nn output is
```

00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller [8086:0150] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller [8086:0152] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
00:1c.4 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 [8086:1e18] (rev c4)
00:1c.6 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c4)
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation H77 Express Chipset LPC Controller [8086:1e4a] (rev 04)
00:1f.2 RAID bus controller [0104]: Intel Corporation 82801 SATA Controller [RAID mode] [8086:2822] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
**02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)**
03:00.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 41)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)

```

I've tried manually loading the alx driver using modprobe. I get no errors. I've also compiled the drivers myself, using [these directions]("http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller"). The Realtek controller that's listed is a PCI adapter that I put in while trying to get the AR8161 to work.

Also, **sudo lshw -class network** returns the following. Why would the network be showing as disabled?
```

  *-network **DISABLED**
       description: Ethernet interface
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: p4p1
       version: 10
       serial: 90:2b:34:9b:dc:a0
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx duplex=full firmware=alx latency=0 link=no multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:44 memory:f7d00000-f7d3ffff ioport:e000(size=128)
  *-network
       description: Ethernet interface
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: p6p1
       version: 10
       serial: 00:14:d1:20:7a:9c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.127 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=1Gbit/s
       resources: irq:18 ioport:d000(size=256) memory:f7c20000-f7c200ff memory:f7c00000-f7c1ffff

```

---

### Post by chili555 on 2013-03-04
> **SoCalChris said:**
> I'm having the same issue, but with a desktop. Gigabyte H77M-DH3 motherboard.

I'm using kernel 3.5.0-25-generic.

I've tried manually loading the alx driver using modprobe. I get no errors.What does this tell us?```
ifconfig
lsmod | grep alx
dmesg | grep -e eth0 -e alx
```Thanks.> I've also compiled the drivers myself, using these directions. Obsolete as of 3.5.0-25.

---

### Post by SoCalChris on 2013-03-04
ifconfig (p6p1 is the Realtek card, I'm not sure why it named it that)
```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.4 KB)  TX bytes:1424 (1.4 KB)

p6p1      Link encap:Ethernet  HWaddr 00:14:d1:20:7a:9c  
          inet addr:10.0.0.127  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::214:d1ff:fe20:7a9c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:97288 (97.2 KB)  TX bytes:243910 (243.9 KB)
```

lsmod | grep alx
```
alx                    81293  0 
compat                 13228  1 alx
```

dmesg | grep -e eth0 -e alx
```
[    0.944825] r8169 0000:04:00.0: eth0: RTL8169sb/8110sb at 0xffffc90000656000, 00:14:d1:20:7a:9c, XID 10000000 IRQ 18
[    0.944828] r8169 0000:04:00.0: eth0: jumbo features [frames: 7152 bytes, tx checksumming: ok]
[    6.585385] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    7.106382] alx 0000:02:00.0: DMA to 64-BIT addresses
[    7.106433] alx 0000:02:00.0: (unregistered net_device): HW Flags = 0x415
[    7.106842] alx 0000:02:00.0: (unregistered net_device): reset PHY, pws = 1, az = 0, ptp = 0
[    7.108015] alx 0000:02:00.0: (unregistered net_device): speed = 0x2f, autoneg = 1
[    7.109053] alx 0000:02:00.0: irq 44 for MSI/MSI-X
[    7.109279] alx: Atheros Gigabit Network Connection
```

---

### Post by chili555 on 2013-03-04
> p6p1      Link encap:Ethernet  HWaddr 00:14:d1:20:7a:9c  
          inet addr:10.0.0.127  Bcast:10.255.255.255  Mask:255.0.0.0Very interesting. As well, I see you have two ethernet devices, one driven by r8169 and the other by alx. The r8169 device, p6p1??, evidently has an IP address. Is an ethernet cable attached to the Atheros? What on earth are you trying to accomplish? 

Did the motherboard come with an Atheros and a Realtek or is one an add-on? 

It looks like alx loaded during boot without drama.

Yikes.

---

### Post by SoCalChris on 2013-03-04
The motherboard has the Atheros chip built in, the Realtek was swiped out of my daughter's computer so that I could download the driver source and work on it remotely over SSH. My ultimate goal is to remove the Realtek card, and just use the Atheros that is built into the motherboard. The Realtek card does have an IP, and is working fine. There is a cable connected to the Atheros as well, and the activity lights are showing activity (They aren't on solid, and aren't blinking in a pattern).

Any other suggestions? Do you think reinstalling from scratch would be worth a try? I haven't done much at all with this system yet, so I wouldn't be losing much.

Thanks for your time, I appreciate it

---

### Post by ShadowVegan on 2013-03-04
I tried your suggestion and it didn't work, and now the USB ports won't work either. They will register USB drives, and my mouse will light up, and my phone will register being connected when I plug it into my computer. However, my mouse doesn't work, and I can't tether my phone to my laptop for internet (so now I can't use the internet at all on that computer). How can I at least get the USB ports working again? Thanks.

---

### Post by chili555 on 2013-03-04
My suggestion? Installing the -25 kernel? I thought alx was working; or was that the compiled version? Did the install go without error or warning? Any clues in dmesg?```
dmesg | grep -i -e warn -e error
```> Do you think reinstalling from scratch would be worth a try? Why??

Network Manager is not designed to manage two competing ethernet connections. I'd detach the ethernet from the Realtek, attach one to the Atheros and reboot.

---

### Post by SoCalChris on 2013-03-04
Ok, I got mine working, here's what I did.

Detaching and removing the Realtek didn't work on it's own. After I removed it, running ifconfig just showed the lo device. Running ifconfig -a showed the Atheros device named p4p1 and disabled. I edited /etc/network/interfaces, which still had the Realtek interface named p6p1 listed. I changed p6p1 to p4p1, rebooted, and all works perfectly now. I'm not sure why it named the interfaces like that, but it works.

Thanks again for your help, hopefully what worked for me will also help the other guy having issues with this chipset.

---

### Post by ShadowVegan on 2013-03-04
I decided to just reinstall Ubuntu to get the USB ports working and get back to where I was. Any other suggestions on getting the Ethernet port to work would be nice, but if I don't get it working it's not that big of a deal because this is mainly a travel laptop, so I'll generally be tethering my phone to it for Internet (via USB), or using wireless networks. It'd still be nice to have Ethernet working just in case I ever want it though. Thanks for trying at least.

And yes my installation went without errors/warnings, but I'm not sure what all was and was not working, I'm pretty new to Ubuntu. Been using it for maybe 2 years but still not that familiar with the 'behind the scenes' stuff.

---

### Post by chili555 on 2013-03-05
> **ShadowVegan said:**
> I decided to just reinstall Ubuntu to get the USB ports working and get back to where I was. Any other suggestions on getting the Ethernet port to work would be nice, but if I don't get it working it's not that big of a deal because this is mainly a travel laptop, so I'll generally be tethering my phone to it for Internet (via USB), or using wireless networks. It'd still be nice to have Ethernet working just in case I ever want it though. Thanks for trying at least.

And yes my installation went without errors/warnings, but I'm not sure what all was and was not working, I'm pretty new to Ubuntu. Been using it for maybe 2 years but still not that familiar with the 'behind the scenes' stuff.I firmly believe the best and easiest approach is linux-image as above.

---

