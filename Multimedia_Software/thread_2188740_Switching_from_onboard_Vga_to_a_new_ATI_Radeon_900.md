---
title: "Switching from onboard Vga to a new ATI Radeon 9000/256M ddr Pci"
date: 2013-11-18
forum: Multimedia Software
---

### Post by ahears on 2013-11-18
I have bought a new Ati Radeon 9000/256M ddr Pci card for use in my old computer with Ubuntu 12.04.  Ubuntu 12.04 will not boot after I install the new Video card. I get a display with the new ATI up to the Grub loader, then when Plymouth takes over (I have a Super Boot Manager installed just for the graphical display) everything stops. The ATI Linux Wiki says this card is no longer supported but I have downloaded the current linux drivers directly from the ATI website for this exact card for x86 linux. Shouldn't the linux drivers from ATI work? I have read everything I can find on ATI and ubuntu but some of it is  beyond my technical level of understanding and I need some help figuring  out what is wrong, or if I'm simply out of luck.

**I hav run these commands:**
> sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0 dh-modaliases
**and: **
> sudo sh *.run --buildpkg Ubuntu/precise

**Output of *_this_* command is:**
> Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Generating package: Ubuntu/precise
[COLOR=#ff0000]Requested package is not supported.[/COLOR] [QUOTE]I guess this is obvious...
Removing temporary directory: fglrx-install[/QUOTE]

**Output of lspci (without the new ATI card installed):**
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

**and lshw -c display:**
> *-display               
       description: VGA compatible controller
       product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:e8000000-efffffff memory:feb80000-febfffff

> [QUOTE][COLOR=#ff0000]I Guess I'm Out Of Luck![/COLOR][/QUOTE]

---

### Post by Yellow Pasque on 2013-11-19
You can't use those ancient 8.28.x proprietary drivers, so don't even try. The open source drivers should work just fine though. Try booting a liveUSB of Ubuntu 13.10 to rule out configuration issues with your current install.

---

