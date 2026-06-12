---
title: "Wireless Disabled"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by biffthemandible on 2009-10-11
My wireless somehow became disabled and I'm not sure how to enable it again. I ran a whole bunch of tests but I don't know what all of it means and what I can do. Here they are:

                                 DISTRIB_ID=Ubuntu  
 DISTRIB_RELEASE=9.04  
 DISTRIB_CODENAME=jaunty  
 DISTRIB_DESCRIPTION="Ubuntu 9.04" 
 

 lo        Interface doesn't support scanning.  
 

 eth1      Interface doesn't support scanning.  
 

 wmaster0  Interface doesn't support scanning.  
 

 wlan0     No scan results  
 

 pan0      Interface doesn't support scanning.  
 

 00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)  
 00:01.0 PCI bridge [0604]: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port [8086:2a41] (rev 07)  
 00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)  
 00:03.0 Communication controller [0780]: Intel Corporation Mobile 4 Series Chipset MEI Controller [8086:2a44] (rev 07)  
 00:03.2 IDE interface [0101]: Intel Corporation Mobile 4 Series Chipset PT IDER Controller [8086:2a46] (rev 07)  
 00:03.3 Serial controller [0700]: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection [8086:2a47] (rev 07)  
 00:19.0 Ethernet controller [0200]: Intel Corporation 82567LM Gigabit Network Connection [8086:10f5] (rev 03)  
 00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)  
 00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)  
 00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)  
 00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)  
 00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)  
 00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)  
 00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)  
 00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)  
 00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)  
 00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)  
 00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)  
 00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)  
 00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)  
 00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)  
 00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M-E LPC Interface Controller [8086:2917] (rev 03)  
 00:1f.2 IDE interface [0101]: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller [8086:2928] (rev 03) 
 00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)  
 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3400 Series [1002:95c4]  
 03:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5300 [8086:4236]  
 15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba)  
 15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04)  
 15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21)  
 15:00.3 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev ff)  
 15:00.4 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 11)  
 15:00.5 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 11)  
 owen@owen-laptop:~$ lspci  
 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)  
 00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)  
 00:03.0 Communication controller: Intel Corporation Mobile 4 Series Chipset MEI Controller (rev 07)  
 00:03.2 IDE interface: Intel Corporation Mobile 4 Series Chipset PT IDER Controller (rev 07)  
 00:03.3 Serial controller: Intel Corporation Mobile 4 Series Chipset AMT SOL Redirection (rev 07)  
 00:19.0 Ethernet controller: Intel Corporation 82567LM Gigabit Network Connection (rev 03)  
 00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)  
 00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)  
 00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)  
 00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)  
 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)  
 00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)  
 00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)  
 00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)  
 00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)  
 00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)  
 00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)  
 00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)  
 00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)  
 00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)  
 00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)  
 00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)  
 01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series  
 03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300  
 15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)  
 15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)  
 15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)  
 15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev ff)  
 15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)  
 15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)
 

 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 002: ID 17ef:1004 Lenovo 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 

   0.000000] found SMP MP-table at [c00f6490] 000f6490  
 [    0.417327] ACPI: EC: EC description table is found, configuring boot EC  
 [    0.465043] ACPI: ACPI Dock Station Driver: 3 docks/bays found  
 [    0.558982] pnp: PnP ACPI: found 10 devices  
 [    1.206793] pcieport-driver 0000:00:01.0: found MSI capability  
 [    1.206931] pcieport-driver 0000:00:1c.0: found MSI capability  
 [    1.207106] pcieport-driver 0000:00:1c.1: found MSI capability  
 [    1.207281] pcieport-driver 0000:00:1c.3: found MSI capability  
 [    1.207456] pcieport-driver 0000:00:1c.4: found MSI capability  
 [    1.661808] isapnp: No Plug & Play device found  
 [    3.216078] hub 1-0:1.0: USB hub found  
 [    3.236070] hub 2-0:1.0: USB hub found  
 [    3.236867] hub 3-0:1.0: USB hub found  
 [    3.237084] hub 4-0:1.0: USB hub found  
 [    3.237856] hub 5-0:1.0: USB hub found  
 [    3.238499] hub 6-0:1.0: USB hub found  
 [    3.238718] hub 7-0:1.0: USB hub found  
 [    3.238937] hub 8-0:1.0: USB hub found  
 [    3.264771] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    3.267231] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    9.033860] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:1004)  
 [    9.679733] iTCO_wdt: Found a ICH9M-E TCO device (Version=2, TCOBASE=0x1060)  
 [    9.699196] ricoh-mmc: Ricoh MMC controller found at 0000:15:00.3 [1180:0843] (rev 11)  
 [    9.767013] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)  
 [    9.895702] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]  
 [    9.900970] thinkpad_acpi: radio switch found; radios are disabled  
 [   10.479209] lp: driver loaded but no devices found  
 [   15.902587] vboxdrv: Found 2 processor cores.  
 

 [    0.424019] ACPI: EC: non-query interrupt received, switching to interrupt mode  
 [    0.536917] Switched to high resolution mode on CPU 1  
 [    0.536919] Switched to high resolution mode on CPU 0  
 [    1.247198] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1  
 [    1.247486] ACPI: Lid Switch [LID]  
 [    9.900970] thinkpad_acpi: radio switch found; radios are disabled  
 [   22.985291] iwlagn: Radio disabled by HW RF Kill switch  
 

 lo        no wireless extensions.  
 

 eth1      no wireless extensions.  
 

 wmaster0  no wireless extensions.  
 

 wlan0     IEEE 802.11abgn  ESSID:""   
           Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
           Tx-Power=15 dBm    
           Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
           Power Management:off  
           Link Quality:0  Signal level:0  Noise level:0  
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0  
 

 pan0      no wireless extensions.  
 

 I'd really appreciate help.

---

### Post by tenmoi on 2009-10-11
wire-connect your machine then:

sudo apt-get install wicd

(this will uninstall network manager,which is getting worse. So dont worry)

then go to applications -> internet -> wicd network manager

hope this'd help.

---

### Post by biffthemandible on 2009-10-11
I installed it but it says there are no wireless networks detected. Does anyone else have an idea as to what I need to do to fix this issue?

---

### Post by t0mppa on 2009-10-11
WICD isn't a miracle cure that will help against any symptoms whatsoever. How about just reading the output from the system and taking action according to it?

> **biffthemandible said:**
> [ 22.985291] iwlagn: Radio disabled by HW RF Kill switch 

In case you're wondering what it means, HW RF Kill switch means the button or key combination (usually Fn + F5) on laptops that switches wireless on and off.

---

### Post by biffthemandible on 2009-10-11
I didn't know about the key combination. Thank you.

---

