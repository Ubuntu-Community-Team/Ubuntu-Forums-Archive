---
title: "Multiple Dvico DVB-T cards"
date: 2010-10-27
forum: Mythbuntu
---

### Post by bawatkins on 2010-10-27
I have three Dvico DVB-T cards that I am installing in mythbuntu 10.10. They are 2 x card type 21 and 1 x card type 64 but only adapter0 is created in /dev. I have done some work in modprobe.d and added a dvb-options.conf file and can now get adapter0 and adapter1 but still don't see the third card. 
 
Any ideas on how to specify all three cards to work via card type or pci address etc?

---

### Post by ian dobson on 2010-10-27
Hi,

Are all cards seen by the system? Just to a lspci and that'll list all cards seen.

Regards
Ian Dobson

---

### Post by bawatkins on 2010-10-30
lspci result
 
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 LE] (rev a2)
05:06.0 Multimedia video controller: Device 0005:0400 (rev f9)
05:06.2 Class 8802: Device 0005:0480 (rev f9)
05:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
05:08.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
05:08.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
05:08.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
 
 
dmesg register
 
[    0.004359] ... generic registers:      4
[    0.088000] EISA bus registered
[    0.088000] ACPI: bus type pci registered
[    0.168947] usbcore: registered new interface driver usbfs
[    0.168960] usbcore: registered new interface driver hub
[    0.168984] usbcore: registered new device driver usb
[    0.178865] ACPI: bus type pnp registered
[    0.183424] ACPI: ACPI bus type pnp unregistered
[    0.220000] TCP reno registered
[    0.260267] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.276422] io scheduler noop registered
[    0.276424] io scheduler deadline registered
[    0.276437] io scheduler cfq registered (default)
[    0.277591] ACPI: acpi_idle registered with cpuidle
[    0.286295] thermal LNXTHERM:01: registered as thermal_zone0
[    0.289969] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[    0.302118] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[    0.616793] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.632555] TCP cubic registered
[    0.633556] registered taskstats version 1
[    1.711353] usbcore: registered new interface driver hiddev
[    1.734196] usbcore: registered new interface driver usbhid
[   12.974495] cx88[0]/0: registered device video0 [v4l2]
[   12.974520] cx88[0]/0: registered device vbi0
[   13.078352] usbcore: registered new interface driver rt2500usb
[   13.537208] cx88[1]/0: registered device video1 [v4l2]
[   13.537296] cx88[1]/0: registered device vbi1
[   13.646603] lirc_dev: IR Remote Control driver registered, major 250 
[   14.146449] usbcore: registered new interface driver rt73usb
[   14.421572] cx88/2: registering cx8802 driver, type: dvb access: shared
[   14.890522] DVB: registering new adapter (cx88[0])
[   14.890528] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...
[  617.695875] usbcore: registered new interface driver usb-storage
[  617.695881] USB Mass Storage support registered.
 
 
log messages dvb
 
Oct 31 11:56:40 htpc kernel: [   12.811331] cx88[0]: subsystem: 18ac:db11, board: DViCO FusionHDTV DVB-T Plus [card=21,autodetected], frontend(s): 1
Oct 31 11:56:40 htpc kernel: [   14.421568] cx88/2: cx2388x dvb driver version 0.0.8 loaded
Oct 31 11:56:40 htpc kernel: [   14.421572] cx88/2: registering cx8802 driver, type: dvb access: shared
Oct 31 11:56:40 htpc kernel: [   14.421576] cx88[0]/2: subsystem: 18ac:db11, board: DViCO FusionHDTV DVB-T Plus [card=21]
Oct 31 11:56:40 htpc kernel: [   14.421579] cx88[0]/2: cx2388x based DVB/ATSC card
Oct 31 11:56:40 htpc kernel: [   14.890522] DVB: registering new adapter (cx88[0])
Oct 31 11:56:40 htpc kernel: [   14.890528] DVB: registering adapter 0 frontend 0 (Zarlink MT352 DVB-T)...

---

### Post by bawatkins on 2010-11-03
anyone have any advice on this one?

---

