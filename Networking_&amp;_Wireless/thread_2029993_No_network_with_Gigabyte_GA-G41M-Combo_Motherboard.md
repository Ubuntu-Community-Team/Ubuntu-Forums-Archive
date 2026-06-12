---
title: "No network with Gigabyte GA-G41M-Combo Motherboard"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by MatthewJS on 2012-07-20
Hi,

I have PC with Ubuntu 10.04. The motherboard stopped working and I replaced it with a Gigabyte GA-G41M-Combo Socket 775 VGA 6 Channel Audio mATX Motherboard. When I powered up everything else appeared to be fine except that it does not recognise a network connection. No lights appear to come on in the socket with the Ethernet cable in. Of course it might be a faulty board but if it is not and this is something to do with this board and Ubuntu I don't want to send it back and get a replacement to find that I am no better off. Does anyone have any ideas?

Regards


PS: Some details:

> sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: Atheros Communications
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:fdec0000-fdefffff ioport:df00(size=128)

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 4 Series Chipset DRAM Controller [8086:2e30] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation 4 Series Chipset Integrated Graphics Controller [8086:2e32] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
02:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)


---

### Post by lJ9%3MR&gt;sa on 2012-07-20
Do you have Linux Kernel 3.x+? It seems through my research on Google that your card should be supported in a higher Linux kernel revision. I recommend upgrading to Ubuntu 12.04 or installing the kernel yourself. Be cautious when installing kernels. Google can tell you how to install kernels. I will try to search for some more for your ethernet.
 
EDIT:
It seems that you have **Atheros AR8151 onboard ethernet.**
 
EDIT 2:
Try the instructions at the this link. [http://tuxthink.blogspot.com/2010/08/enabling-atheros-ethernet-controller-on.html](http://tuxthink.blogspot.com/2010/08/enabling-atheros-ethernet-controller-on.html)

---

