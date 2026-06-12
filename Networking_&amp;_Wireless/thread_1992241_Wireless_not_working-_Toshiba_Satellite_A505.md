---
title: "Wireless not working- Toshiba Satellite A505"
date: 2012-05-31
forum: Networking &amp; Wireless
---

### Post by cortman on 2012-05-31
So a couple weeks ago I removed my stock Ubuntu 12.04 and installed via the 12.04 minimal CD. I installed xorg, gnome shell, gdm, and a handful of apps. Unfortunately, it appears that my wireless (which has always worked out of the box with previous versions of Ubuntu) no longer works- especially puzzling because I'm pretty sure it worked fine in the stock 12.04.
The laptop is a Toshiba Satellite A505-S6980, which uses a Realtek wireless card, I believe.

Here are some outputs:

```
lspci:
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
03:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller (rev 01)
03:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
```

```
iwconfig:
lo        no wireless extensions.
 
eth0      no wireless extensions.
```

```
sudo lshw -C network:
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:34:01:7d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.0.216 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
```

---

### Post by TBABill on 2012-05-31
I don't see a wireless device listed in your lspci output. Could it be an internal USB device? If so, perhaps lsusb would show it.

---

### Post by cortman on 2012-05-31
> **TBABill said:**
> I don't see a wireless device listed in your lspci output. Could it be an internal USB device? If so, perhaps lsusb would show it.

lsusb returns nothing related to networking.

---

### Post by wildmanne39 on 2012-05-31
Hi, it is possible that you did not build the wireless module into the kernel, but there is one more command to try:
```
sudo pccardctl ident
```
Also post:
```
lsusb
```
so we can look at the ID numbers.

Let us see:
```
lspci -nnk | grep -iA2 net
lsmod
```
You can check in your bios and make sure wireless lan is turned on, some have that option in the bios.
Thanks

---

### Post by cortman on 2012-05-31
> **wildmanne39 said:**
> Hi, it is possible that you did not build the wireless module into the kernel, but there is one more command to try:
```
sudo pccardctl ident
```
Also post:
```
lsusb
```
so we can look at the ID numbers.

Let us see:
```
lspci -nnk | grep -iA2 net
lsmod
```
You can check in your bios and make sure wireless lan is turned on, some have that option in the bios.
Thanks

A reboot (for other purposes) and the wireless is working great.

?????

I guess I'll just grin and count myself lucky. Thanks for the attention, wildmanne39 and TABill.

---

### Post by wildmanne39 on 2012-05-31
Hi Cortman now where was the fun in that? :P

---

### Post by TBABill on 2012-05-31
So a standard Windows fix also fixes Ubuntu every now and again? haha Awesome that it's working again.

---

