---
title: "acer aspire v7-582P wirrelless not working"
date: 2013-08-13
forum: Networking &amp; Wireless
---

### Post by NdMrYLH on 2013-08-13
Hi i've installed ubuntu 13.04 on new Acer Aspire v7-582p but its not working and i cant get it to work. 

laufem@laufem-acer:~$ lspci -nn


00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09)
00:03.0 Audio device [0403]: Intel Corporation Device [8086:0a0c] (rev 09)
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 1 [8086:9c10] (rev e4)
00:1c.2 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
04:00.0 Network controller [0280]: Intel Corporation Device [8086:08b1] (rev 63)
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5287] (rev 01)
05:00.1 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 14)


root@laufem-acer:~# lshw -C Network

  *-network UNCLAIMED     
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 63
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:b0500000-b0501fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168 PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.1
       bus info: pci@0000:05:00.1
       logical name: eth0
       version: 14
       serial: 08:9e:01:b9:ae:d6
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.103 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:61 ioport:3000(size=256) memory:b0404000-b0404fff memory:b0400000-b0403fff

---

### Post by varunendra on 2013-08-13
> **NdMrYLH said:**
> 
04:00.0 Network controller [0280]: Intel Corporation Device [**8086:08b1**] (rev 63)

Your wireless card is very new and support for it is not available in the default kernel for 13.04.

As per [wikidevi.com]("http://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_7260_(7260HMW)"), the iwlwifi driver in kernel 3.11+ seems to have support  for it.

Accordingly, you may try downloading and installing kernel 3.11 from the kernel ppa mainline : [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
...but be aware that manually jumping to a much newer kernel than the default one has the potential to break the system or certain functionalities in it. So install it at your own risk.

---

### Post by NdMrYLH on 2013-08-13
Thank you for advice i downloaded and installed new kernel 

uname -r
3.11.0-999-generic


but still not working

---

### Post by varunendra on 2013-08-13
Please post the output of-
```
modinfo iwlwifi
```

---

### Post by NdMrYLH on 2013-08-13
Okej i solved it. For others :

First u need to install new kernel at least 3.11 and You need to have iwlwifi

Then download uccode file with 7062 wifi : for example from this page [http://anonscm.debian.org/viewvc/kernel/dists/trunk/firmware-nonfree/iwlwifi/](http://anonscm.debian.org/viewvc/kernel/dists/trunk/firmware-nonfree/iwlwifi/)

thne copy this file to  /lib/firmware and run these commands 

sudo modprobe -r iwlwifi 
sudo modprobe -v  iwlwifi  

reboot 

This works for me

---

### Post by varunendra on 2013-08-13
Wonderful !
The iwlwifi module should already be a part of the kernel itself, so it must have been only the firmware that was amiss. Thanks for the tip and confirmation. :)

---

### Post by michaelhinespot.com on 2013-10-12
This worked for me too!

To clarify for anyone else who also has the same acer laptop or wifi card:

You need to download this firmware: [http://anonscm.debian.org/viewvc/kernel/dists/trunk/firmware-nonfree/iwlwifi/iwlwifi-7260-7.ucode-22.0.7.0?view=log](http://anonscm.debian.org/viewvc/kernel/dists/trunk/firmware-nonfree/iwlwifi/iwlwifi-7260-7.ucode-22.0.7.0?view=log)

and delete the version "22.0.7.0" off the end of the filename and *then* save it to /lib/firmware and reload the kernel module as the thread suggests.

If you get it wrong you will see an error at the end of $ dmesg that says it is trying to load the firmware but could not find it.

Then once you do that, install a new 3.11 kernel using these instructions:

[http://ubuntuhandbook.org/index.php/2013/10/linux-kernel-3-11-4-released-upgrade-in-ubuntu/](http://ubuntuhandbook.org/index.php/2013/10/linux-kernel-3-11-4-released-upgrade-in-ubuntu/)

..... then you're good to go.

Thanks for the help everybody!

---

### Post by Tyler_Aschenbrenner on 2013-10-14
CONFIRMED

Thank you so much!

I have been trying to fix this on my Acer Aspire M5-583P for over a week.

---

