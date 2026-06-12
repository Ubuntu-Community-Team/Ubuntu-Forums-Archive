---
title: "wired problem"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by sanhing on 2012-08-15
New Lenovo G480. Nuked Windows 7 and installed 11.04 via CD. 

Everything seems to be hunky dory except Wired/DSL not recognised.

I have spent a lot of time searching forums but if there is a solution my 'terminal' skills have not been able to cope. That said, I just discovered the very excellent "Learning the Shell"  ([http://linuxcommand.org/lc3_lts0020.php](http://linuxcommand.org/lc3_lts0020.php)).

This may be the solution: [http://www.linuxfoundation.org/collaborate/workgroups/networking/alx](http://www.linuxfoundation.org/collaborate/workgroups/networking/alx)

But those instructions are beyond me.

I don't know if this is any help:

------
jem@gromit:~$ lspci -nnk
 

 00:00.0 Host bridge [0600]: Intel Corporation Device [8086:0154] (rev 09)
 

     Subsystem: Lenovo Device [17aa:3977]
 

 00:01.0 PCI bridge [0604]: Intel Corporation Device [8086:0151] (rev 09)
 

     Kernel driver in use: pcieport
 

     Kernel modules: shpchp
 

 00:01.1 PCI bridge [0604]: Intel Corporation Device [8086:0155] (rev 09)
 

     Kernel driver in use: pcieport
 

     Kernel modules: shpchp
 

 00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:0166] (rev 09)
 

     Subsystem: Lenovo Device [17aa:3977]
 

 00:14.0 USB Controller [0c03]: Intel Corporation Device [8086:1e31] (rev 04)
 

     Subsystem: Lenovo Device [17aa:3977]
 

     Kernel driver in use: xhci_hcd
 

     Kernel modules: xhci-hcd
 

 00:16.0 Communication controller [0780]: Intel Corporation Device [8086:1e3a] (rev 04)
 

     Subsystem: Lenovo Device [17aa:3977]
 

 00:1a.0 USB Controller [0c03]: Intel Corporation Device [8086:1e2d] (rev 04)
 

     Subsystem: Lenovo Device [17aa:3977]
 

     Kernel driver in use: ehci_hcd
 

 00:1b.0 Audio device [0403]: Intel Corporation Device [8086:1e20] (rev 04)
 

     Subsystem: Lenovo Device [17aa:3977]
 

     Kernel driver in use: HDA Intel
 

     Kernel modules: snd-hda-intel
 

 00:1c.0 PCI bridge [0604]: Intel Corporation Device [8086:1e10] (rev c4)
 

     Kernel driver in use: pcieport
 

     Kernel modules: shpchp
 

 00:1c.1 PCI bridge [0604]: Intel Corporation Device [8086:1e12] (rev c4)
 

     Kernel driver in use: pcieport
 

     Kernel modules: shpchp
 

 00:1d.0 USB Controller [0c03]: Intel Corporation Device [8086:1e26] (rev 04)
 

     Subsystem: Lenovo Device [17aa:3977]
 

     Kernel driver in use: ehci_hcd
 

 00:1f.0 ISA bridge [0601]: Intel Corporation Device [8086:1e59] (rev 04)
 

     Subsystem: Lenovo Device [17aa:3977]
 

 00:1f.2 SATA controller [0106]: Intel Corporation Device [8086:1e03] (rev 04)
 

     Subsystem: Lenovo Device [17aa:3977]
 

     Kernel driver in use: ahci
 

     Kernel modules: ahci
 

 00:1f.3 SMBus [0c05]: Intel Corporation Device [8086:1e22] (rev 04)
 

     Subsystem: Lenovo Device [17aa:3977]
 

 01:00.0 3D controller [0302]: nVidia Corporation Device [10de:1140] (rev a1)
 

     Subsystem: Lenovo Device [17aa:3901]
 

     Kernel modules: nouveau, nvidiafb
 

 03:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1090] (rev 08)
 

     Subsystem: Lenovo Device [17aa:3979]
 

 04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
 

     Subsystem: Broadcom Corporation Device [14e4:0587]
 

     Kernel driver in use: brcm80211
 

     Kernel modules: brcm80211
  ---

I am posting this from another laptop.

Help! Thanks

---

