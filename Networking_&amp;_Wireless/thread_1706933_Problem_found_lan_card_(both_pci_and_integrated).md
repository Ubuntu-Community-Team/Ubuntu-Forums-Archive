---
title: "Problem found lan card (both pci and integrated)"
date: 2011-03-14
forum: Networking &amp; Wireless
---

### Post by mrdevito on 2011-03-14
Hi guys!

I have an old pc-desktop and I have installed on it an ubuntu server version.

I have on it 2 lan card but no one is founded.

I post here below the result obtained by using the lspci command. Can anyone help me?

```


uname -a: Linux cervelletto 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
lspci -knn: 00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 03)
lspci -knn: 	Subsystem: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30]
lspci -knn: 	Kernel driver in use: agpgart-intel
lspci -knn: 	Kernel modules: intel-agp
lspci -knn: 00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 03)
lspci -knn: 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 12)
lspci -knn: 00:1f.0 ISA bridge [0601]: Intel Corporation 82801BA ISA Bridge (LPC) [8086:2440] (rev 12)
lspci -knn: 00:1f.1 IDE interface [0101]: Intel Corporation 82801BA IDE U100 Controller [8086:244b] (rev 12)
lspci -knn: 	Subsystem: Micro-Star International Co., Ltd. Device [1462:3990]
lspci -knn: 	Kernel driver in use: ata_piix
lspci -knn: 00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 12)
lspci -knn: 	Subsystem: Micro-Star International Co., Ltd. Device [1462:3990]
lspci -knn: 	Kernel driver in use: uhci_hcd
lspci -knn: 00:1f.3 SMBus [0c05]: Intel Corporation 82801BA/BAM SMBus Controller [8086:2443] (rev 12)
lspci -knn: 	Subsystem: Micro-Star International Co., Ltd. Device [1462:3990]
lspci -knn: 00:1f.4 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2444] (rev 12)
lspci -knn: 	Subsystem: Micro-Star International Co., Ltd. Device [1462:3990]
lspci -knn: 	Kernel driver in use: uhci_hcd
lspci -knn: 01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 MX/MX 400] [10de:0110] (rev a1)
lspci -knn: 	Subsystem: ASUSTeK Computer Inc. Device [1043:4019]
lspci -knn: 02:01.0 Non-VGA unclassified device [0000]: Device [0c11:0000] (rev 11)
lspci -knn: 	Subsystem: Allied Telesis, Inc Device [0010:0000]
lspci -knn: 02:02.0 Class [e300]: Device [7010:e300] (rev 10)
lspci -knn: 	Subsystem: Allied Telesis, Inc Device [0010:0000]
lspci -knn: 02:03.0 Class [e300]: Device [6010:e300] (rev 10)
lspci -knn: 	Subsystem: Allied Telesis, Inc Device [0010:0000]
lspci -knn: 02:06.0 Non-VGA unclassified device [0000]: Device [0411:0000] (rev 11)
lspci -knn: 	Subsystem: Allied Telesis, Inc Device [0010:0000]
lspci -knn: 02:07.0 Non-VGA unclassified device [0000]: Device [1c11:0000] (rev 11)
lspci -knn: 	Subsystem: Allied Telesis, Inc Device [0010:0000]
lsmod: Module                  Size  Used by
lsmod: aes_generic            26875  1 
lsmod: hfsplus                71344  0 
lsmod: hfs                    41250  0 
lsmod: xfs                   693150  0 

``` 

Thanks in advance

Denny

---

