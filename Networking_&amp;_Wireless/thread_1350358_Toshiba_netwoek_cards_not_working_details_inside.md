---
title: "Toshiba netwoek cards not working details inside"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by hero1900 on 2009-12-09
[B][COLOR=Red]hi i was installing ubuntu 9.10 on my firend laptop and i got a problem no network card work (wired and wireless) so here is the details if any one can help:[/COLOR]

1 ) Machine Brand and Model (PC/Laptop)[/B]:
```
Toshiba satellite l310 laptop
```
[B]2 ) Wired/Wireless Brand, Model and Wireless Chipset:
[/B]   	 	 	 	 	```
*07:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller [11ab:4355] (rev 12) 



 *08:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
 
```
[B]3 ) check interface:
[/B]```

  	 	 	 	 	ifconfig 	 lo        Link encap:Local Loopback   
        	   inet addr:127.0.0.1  Mask:255.0.0.0  
         	  inet6 addr: ::1/128 Scope:Host  
           	UP LOOPBACK RUNNING  MTU:16436  Metric:1  
          	 RX packets:4 errors:0 dropped:0 overruns:0 frame:0  
           	TX packets:4 errors:0 dropped:0 overruns:0 carrier:0  
           	collisions:0 txqueuelen:0  
           	RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)  
 ------------------------------------

 iwconfig  
 lo        no wireless extensions.  
 

```
[B]4 ) Check for modules:
[/B]```

  	 	 	 	 	 	  Module                  Size  Used by  
 usbhid                 38208  0  
 usb_storage            52544  1  
 binfmt_misc             8356  1  
 ppdev                   6688  0  
 snd_hda_codec_conexant    20060  1  
 snd_hda_intel          26920  2  
 snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel  
 snd_hwdep               7200  1 snd_hda_codec  
 snd_pcm_oss            37920  0  
 snd_mixer_oss          16028  1 snd_pcm_oss  
 snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 snd_seq_dummy           2656  0  
 snd_seq_oss            28576  0  
 snd_seq_midi            6432  0  
 snd_rawmidi            22208  1 snd_seq_midi  
 iptable_filter          3100  0  
 snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi  
 ath5k                 124260  0  
 ip_tables              11692  1 iptable_filter  
 snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 snd_timer              22276  2 snd_pcm,snd_seq  
 snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 mac80211              181236  1 ath5k  
 uvcvideo               59080  0  
 sdhci_pci               7100  0  
 joydev                 10272  0  
 ath                     8060  1 ath5k  
 x_tables               16544  1 ip_tables  
 sdhci                  17472  1 sdhci_pci  
 videodev               36736  1 uvcvideo  
 snd                    59204  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 psmouse                56180  0  
 v4l1_compat            14496  2 uvcvideo,videodev  
 soundcore               7264  1 snd  
 cfg80211               93052  3 ath5k,mac80211,ath  
 serio_raw               5280  0  
 led_class               4096  2 ath5k,sdhci  
 snd_page_alloc          9156  2 snd_hda_intel,snd_pcm  
 lp                      8964  0  
 parport                35340  2 ppdev,lp  
 fbcon                  36640  72  
 tileblit                2460  1 fbcon  
 font                    8124  1 fbcon  
 bitblit                 5372  1 fbcon  
 softcursor              1756  1 bitblit 
 i915                  221064  3  
 drm                   159584  3 i915  
 i2c_algo_bit            5760  1 i915  
 ohci1394               29900  0  
 ieee1394               86596  1 ohci1394  
 sky2                   46560  0  
 video                  19380  1 i915  
 output                  2780  1 video  
 intel_agp              27484  2 i915  
 agpgart                34988  2 drm,intel_agp  
 
```
**5 ) Kernel boot messages**
```

  	 	 	 	 	 	  [    1.625878] io scheduler anticipatory registered  
 [    1.625880] io scheduler deadline registered  
 [    1.625921] io scheduler cfq registered (default)  
 [    1.625933] pci 0000:00:02.0: Boot video device  
 [    1.626215]   alloc irq_desc for 24 on node -1  
 [    1.626218]   alloc kstat_irqs on node -1  
 [    1.626229] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X  
 [    1.626241] pcieport-driver 0000:00:1c.0: setting latency timer to 64  
 [    1.626398]   alloc irq_desc for 25 on node -1  
 [    1.626399]   alloc kstat_irqs on node -1  
 [    1.626408] pcieport-driver 0000:00:1c.4: irq 25 for MSI/MSI-X  
 [    1.626420] pcieport-driver 0000:00:1c.4: setting latency timer to 64  
 [    1.626574]   alloc irq_desc for 26 on node -1  
 [    1.626581]   alloc kstat_irqs on node -1  
 [    1.626590] pcieport-driver 0000:00:1c.5: irq 26 for MSI/MSI-X  
 [    1.626601] pcieport-driver 0000:00:1c.5: setting latency timer to 64  
 [    1.626704] pci_hotplug: PCI Hot Plug PCI Core version: 0.5  
 [    1.626821] pciehp: PCI Express Hot Plug Controller Driver version: 0.4  
 [    1.680108] ACPI: AC Adapter [ACAD] (on-line)  
 [    1.680167] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0  
 [    1.680170] ACPI: Power Button [PWRF]  
 [    1.680229] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1  
 [    1.680232] ACPI: Power Button [PWRB]  
 [    1.680273] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2  
 [    1.680407] ACPI: Lid Switch [LID]  
 [    1.681198] ACPI: SSDT b5f1aca0 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20061109)  
 [    1.681765] ACPI: SSDT b5f19620 00594 (v01  PmRef  Cpu0Cst 00003001 INTL 20061109)  
 [    1.684047] Monitor-Mwait will be used to enter C-1 state  
 [    1.684074] Monitor-Mwait will be used to enter C-2 state  
 [    1.684082] Marking TSC unstable due to TSC halts in idle  
 [    1.684096] ACPI: CPU0 (power states: C1[C1] C2[C2])  
 [    1.684120] processor LNXCPU:00: registered as cooling_device0  
 [    1.684124] ACPI: Processor [CPU0] (supports 8 throttling states)  
 [    1.684567] ACPI: SSDT b5f1aa20 001CF (v01  PmRef    ApIst 00003000 INTL 20061109)  
 [    1.685016] ACPI: SSDT b5f1af20 0008D (v01  PmRef    ApCst 00003000 INTL 20061109)  
 [    1.686080] ACPI: CPU1 (power states: C1[C1] C2[C2])  
 [    1.686104] processor LNXCPU:01: registered as cooling_device1  
 [    1.686108] ACPI: Processor [CPU1] (supports 8 throttling states)  
 [    1.868065] thermal LNXTHERM:01: registered as thermal_zone0  
 [    1.868073] ACPI: Thermal Zone [THRM] (53 C)  
 [    1.868126] isapnp: Scanning for PnP cards...  
 [    1.880089] ACPI: Battery Slot [BAT1] (battery absent)  
 [    2.221985] isapnp: No Plug & Play device found  
 [    2.223144] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled  
 [    2.224400] brd: module loaded  
 [    2.224826] loop: module loaded  
 [    2.224897] input: Macintosh mouse button emulation as /devices/virtual/input/input3  
 [    2.224970] ahci 0000:00:1f.2: version 3.0  
 [    2.224984]   alloc irq_desc for 19 on node -1  
 [    2.224986]   alloc kstat_irqs on node -1  
 [    2.224992] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19  
 [    2.225042]   alloc irq_desc for 27 on node -1  
 [    2.225044]   alloc kstat_irqs on node -1  
 [    2.225053] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X  
 [    2.225135] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode  
 [    2.225139] ahci 0000:00:1f.2: flags: 64bit ncq sntf led clo pio slum part ems  
 [    2.225145] ahci 0000:00:1f.2: setting latency timer to 64  
 [    2.248088] scsi0 : ahci  
 [    2.248191] scsi1 : ahci  
 [    2.248248] scsi2 : ahci  
 [    2.248304] scsi3 : ahci  
 [    2.248358] scsi4 : ahci  
 [    2.248415] scsi5 : ahci  
 [    2.248551] ata1: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04100 irq 27  
 [    2.248555] ata2: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04180 irq 27  
 [    2.248557] ata3: DUMMY  
 [    2.248559] ata4: DUMMY  
 [    2.248561] ata5: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04300 irq 27  
 [    2.248565] ata6: SATA max UDMA/133 abar m2048@0xf4a04000 port 0xf4a04380 irq 27  
 [    2.249501] Fixed MDIO Bus: probed  
 [    2.249535] PPP generic driver version 2.4.2  
 [    2.249636] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver  
 [    2.249657] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19  
 [    2.249674] ehci_hcd 0000:00:1a.7: setting latency timer to 64  
 [    2.249678] ehci_hcd 0000:00:1a.7: EHCI Host Controller  
 [    2.249724] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1  
 [    2.253633] ehci_hcd 0000:00:1a.7: debug port 1  
 [    2.253640] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported  
 [    2.253682] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf4a04800  
 [    2.268017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00  
 [    2.268085] usb usb1: configuration #1 chosen from 1 choice  
 [    2.268113] hub 1-0:1.0: USB hub found  
 [    2.268120] hub 1-0:1.0: 6 ports detected  
 [    2.268183]   alloc irq_desc for 23 on node -1  
 [    2.268186]   alloc kstat_irqs on node -1  
 [    2.268191] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23  
 [    2.268201] ehci_hcd 0000:00:1d.7: setting latency timer to 64  
 [    2.268205] ehci_hcd 0000:00:1d.7: EHCI Host Controller  
 [    2.268235] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2  
 [    2.272156] ehci_hcd 0000:00:1d.7: debug port 1  
 [    2.272163] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported  
 [    2.272176] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf4a04c00  
 [    2.284017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00  
 [    2.284087] usb usb2: configuration #1 chosen from 1 choice  
 [    2.284112] hub 2-0:1.0: USB hub found  
 [    2.284118] hub 2-0:1.0: 6 ports detected  
 [    2.284180] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver  
 [    2.284198] uhci_hcd: USB Universal Host Controller Interface driver  
 [    2.284225] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    2.284232] uhci_hcd 0000:00:1a.0: setting latency timer to 64  
 [    2.284236] uhci_hcd 0000:00:1a.0: UHCI Host Controller  
 [    2.284270] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3  
 [    2.284305] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820  
 [    2.284379] usb usb3: configuration #1 chosen from 1 choice  
 [    2.284404] hub 3-0:1.0: USB hub found  
 [    2.284410] hub 3-0:1.0: 2 ports detected  
 [    2.284456]   alloc irq_desc for 21 on node -1  
 [    2.284458]   alloc kstat_irqs on node -1  
 [    2.284463] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21  
 [    2.284469] uhci_hcd 0000:00:1a.1: setting latency timer to 64  
 [    2.284473] uhci_hcd 0000:00:1a.1: UHCI Host Controller  
 [    2.284501] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4  
 [    2.284535] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840  
 [    2.284612] usb usb4: configuration #1 chosen from 1 choice  
 [    2.284637] hub 4-0:1.0: USB hub found  
 [    2.284643] hub 4-0:1.0: 2 ports detected  
 [    2.284689] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19  
 [    2.284695] uhci_hcd 0000:00:1a.2: setting latency timer to 64  
 [    2.284699] uhci_hcd 0000:00:1a.2: UHCI Host Controller  
 [    2.284727] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5  
 [    2.284753] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860  
 [    2.284827] usb usb5: configuration #1 chosen from 1 choice  
 [    2.284851] hub 5-0:1.0: USB hub found  
 [    2.284857] hub 5-0:1.0: 2 ports detected  
 [    2.284904] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23  
 [    2.284911] uhci_hcd 0000:00:1d.0: setting latency timer to 64  
 [    2.284914] uhci_hcd 0000:00:1d.0: UHCI Host Controller  
 [    2.284945] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6  
 [    2.284972] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880  
 [    2.285059] usb usb6: configuration #1 chosen from 1 choice  
 [    2.285083] hub 6-0:1.0: USB hub found  
 [    2.285092] hub 6-0:1.0: 2 ports detected  
 [    2.285138] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19  
 [    2.285144] uhci_hcd 0000:00:1d.1: setting latency timer to 64  
 [    2.285148] uhci_hcd 0000:00:1d.1: UHCI Host Controller  
 [    2.285176] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7  
 [    2.285203] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0  
 [    2.285280] usb usb7: configuration #1 chosen from 1 choice  
 [    2.285306] hub 7-0:1.0: USB hub found  
 [    2.285312] hub 7-0:1.0: 2 ports detected  
 [    2.285359]   alloc irq_desc for 18 on node -1  
 [    2.285361]   alloc kstat_irqs on node -1  
 [    2.285366] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18  
 [    2.285373] uhci_hcd 0000:00:1d.2: setting latency timer to 64  
 [    2.285376] uhci_hcd 0000:00:1d.2: UHCI Host Controller  
 [    2.285410] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8  
 [    2.285445] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0  
 [    2.285520] usb usb8: configuration #1 chosen from 1 choice  
 [    2.285545] hub 8-0:1.0: USB hub found  
 [    2.285551] hub 8-0:1.0: 2 ports detected  
 [    2.285646] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2A] at 0x60,0x64 irq 1,12  
 [    2.287869] i8042.c: Detected active multiplexing controller, rev 1.1.  
 [    2.289356] serio: i8042 KBD port at 0x60,0x64 irq 1  
 [    2.289362] serio: i8042 AUX0 port at 0x60,0x64 irq 12  
 [    2.289365] serio: i8042 AUX1 port at 0x60,0x64 irq 12  
 [    2.289368] serio: i8042 AUX2 port at 0x60,0x64 irq 12  
 [    2.289371] serio: i8042 AUX3 port at 0x60,0x64 irq 12  
 [    2.289436] mice: PS/2 mouse device common for all mice  
 [    2.289550] rtc_cmos 00:05: RTC can wake from S4  
 [    2.289582] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0  
 [    2.289612] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs  
 [    2.289713] device-mapper: uevent: version 1.0.3  
 [    2.289809] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com  
 [    2.289895] device-mapper: multipath: version 1.1.0 loaded  
 [    2.289898] device-mapper: multipath round-robin: version 1.0.0 loaded  
 [    2.290016] EISA: Probing bus 0 at eisa.0  
 [    2.290023] Cannot allocate resource for EISA slot 1  
 [    2.290026] Cannot allocate resource for EISA slot 2  
 [    2.290051] EISA: Detected 0 cards.  
 [    2.290203] cpuidle: using governor ladder  
 [    2.290293] cpuidle: using governor menu  
 [    2.290775] TCP cubic registered  
 [    2.290923] NET: Registered protocol family 10  
 [    2.291355] lo: Disabled Privacy Extensions  
 [    2.291680] NET: Registered protocol family 17  
 [    2.291697] Bluetooth: L2CAP ver 2.13  
 [    2.291699] Bluetooth: L2CAP socket layer initialized  
 [    2.291702] Bluetooth: SCO (Voice Link) ver 0.6  
 [    2.291703] Bluetooth: SCO socket layer initialized  
 [    2.291743] Bluetooth: RFCOMM TTY layer initialized  
 [    2.291749] Bluetooth: RFCOMM socket layer initialized  
 [    2.291751] Bluetooth: RFCOMM ver 1.11  
 [    2.292390] Using IPI No-Shortcut mode  
 [    2.292452] PM: Resume from disk failed.  
 [    2.292463] registered taskstats version 1  
 [    2.292577]   Magic number: 5:159:405  
 [    2.292667] rtc_cmos 00:05: setting system clock to 2009-12-10 00:24:12 UTC (1260404652)  
 [    2.292670] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found  
 [    2.292672] EDD information not available.  
 [    2.320348] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4  
 [    2.500026] Clocksource tsc unstable (delta = -196623729 ns)  
 [    2.568051] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)  
 [    2.572048] ata5: SATA link down (SStatus 0 SControl 300)  
 [    2.572081] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)  
 [    2.572101] ata6: SATA link down (SStatus 0 SControl 300)  
 [    2.572608] ACPI Warning: \_SB_.PCI0.SAT0.PRT0._GTF: Return type mismatch - found Integer, expected Buffer 20090521 nspredef-940  
 [    2.572616] ata1.00: _GTF unexpected object type 0x1  
 [    2.581134] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L633A, TO01, max UDMA/100, ATAPI AN  
 [    2.595051] ata2.00: configured for UDMA/100  
 [    2.597047] hub 2-0:1.0: unable to enumerate USB device on port 3  
 [    2.634200] ata1.00: ATA-8: TOSHIBA MK2555GSX, FG001M, max UDMA/100  
 [    2.634203] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)  
 [    2.635044] ata1.00: _GTF unexpected object type 0x1  
 [    2.635197] ata1.00: configured for UDMA/100  
 [    2.635315] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK2555GS FG00 PQ: 0 ANSI: 5  
 [    2.635436] sd 0:0:0:0: Attached scsi generic sg0 type 0  
 [    2.635474] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)  
 [    2.635517] sd 0:0:0:0: [sda] Write Protect is off  
 [    2.635520] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00  
 [    2.635542] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA  
 [    2.635658]  sda:  
 [    2.639225] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633A  TO01 PQ: 0 ANSI: 5  
 [    2.649664] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray  
 [    2.649667] Uniform CD-ROM driver Revision: 3.20  
 [    2.649748] sr 1:0:0:0: Attached scsi CD-ROM sr0  
 [    2.649790] sr 1:0:0:0: Attached scsi generic sg1 type 5  
 [    2.687736]  sda1 sda2 sda3 sda4 < 
 [    2.708049] usb 2-4: new high speed USB device using ehci_hcd and address 3  
 [    2.713032]  sda5 sda6 >  
 [    2.732253] sd 0:0:0:0: [sda] Attached SCSI disk  
 [    2.732281] Freeing unused kernel memory: 540k freed  
 [    2.732579] Write protecting the kernel text: 4568k  
 [    2.732631] Write protecting the kernel read-only data: 1836k  
 [    2.840711] Linux agpgart interface v0.103  
 [    2.843475] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset  
 [    2.843937] agpgart-intel 0000:00:00.0: detected 131068K stolen memory  
 [    2.858873] sky2 driver version 1.23 
 [    2.858916] sky2 0000:07:00.0: enabling device (0000 -> 0003)  
 [    2.858925] sky2 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    2.858943] sky2 0000:07:00.0: setting latency timer to 64  
 [    2.858965] sky2 0000:07:00.0: unsupported chip type 0x0  
 [    2.858975] sky2 0000:07:00.0: PCI INT A disabled  
 [    2.858982] sky2: probe of 0000:07:00.0 failed with error -95  
 [    2.862443] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000  
 [    2.894907] usb 2-4: configuration #1 chosen from 1 choice  
 [    2.896597] ohci1394 0000:0a:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    2.950091] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[ff501000-ff5017ff]  Max Packet=[2048]  IR/IT contexts=[8/8]  
 [    2.967384] [drm] Initialized drm 1.1.0 20060810  
 [    2.978326] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [    2.978332] i915 0000:00:02.0: setting latency timer to 64  
 [    2.980317]   alloc irq_desc for 28 on node -1  
 [    2.980320]   alloc kstat_irqs on node -1  
 [    2.980329] i915 0000:00:02.0: irq 28 for MSI/MSI-X  
 [    3.086784] [drm] i2c_init DPDDC-B  
 [    3.099267] [drm] i2c_init DPDDC-D  
 [    3.217677] i2c-adapter i2c-2: unable to read EDID block.  
 [    3.217681] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [    3.551669] [drm] TV-20: set mode NTSC 480i 0  
 [    3.676711] [drm] fb0: inteldrmfb frame buffer device  
 [    3.916141] acpi device:05: registered as cooling_device2  
 [    3.916318] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/input/input5  
 [    3.916351] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)  
 [    3.916377] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0  
 [    3.982675] [drm] LVDS-8: set mode 1280x800 1d  
 [    4.020397] Console: switching to colour frame buffer device 160x50  
 [    4.272185] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001b2400016fa1c6]  
 [    4.321065] PM: Starting manual resume from disk  
 [    4.321069] PM: Resume from partition 8:6  
 [    4.321071] PM: Checking hibernation image.  
 [    4.321183] PM: Resume from disk failed.  
 [    4.340458] EXT4-fs (sda5): barriers enabled  
 [    4.364011] kjournald2 starting: pid 423, dev sda5:8, commit interval 5 seconds  
 [    4.364027] EXT4-fs (sda5): delayed allocation enabled  
 [    4.364030] EXT4-fs: file extents enabled  
 [    4.371347] EXT4-fs: mballoc enabled 
 [    4.371360] EXT4-fs (sda5): mounted filesystem with ordered data mode  
 [    5.090425] type=1505 audit(1260404655.296:2): operation="profile_load" pid=446 name=/usr/share/gdm/guest-session/Xsession  
 [    5.238796] type=1505 audit(1260404655.444:3): operation="profile_load" pid=447 name=/sbin/dhclient3  
 [    5.238851] type=1505 audit(1260404655.444:4): operation="profile_load" pid=447 name=/usr/lib/NetworkManager/nm-dhcp-client.action  
 [    5.238893] type=1505 audit(1260404655.444:5): operation="profile_load" pid=447 name=/usr/lib/connman/scripts/dhclient-script  
 [   14.814949] type=1505 audit(1260404665.020:6): operation="profile_load" pid=448 name=/usr/bin/evince  
 [   14.815483] type=1505 audit(1260404665.020:7): operation="profile_load" pid=448 name=/usr/bin/evince-previewer  
 [   14.815971] type=1505 audit(1260404665.020:8): operation="profile_load" pid=448 name=/usr/bin/evince-thumbnailer  
 [   15.081135] type=1505 audit(1260404665.288:9): operation="profile_load" pid=450 name=/usr/lib/cups/backend/cups-pdf  
 [   15.081262] type=1505 audit(1260404665.288:10): operation="profile_load" pid=450 name=/usr/sbin/cupsd  
 [   15.158856] type=1505 audit(1260404665.363:11): operation="profile_load" pid=451 name=/usr/sbin/tcpdump  
 [   15.927602] Adding 7245272k swap on /dev/sda6.  Priority:-1 extents:1 across:7245272k  
 [   16.058482] udev: starting version 147  
 [   16.129817] EXT4-fs (sda5): internal journal on sda5:8  
 [   16.813675] lp: driver loaded but no devices found  
 [   17.788216] cfg80211: Calling CRDA to update world regulatory domain  
 [   18.325558] input: PS/2 Mouse as /devices/platform/i8042/serio4/input/input6  
 [   18.342883] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio4/input/input7  
 [   18.526771] Linux video capture interface: v2.00  
 [   18.527335] cfg80211: World regulatory domain updated:  
 [   18.527338] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)  
 [   18.527341] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   18.527344] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   18.527347] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)  
 [   18.527349] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   18.527352] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)  
 [   18.576436] sdhci: Secure Digital Host Controller Interface driver  
 [   18.576439] sdhci: Copyright(c) Pierre Ossman  
 [   18.598833] type=1505 audit(1260375868.803:12): operation="profile_replace" pid=826 name=/usr/share/gdm/guest-session/Xsession  
 [   18.750443] sdhci-pci 0000:0a:01.2: SDHCI controller found [1217:7120] (rev 2)  
 [   18.750462] sdhci-pci 0000:0a:01.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16  
 [   18.750490] mmc0: Unknown controller version (2). You may experience problems.  
 [   18.750532] Registered led device: mmc0::  
 [   18.750569] mmc0: SDHCI controller on PCI [0000:0a:01.2] using DMA  
 [   18.751584] type=1505 audit(1260375868.955:13): operation="profile_replace" pid=827 name=/sbin/dhclient3  
 [   18.751721] type=1505 audit(1260375868.955:14): operation="profile_replace" pid=827 name=/usr/lib/NetworkManager/nm-dhcp-client.action  
 [   18.751800] type=1505 audit(1260375868.955:15): operation="profile_replace" pid=827 name=/usr/lib/connman/scripts/dhclient-script  
 [   18.777989] uvcvideo: Found UVC 1.00 device CNF7051 (04f2:b070)  
 [   18.794721] input: CNF7051 as /devices/pci0000:00/0000:00:1d.7/usb2/2-4/2-4:1.0/input/input8  
 [   18.794770] usbcore: registered new interface driver uvcvideo  
 [   18.794774] USB Video Class driver (v0.1.0)  
 [   18.996910] ip_tables: (C) 2000-2006 Netfilter Core Team  
 [   19.022112] ath5k 0000:08:00.0: enabling device (0000 -> 0002)  
 [   19.022124] ath5k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17  
 [   19.022138] ath5k 0000:08:00.0: setting latency timer to 64  
 [   19.022175] ath5k 0000:08:00.0: registered as 'phy0'  
 [   19.024244] ath5k phy0: Couldn't identify radio revision.  
 [   19.024276] ath5k 0000:08:00.0: PCI INT A disabled  
 [   20.696039]   alloc irq_desc for 22 on node -1  
 [   20.696043]   alloc kstat_irqs on node -1  
 [   20.696049] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22  
 [   20.696088] HDA Intel 0000:00:1b.0: setting latency timer to 64  
 [   20.828454] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9  
 [   20.828527] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10  
 [   20.828582] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11  
 [   24.669609] i2c-adapter i2c-2: unable to read EDID block.  
 [   24.669614] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [   24.674041] i2c-adapter i2c-2: unable to read EDID block.  
 [   24.674044] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [   24.719828] [drm] TV-20: set mode NTSC 480i 0  
 [   24.863076] [drm] TV-20: set mode NTSC 480i 0  
 [   25.131262] i2c-adapter i2c-2: unable to read EDID block.  
 [   25.131267] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [   25.136065] i2c-adapter i2c-2: unable to read EDID block.  
 [   25.136068] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [   25.181774] [drm] TV-20: set mode NTSC 480i 0  
 [   25.322806] [drm] TV-20: set mode NTSC 480i 0  
 [   28.469133] type=1505 audit(1260375878.675:16): operation="profile_replace" pid=829 name=/usr/bin/evince  
 [   28.470345] type=1505 audit(1260375878.675:17): operation="profile_replace" pid=829 name=/usr/bin/evince-previewer  
 [   28.471211] type=1505 audit(1260375878.675:18): operation="profile_replace" pid=829 name=/usr/bin/evince-thumbnailer  
 [   28.751247] type=1505 audit(1260375878.955:19): operation="profile_replace" pid=1232 name=/usr/lib/cups/backend/cups-pdf  
 [   28.751456] type=1505 audit(1260375878.955:20): operation="profile_replace" pid=1232 name=/usr/sbin/cupsd  
 [   28.831170] type=1505 audit(1260375879.035:21): operation="profile_replace" pid=1240 name=/usr/sbin/tcpdump  
 [   29.544877] ppdev: user-space parallel port driver  
 [   32.070442] i2c-adapter i2c-2: unable to read EDID block.  
 [   32.070446] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [   32.075124] i2c-adapter i2c-2: unable to read EDID block.  
 [   32.075127] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [   32.120850] [drm] TV-20: set mode NTSC 480i 0  
 [   32.261730] [drm] TV-20: set mode NTSC 480i 0  
 [   32.487717] i2c-adapter i2c-2: unable to read EDID block.  
 [   32.487721] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [   32.492241] i2c-adapter i2c-2: unable to read EDID block.  
 [   32.492244] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [   32.537949] [drm] TV-20: set mode NTSC 480i 0  
 [   32.678901] [drm] TV-20: set mode NTSC 480i 0  
 [   32.903544] i2c-adapter i2c-2: unable to read EDID block.  
 [   32.903548] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [   32.907968] i2c-adapter i2c-2: unable to read EDID block.  
 [   32.907971] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [   32.953682] [drm] TV-20: set mode NTSC 480i 0  
 [   33.093760] [drm] TV-20: set mode NTSC 480i 0  
 [  124.481148] i2c-adapter i2c-2: unable to read EDID block.  
 [  124.481154] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [  124.485585] i2c-adapter i2c-2: unable to read EDID block.  
 [  124.485589] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [  124.531353] [drm] TV-20: set mode NTSC 480i 0  
 [  124.680671] [drm] TV-20: set mode NTSC 480i 0  
 [  124.914510] i2c-adapter i2c-2: unable to read EDID block.  
 [  124.914514] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [  124.918932] i2c-adapter i2c-2: unable to read EDID block.  
 [  124.918935] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [  124.964647] [drm] TV-20: set mode NTSC 480i 0  
 [  125.105103] [drm] TV-20: set mode NTSC 480i 0  
 [  125.339929] i2c-adapter i2c-2: unable to read EDID block.  
 [  125.339933] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [  125.344722] i2c-adapter i2c-2: unable to read EDID block.  
 [  125.344725] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [  125.390439] [drm] TV-20: set mode NTSC 480i 0  
 [  125.530553] [drm] TV-20: set mode NTSC 480i 0  
 [  127.371710] i2c-adapter i2c-2: unable to read EDID block.  
 [  127.371717] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [  127.376765] i2c-adapter i2c-2: unable to read EDID block.  
 [  127.376771] i915 0000:00:02.0: HDMI Type A-1: no EDID data  
 [  127.423038] [drm] TV-20: set mode NTSC 480i 0  
 [  127.563588] [drm] TV-20: set mode NTSC 480i 0  
 [  296.826533] atkbd.c: Unknown key pressed (translated set 2, code 0xf0 on isa0060/serio0).  
 [  296.826539] atkbd.c: Use 'setkeycodes e070 <keycode>' to make it known.  
 [  296.836554] atkbd.c: Unknown key released (translated set 2, code 0xf0 on isa0060/serio0).  
 [  296.836559] atkbd.c: Use 'setkeycodes e070 <keycode>' to make it known.  
 [ 3313.208081] usb 1-1: new high speed USB device using ehci_hcd and address 2  
 [ 3313.342244] usb 1-1: configuration #1 chosen from 1 choice  
 [ 3313.729131] Initializing USB Mass Storage driver...  
 [ 3313.729304] scsi6 : SCSI emulation for USB Mass Storage devices  
 [ 3313.729450] usbcore: registered new interface driver usb-storage  
 [ 3313.729455] USB Mass Storage support registered.  
 [ 3313.729601] usb-storage: device found at 2  
 [ 3313.729604] usb-storage: waiting for device to settle before scanning  
 [ 3318.728442] usb-storage: device scan complete  
 [ 3318.729285] scsi 6:0:0:0: Direct-Access     WDC WD12  WD-WXE907E57357 1A01 PQ: 0 ANSI: 2 CCS  
 [ 3318.729923] sd 6:0:0:0: Attached scsi generic sg2 type 0  
 [ 3318.731378] sd 6:0:0:0: [sdb] 234441648 512-byte logical blocks: (120 GB/111 GiB)  
 [ 3318.732911] sd 6:0:0:0: [sdb] Write Protect is off  
 [ 3318.732917] sd 6:0:0:0: [sdb] Mode Sense: 00 38 00 00  
 [ 3318.732921] sd 6:0:0:0: [sdb] Assuming drive cache: write through  
 [ 3318.737764] sd 6:0:0:0: [sdb] Assuming drive cache: write through  
 [ 3318.737774]  sdb: sdb1 sdb2 < sdb5 >  
 [ 3319.059404] sd 6:0:0:0: [sdb] Assuming drive cache: write through  
 [ 3319.059414] sd 6:0:0:0: [sdb] Attached SCSI disk  
 [ 3327.400092] usb 6-1: new low speed USB device using uhci_hcd and address 2  
 [ 3327.632263] usb 6-1: configuration #1 chosen from 1 choice  
 [ 3327.679021] usbcore: registered new interface driver hiddev  
 [ 3327.694600] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input12  
 [ 3327.694738] generic-usb 0003:046D:C052.0001: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1d.0-1/input0  
 [ 3327.694766] usbcore: registered new interface driver usbhid  
 [ 3327.694770] usbhid: v2.6:USB HID core driver  
 [ 3382.967058] usb 1-1: USB disconnect, address 2  
 [ 3401.736129] usb 6-1: USB disconnect, address 2  
 [ 3452.928078] usb 1-1: new high speed USB device using ehci_hcd and address 3  
 [ 3453.062308] usb 1-1: configuration #1 chosen from 1 choice  
 [ 3453.073512] scsi7 : SCSI emulation for USB Mass Storage devices  
 [ 3453.078658] usb-storage: device found at 3  
 [ 3453.078663] usb-storage: waiting for device to settle before scanning  
 [ 3458.076379] usb-storage: device scan complete  
 [ 3458.077245] scsi 7:0:0:0: Direct-Access     WDC WD12  WD-WXE907E57357 1A01 PQ: 0 ANSI: 2 CCS  
 [ 3458.078275] sd 7:0:0:0: Attached scsi generic sg2 type 0  
 [ 3458.078860] sd 7:0:0:0: [sdc] 234441648 512-byte logical blocks: (120 GB/111 GiB)  
 [ 3458.085274] sd 7:0:0:0: [sdc] Write Protect is off  
 [ 3458.085281] sd 7:0:0:0: [sdc] Mode Sense: 00 38 00 00  
 [ 3458.085285] sd 7:0:0:0: [sdc] Assuming drive cache: write through  
 [ 3458.088431] sd 7:0:0:0: [sdc] Assuming drive cache: write through  
 [ 3458.088441]  sdc: sdc1 sdc2 < sdc5 >  
 [ 3458.419190] sd 7:0:0:0: [sdc] Assuming drive cache: write through  
 [ 3458.419198] sd 7:0:0:0: [sdc] Attached SCSI disk  
 [ 3492.180851] usb 1-1: USB disconnect, address 3  
 [ 3662.808218] usb 1-1: new high speed USB device using ehci_hcd and address 4  
 [ 3662.942306] usb 1-1: configuration #1 chosen from 1 choice  
 [ 3662.943495] scsi8 : SCSI emulation for USB Mass Storage devices  
 [ 3662.943756] usb-storage: device found at 4  
 [ 3662.943760] usb-storage: waiting for device to settle before scanning  
 [ 3667.940387] usb-storage: device scan complete  
 [ 3667.941253] scsi 8:0:0:0: Direct-Access     WDC WD12  WD-WXE907E57357 1A01 PQ: 0 ANSI: 2 CCS  
 [ 3667.942307] sd 8:0:0:0: Attached scsi generic sg2 type 0  
 [ 3667.946804] sd 8:0:0:0: [sdc] 234441648 512-byte logical blocks: (120 GB/111 GiB)  
 [ 3667.948705] sd 8:0:0:0: [sdc] Write Protect is off  
 [ 3667.948712] sd 8:0:0:0: [sdc] Mode Sense: 00 38 00 00  
 [ 3667.948716] sd 8:0:0:0: [sdc] Assuming drive cache: write through  
 [ 3667.951943] sd 8:0:0:0: [sdc] Assuming drive cache: write through  
 [ 3667.951952]  sdc: sdc1 sdc2 < sdc5 >  
 [ 3668.256685] sd 8:0:0:0: [sdc] Assuming drive cache: write through  
 [ 3668.256693] sd 8:0:0:0: [sdc] Attached SCSI disk  
 [ 3676.492056] usb 6-1: new low speed USB device using uhci_hcd and address 3  
 [ 3676.723234] usb 6-1: configuration #1 chosen from 1 choice  
 [ 3676.743533] input: Logitech USB Laser Mouse as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input13  
 [ 3676.743671] generic-usb 0003:046D:C052.0002: input,hidraw0: USB HID v1.10 Mouse [Logitech USB Laser Mouse] on usb-0000:00:1d.0-1/input0  
 [ 3841.624102] INFO: task sync:2543 blocked for more than 120 seconds.  
 [ 3841.624109] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.  
 [ 3841.624113] sync          D c08145c0     0  2543   2540 0x00000000  
 [ 3841.624120]  ee8a7f2c 00000082 f6680000 c08145c0 f593da88 c08145c0 1a98597b 00000356  
 [ 3841.624132]  c08145c0 c08145c0 f593da88 c08145c0 00000000 00000356 c08145c0 f446e540  
 [ 3841.624142]  f593d7f0 ee8a7f60 f593d7f0 f61a723c ee8a7f58 c0570515 fffeffff f61e2000  
 [ 3841.624152] Call Trace:  
 [ 3841.624163]  [<c0570515>] rwsem_down_failed_common+0x75/0x1a0  
 [ 3841.624169]  [<c057068d>] rwsem_down_read_failed+0x1d/0x30  
 [ 3841.624176]  [<c05706e7>] call_rwsem_down_read_failed+0x7/0x10  
 [ 3841.624181]  [<c056fca7>] ? down_read+0x17/0x20  
 [ 3841.624187]  [<c0207385>] sync_filesystems+0xb5/0x100  
 [ 3841.624192]  [<c0207411>] sys_sync+0x11/0x40  
 [ 3841.624197]  [<c010336c>] syscall_call+0x7/0xb  
 [ 3961.624104] INFO: task sync:2543 blocked for more than 120 seconds.  
 [ 3961.624110] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.  
 [ 3961.624114] sync          D c08145c0     0  2543   2540 0x00000000  
 [ 3961.624122]  ee8a7f2c 00000082 f6680000 c08145c0 f593da88 c08145c0 1a98597b 00000356  
 [ 3961.624133]  c08145c0 c08145c0 f593da88 c08145c0 00000000 00000356 c08145c0 f446e540  
 [ 3961.624144]  f593d7f0 ee8a7f60 f593d7f0 f61a723c ee8a7f58 c0570515 fffeffff f61e2000  
 [ 3961.624154] Call Trace:  
 [ 3961.624164]  [<c0570515>] rwsem_down_failed_common+0x75/0x1a0  
 [ 3961.624171]  [<c057068d>] rwsem_down_read_failed+0x1d/0x30  
 [ 3961.624177]  [<c05706e7>] call_rwsem_down_read_failed+0x7/0x10  
 [ 3961.624183]  [<c056fca7>] ? down_read+0x17/0x20  
 [ 3961.624189]  [<c0207385>] sync_filesystems+0xb5/0x100  
 [ 3961.624194]  [<c0207411>] sys_sync+0x11/0x40  
 [ 3961.624199]  [<c010336c>] syscall_call+0x7/0xb  
 [ 4081.624112] INFO: task sync:2543 blocked for more than 120 seconds.  
 [ 4081.624118] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.  
 [ 4081.624122] sync          D c08145c0     0  2543   2540 0x00000000  
 [ 4081.624130]  ee8a7f2c 00000082 f6680000 c08145c0 f593da88 c08145c0 1a98597b 00000356  
 [ 4081.624141]  c08145c0 c08145c0 f593da88 c08145c0 00000000 00000356 c08145c0 f446e540  
 [ 4081.624151]  f593d7f0 ee8a7f60 f593d7f0 f61a723c ee8a7f58 c0570515 fffeffff f61e2000  
 [ 4081.624161] Call Trace:  
 [ 4081.624172]  [<c0570515>] rwsem_down_failed_common+0x75/0x1a0  
 [ 4081.624179]  [<c057068d>] rwsem_down_read_failed+0x1d/0x30  
 [ 4081.624185]  [<c05706e7>] call_rwsem_down_read_failed+0x7/0x10  
 [ 4081.624190]  [<c056fca7>] ? down_read+0x17/0x20  
 [ 4081.624196]  [<c0207385>] sync_filesystems+0xb5/0x100  
 [ 4081.624201]  [<c0207411>] sys_sync+0x11/0x40  
 [ 4081.624207]  [<c010336c>] syscall_call+0x7/0xb  
 
```
[B]6 ) Network configuration
[/B]   	 	 	 	 	```
*-network UNCLAIMED      
        description: Ethernet controller 
        product: 88E8040T PCI-E Fast Ethernet Controller  
        vendor: Marvell Technology Group Ltd.  
        physical id: 0  
        bus info: pci@0000:07:00.0  
        version: 12  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress cap_list  
        configuration: latency=0  
        resources: memory:b6000000-b6003fff ioport:2000(size=256)  
   *-network UNCLAIMED  
        description: Ethernet controller 
        product: AR5001 Wireless Network Adapter  
        vendor: Atheros Communications Inc.  
        physical id: 0  
        bus info: pci@0000:08:00.0  
        version: 01  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress msix cap_list  
        configuration: latency=0  
         resources: memory:b6100000-b610ffff  

```
[B]7 ) Scan for networks:
[/B]   	 	 	 	 	 	   ```
lo        Interface doesn't support scanning.  
```
 
**8 ) Ubuntu Version: **
 	   	 	 	 	 	 	   Description:	Ubuntu 9.10
 
**9 ) Kernel/architecture (including 32 vs. 64 bit): **
 	   	 	 	 	 	 	   ```
2.6.31-14-generic i686
```
 
**10 ) Restarting the network:**
  	 	 	 	 	 	   ```
Reconfiguring network interfaces...                                                               [ OK ]  
```

---

### Post by chili555 on 2009-12-09
I believe this is most of the problem:> [   19.024244] ath5k phy0: Couldn't identify radio revision.  
 [   19.024276] ath5k 0000:08:00.0: PCI INT A disabled  
I am googling and suggest you do so as well. I have not found the answer yet.

---

### Post by hero1900 on 2009-12-09
i dont know this is bad
each time i want to install ubuntu i got these problems is it common these problems or it is just bad luck

---

### Post by hero1900 on 2009-12-10
finally i get it work but not directly
i used the new kernel 2.6.32 and all card work fine now i hope all this issues will be fixed in future since i really like ubuntu and linux and want people to change too

---

