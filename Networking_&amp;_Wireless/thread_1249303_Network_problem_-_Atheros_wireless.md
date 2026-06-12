---
title: "Network problem - Atheros wireless"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by lover_of_sc on 2009-08-25
Hi guys,

I am really struggling, cant understand how to get my Sony vaio w series laptop to work with 32-bits ubuntu. I have already posted the problem in the beginner sections but I though that I may have more luck here. See reference tread: [http://ubuntuforums.org/showthread.php?t=1249187](http://ubuntuforums.org/showthread.php?t=1249187)

I have contacted SONY and they have sent me a XP driver for the network card but it's in a CAB file and not a INF file (that I thought could be used with the application 'windows wieless drivers' but I have not been able to do that.

Other Hopefully Somewhat Usefull Info:

anders@anders-laptop:~$ cat /proc/versions_signature
cat: /proc/versions_signature: No such file or directory
anders@anders-laptop:~$ cat /proc/version_signature
Ubuntu 2.6.28-15.49-generic
anders@anders-laptop:~$ 
anders@anders-laptop:~$ lspci -k
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
	Kernel modules: intelfb
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Kernel modules: iTCO_wdt, intel-rng
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
	Kernel driver in use: ata_piix
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Kernel modules: i2c-i801
02:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
0a:09.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci
0a:09.1 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
anders@anders-laptop:~$ 
anders@anders-laptop:~$ iwconfig
lo        no wireless extensions.

pan0      no wireless extensions.

anders@anders-laptop:~$ 
anders@anders-laptop:~$

---

### Post by lover_of_sc on 2009-08-25
Intresting progress!! I re-installed Ubuntu 9.04 then downloaded the linux backports modules 2.6.28-11.11 and installed the deb package. This actually got the network going again even after a couple of restarts!! :0)

Now the difficult part, I did a full system update with the update manager, installed about 185 updates. I then restarted the system and the network was unavailable again!! Tried to reinstall the same package again but that did not help. What update can cause this and how do I avoid it going forward?

Do I need to reinstall ubuntu again or can someone help me to get it sorted??

All the best /one step closer (Anders)

---

