---
title: "Issues with Intel integrated video in Maverick"
date: 2010-10-17
forum: Multimedia Software
---

### Post by Telemetron on 2010-10-17
I am fairly new to Ubuntu, so I'm sorry if I don't include any necessary information.
Installed 10.10 rc from CD about 3 days prior to official release and everything was working fine... went about installing software and setting up laptop for use.
About one week later, got prompted for upgrade and went ahead through update manager. Now can't enable desktop effects.  Right after upgrade had a period where title bars of windows would not display... menus were present, but no title bars, no maximize/minimize/close buttons and no dragging windows to new locations on screen :(  That has since resolved itself.
Spent quite awhile searching forums, created xorg.conf at one point, later deleted it.

compiz-check says this:
```
./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]
```lspci says this: 

```
lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LC Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 57)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```Most things still work fine, but I miss the desktop effects, compiz-config-settings-manager doesn't work and the menus in firefox show up blank until I mouse over the entries... more of irritations than anything.  I just want it to work like it did before the upgrade, but not looking forward to starting over again from the cd.  Please help!

---

### Post by julio prada on 2010-12-08
There is a problem with the Ubuntu driver for: "Intel Corporation Core Processor Integrated Graphics Controller (rev 02)" included on my P6100 processor. My problem is that my external monitor flickers.
Can anybody give us a clue of how to solve?

---

