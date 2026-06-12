---
title: "A little help Ubuntu-LAMP"
date: 2008-10-28
forum: Michigan Team - US
---

### Post by adman4054 on 2008-10-28
I'm a web/software developer located in Oakland County Michigan. I have a Windoze server at a datacenter in Troy and I'm adding another one, but this time I want it to run Ubuntu as a LAMP server. I need some help with setup and troubleshooting before I deploy it. I'm looking for some phone time with somebody with some Ubuntu and LAMP expierence. I can pay or trade. Thanks

---

### Post by scragar on 2008-10-28
I have plenty of lamp and ubuntu experience, but I live in the UK, so talking over the phone may be hard, till I get skype working on Ibex you can always email me or PM me here if you don't want to talk publicly about a problem for some reason(although honestly that will give you a better over all response).

---

### Post by adman4054 on 2008-10-28
> **scragar said:**
> I have plenty of lamp and ubuntu experience, but I live in the UK, so talking over the phone may be hard, till I get skype working on Ibex you can always email me or PM me here if you don't want to talk publicly about a problem for some reason(although honestly that will give you a better over all response).

Thanks for the reply Scragar. I dont have a problem with discussing it here, the issues seem to be so basic in nature that I dont really want to impose, but here goes. I bought a used server that had windoze 2003 enterprise. I installed ubuntu 8.04 desktop (because of the gui)and then installed Apache, PHP and MYSQL. A couple of times the machine has locked up. Each time it locked up I was doing something, ie., downloading, browsing, etc. I ran Windows Diagnostic for 5 hours with no hardware errors. I looked at what logs I could find (my lack of Linux expierence, I might not have been looking in the right place)and couldnt find any error messages. The data center where this box will be hung is about 40 miles from my office and multiple trips and unreliabilty cant happen. 
Is there something I can check to nail down the problem? Should I have done something different with the install of Ubuntu? I just installed it over Windoze and re-partitioned the drive.
Any help would be appreciated.

---

### Post by scragar on 2008-10-28
A better explination of locked up would be nice, but if it has locked up normaly dmesg will have something to say. so if you managed to recover from the lock up run:
```
dmesg | less
```
or otherwise you can find it in the logs directory(**/var/log**), only the latest 2 versions(current and last) are in text format, the remainder are put in tarballs to save space. If you could post the last few lines here([noparse]in ```
OUTPUT HERE
```[/noparse] if you can) it would be a big help in seeing what's going on(some people have reported lock ups on hardy, I myself experienced one or 2, but nothing after the first kernel update...)



EDIT: it's /var/log on them both, now how did I rename that folder without knowing on my second partition?

---

### Post by adman4054 on 2008-10-28
> **scragar said:**
> A better explination of locked up would be nice, but if it has locked up normaly dmesg will have something to say. so if you managed to recover from the lock up run:
```
dmesg | less
```
or otherwise you can find it in the logs directory(**/var/log** on Ibex, **/var/logs** on hardy and earlier, dunno why that changed), only the latest 2 versions(current and last) are in text format, the remainder are put in tarballs to save space. If you could post the last few lines here([noparse]in ```
OUTPUT HERE
```[/noparse] if you can) it would be a big help in seeing what's going on(some people have reported lock ups on hardy, I myself experienced one or 2, but nothing after the first kernel update...)
Sorry, I have several logs, lastlog, faillog, system log, which one? thanks

---

### Post by adman4054 on 2008-10-28
> **adman4054 said:**
> Sorry, I have several logs, lastlog, faillog, system log, which one? thanks

Sorry again, How do I open these files. I created an association to open with a text editor and that didnt work.
Thanks

---

### Post by scragar on 2008-10-28
/var/log**s**/dmesg and /var/log**s**/dmesg.0 should both open with the text editor, the other ones(the ones ending .gz) should be extracted first(from the command line that can be accomplished with:```
gzip -d **file**
```You may want to copy it to your home folder first so you don't need root perms to extract it).

---

### Post by adman4054 on 2008-10-28
> **scragar said:**
> /var/log**s**/dmesg and /var/log**s**/dmesg.0 should both open with the text editor, the other ones(the ones ending .gz) should be extracted first(from the command line that can be accomplished with:```
gzip -d **file**
```You may want to copy it to your home folder first so you don't need root perms to extract it).
From dmesg
```

100.599545] Attempting manual resume
[  100.599549] swsusp: Resume From Partition 104:5
[  100.599551] PM: Checking swsusp image.
[  100.599716] PM: Resume from disk failed.
[  100.632007] kjournald starting.  Commit interval 5 seconds
[  100.632017] EXT3-fs: mounted filesystem with ordered data mode.
[  104.452986] Linux agpgart interface v0.102
[  104.780450] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[  104.881010] input: Power Button (FF) as /devices/virtual/input/input2
[  104.904578] ACPI: Power Button (FF) [PWRF]
[  105.652184] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  105.688223] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  105.714052] input: PC Speaker as /devices/platform/pcspkr/input/input3
[  105.783760] cpqphp: Compaq Hot Plug PCI Controller Driver version: 0.9.8
[  105.908519] ACPI: PCI Interrupt 0000:06:1e.0[A] -> GSI 18 (level, low) -> IRQ 19
[  105.908533] cpqphp: Hot Plug Subsystem Device ID: a2fe
[  105.908539] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 6
[  105.908547] PCI: Using BIOS Interrupt Routing Table
[  105.910505] PCI: Using BIOS Interrupt Routing Table
[  106.095236] usb 1-3: reset full speed USB device using ohci_hcd and address 2
[  106.266170] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[  106.326234] ndiswrapper: driver wusb11v4 (Cisco-Linksys LLC.,05/13/2004, 3.110.0513.2004) loaded
[  107.291278] wlan0: ethernet device 00:0f:66:e9:30:9d using NDIS driver: wusb11v4, version: 0x36e, NDIS version: 0x501, vendor: 'M4301 NDIS Miniport Driver', 13B1:000B.F.conf
[  107.292806] ndiswrapper (set_iw_encr_mode:717): setting encryption mode to 6 failed (C00000BB)
[  107.294321] wlan0: encryption modes supported: WEP; TKIP with WPA
[  107.295367] usbcore: registered new interface driver ndiswrapper
[  108.029322] lp: driver loaded but no devices found
[  108.092244] Adding 7245272k swap on /dev/cciss/c0d0p5.  Priority:-1 extents:1 across:7245272k
[  108.703110] EXT3 FS on cciss/c0d0p1, internal journal
[  109.844406] ip_tables: (C) 2000-2006 Netfilter Core Team

```

---

### Post by adman4054 on 2008-10-28
> **adman4054 said:**
> From dmesg
```

100.599545] Attempting manual resume
[  100.599549] swsusp: Resume From Partition 104:5
[  100.599551] PM: Checking swsusp image.
[  100.599716] PM: Resume from disk failed.
[  100.632007] kjournald starting.  Commit interval 5 seconds
[  100.632017] EXT3-fs: mounted filesystem with ordered data mode.
[  104.452986] Linux agpgart interface v0.102
[  104.780450] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[  104.881010] input: Power Button (FF) as /devices/virtual/input/input2
[  104.904578] ACPI: Power Button (FF) [PWRF]
[  105.652184] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  105.688223] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  105.714052] input: PC Speaker as /devices/platform/pcspkr/input/input3
[  105.783760] cpqphp: Compaq Hot Plug PCI Controller Driver version: 0.9.8
[  105.908519] ACPI: PCI Interrupt 0000:06:1e.0[A] -> GSI 18 (level, low) -> IRQ 19
[  105.908533] cpqphp: Hot Plug Subsystem Device ID: a2fe
[  105.908539] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 6
[  105.908547] PCI: Using BIOS Interrupt Routing Table
[  105.910505] PCI: Using BIOS Interrupt Routing Table
[  106.095236] usb 1-3: reset full speed USB device using ohci_hcd and address 2
[  106.266170] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[  106.326234] ndiswrapper: driver wusb11v4 (Cisco-Linksys LLC.,05/13/2004, 3.110.0513.2004) loaded
[  107.291278] wlan0: ethernet device 00:0f:66:e9:30:9d using NDIS driver: wusb11v4, version: 0x36e, NDIS version: 0x501, vendor: 'M4301 NDIS Miniport Driver', 13B1:000B.F.conf
[  107.292806] ndiswrapper (set_iw_encr_mode:717): setting encryption mode to 6 failed (C00000BB)
[  107.294321] wlan0: encryption modes supported: WEP; TKIP with WPA
[  107.295367] usbcore: registered new interface driver ndiswrapper
[  108.029322] lp: driver loaded but no devices found
[  108.092244] Adding 7245272k swap on /dev/cciss/c0d0p5.  Priority:-1 extents:1 across:7245272k
[  108.703110] EXT3 FS on cciss/c0d0p1, internal journal
[  109.844406] ip_tables: (C) 2000-2006 Netfilter Core Team

```



from dmesg.0
```

Cannot allocate resource for EISA slot 1
[   71.378043] Cannot allocate resource for EISA slot 2
[   71.378045] Cannot allocate resource for EISA slot 3
[   71.378065] EISA: Detected 0 cards.
[   71.378069] cpuidle: using governor ladder
[   71.378071] cpuidle: using governor menu
[   71.378176] NET: Registered protocol family 1
[   71.378208] Using IPI No-Shortcut mode
[   71.378244] registered taskstats version 1
[   71.378369]   Magic number: 12:728:399
[   71.378479] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   71.378481] EDD information not available.
[   71.378735] Freeing unused kernel memory: 368k freed
[   71.420109] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   72.631648] fuse init (API version 7.9)
[   72.656684] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   72.656699] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   72.656711] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   72.656725] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   72.657992] ACPI: Thermal Zone [THM0] (8 C)
[   72.921032] usbcore: registered new interface driver usbfs
[   72.921070] usbcore: registered new interface driver hub
[   72.921322] usbcore: registered new device driver usb
[   72.921491] tg3.c:v3.86 (November 9, 2007)
[   72.921524] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 29 (level, low) -> IRQ 16
[   72.968627] eth0: Tigon3 [partno(NA) rev 1002 PHY(5703)] (PCIX:100MHz:64-bit) 10/100/1000Base-T Ethernet 00:0b:cd:ef:66:01
[   72.968636] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   72.968639] eth0: dma_rwctrl[769c4000] dma_mask[64-bit]
[   72.968674] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 31 (level, low) -> IRQ 17
[   72.970404] SCSI subsystem initialized
[   72.970542] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   72.970880] ACPI: PCI Interrupt Link [IUSB] enabled at IRQ 11
[   72.970890] ACPI: PCI Interrupt 0000:00:0f.2[A] -> Link [IUSB] -> GSI 11 (level, low) -> IRQ 11
[   72.970908] ohci_hcd 0000:00:0f.2: OHCI Host Controller
[   72.971216] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
[   72.971243] ohci_hcd 0000:00:0f.2: irq 11, io mem 0xeeef0000
[   72.974526] HP CISS Driver (v 3.6.14)
[   73.024568] eth1: Tigon3 [partno(NA) rev 1002 PHY(5703)] (PCIX:100MHz:64-bit) 10/100/1000Base-T Ethernet 00:0b:cd:ef:66:00
[   73.024580] eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   73.024584] eth1: dma_rwctrl[769c4000] dma_mask[64-bit]
[   73.027260] usb usb1: configuration #1 chosen from 1 choice
[   73.027299] hub 1-0:1.0: USB hub found
[   73.027311] hub 1-0:1.0: 4 ports detected
[   73.129375] ACPI: PCI Interrupt 0000:01:03.0[A] -> GSI 30 (level, low) -> IRQ 18
[   73.166355] libata version 3.00 loaded.
[   73.168972] cciss0: <0xb178> at PCI 0000:01:03.0 IRQ 18 using DAC
[   73.170183] Floppy drive(s): fd0 is 1.44M
[   73.181010]       blocks= 355612800 block_size= 512
[   73.182658] PCI: Setting latency timer of device 0000:00:0f.1 to 64
[   73.184945]       heads=255, sectors=32, cylinders=43580
[   73.184949] 
[   73.185168]       blocks= 355612800 block_size= 512
[   73.185336]       heads=255, sectors=32, cylinders=43580
[   73.185338] 
[   73.185342]  cciss/c0d0: p1 p2 <<6>FDC 0 is a National Semiconductor PC87306
[   73.191332]  p5 >
[   73.202441] scsi0 : pata_serverworks
[   73.202526] scsi1 : pata_serverworks
[   73.202570] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2000 irq 14
[   73.202574] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2008 irq 15
[   73.436272] usb 1-3: new full speed USB device using ohci_hcd and address 2
[   73.637602] ata1.00: ATAPI: COMPAQ  CD-ROM SN-124, N104, max PIO4
[   73.652657] usb 1-3: configuration #1 chosen from 1 choice
[   73.809356] ata1.00: configured for PIO4
[   73.854993] Attempting manual resume
[   73.854997] swsusp: Resume From Partition 104:5
[   73.854999] PM: Checking swsusp image.
[   73.855168] PM: Resume from disk failed.
[   73.878635] kjournald starting.  Commit interval 5 seconds
[   73.878645] EXT3-fs: mounted filesystem with ordered data mode.
[   73.965903] scsi 0:0:0:0: CD-ROM            COMPAQ   CD-ROM SN-124    N104 PQ: 0 ANSI: 5
[   78.110095] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   78.195093] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   78.231539] cpqphp: Compaq Hot Plug PCI Controller Driver version: 0.9.8
[   78.231653] ACPI: PCI Interrupt 0000:06:1e.0[A] -> GSI 18 (level, low) -> IRQ 19
[   78.231665] cpqphp: Hot Plug Subsystem Device ID: a2fe
[   78.231671] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 6
[   78.231679] PCI: Using BIOS Interrupt Routing Table
[   78.276764] PCI: Using BIOS Interrupt Routing Table
[   78.388736] Linux agpgart interface v0.102
[   78.532824] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[   78.707671] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[   78.768733] input: Power Button (FF) as /devices/virtual/input/input4
[   78.800363] ACPI: Power Button (FF) [PWRF]
[   79.294220] Driver 'sr' needs updating - please use bus_type methods
[   79.304657] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   79.304664] Uniform CD-ROM driver Revision: 3.20
[   79.304782] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   79.341564] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   79.386204] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   79.683753] usb 1-3: reset full speed USB device using ohci_hcd and address 2
[   79.927402] ndiswrapper: driver wusb11v4 (Cisco-Linksys LLC.,05/13/2004, 3.110.0513.2004) loaded
[   80.891757] wlan0: ethernet device 00:0f:66:e9:30:9d using NDIS driver: wusb11v4, version: 0x36e, NDIS version: 0x501, vendor: 'M4301 NDIS Miniport Driver', 13B1:000B.F.conf
[   80.893280] ndiswrapper (set_iw_encr_mode:717): setting encryption mode to 6 failed (C00000BB)
[   80.894789] wlan0: encryption modes supported: WEP; TKIP with WPA
[   80.895824] usbcore: registered new interface driver ndiswrapper
[   81.542975] lp: driver loaded but no devices found
[   81.672588] Adding 7245272k swap on /dev/cciss/c0d0p5.  Priority:-1 extents:1 across:7245272k
[   82.276948] EXT3 FS on cciss/c0d0p1, internal journal
[   83.424029] ip_tables: (C) 2000-2006 Netfilter Core Team

```

---

### Post by adman4054 on 2008-10-28
It just locked up again. I'll have to kill the box in order to restart. Additional info: keyboard "caps" and "scroll" lock buttons are flashing and the mouse doesnt respond.
Thanks for looking at this:)

---

### Post by adman4054 on 2008-10-28
```

 75.920302] PM: Checking swsusp image.
[   75.920470] PM: Resume from disk failed.
[   75.941471] usb 1-3: configuration #1 chosen from 1 choice
[   75.944533] kjournald starting.  Commit interval 5 seconds
[   75.944544] EXT3-fs: mounted filesystem with ordered data mode.
[   76.025232] ata1.00: configured for PIO4
[   76.177870] scsi 0:0:0:0: CD-ROM            COMPAQ   CD-ROM SN-124    N104 PQ: 0 ANSI: 5
[   80.150345] Linux agpgart interface v0.102
[   80.470432] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   80.513679] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   80.554112] cpqphp: Compaq Hot Plug PCI Controller Driver version: 0.9.8
[   80.554225] ACPI: PCI Interrupt 0000:06:1e.0[A] -> GSI 18 (level, low) -> IRQ 19
[   80.554237] cpqphp: Hot Plug Subsystem Device ID: a2fe
[   80.554243] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 6
[   80.554252] PCI: Using BIOS Interrupt Routing Table
[   80.585919] PCI: Using BIOS Interrupt Routing Table
[   80.610069] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
[   80.657701] input: Power Button (FF) as /devices/virtual/input/input3
[   80.673844] ACPI: Power Button (FF) [PWRF]
[   81.133127] Driver 'sr' needs updating - please use bus_type methods
[   81.164942] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[   81.164949] Uniform CD-ROM driver Revision: 3.20
[   81.165040] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   81.235778] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   81.506502] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   81.801964] usb 1-3: reset full speed USB device using ohci_hcd and address 2
[   82.037941] ndiswrapper: driver wusb11v4 (Cisco-Linksys LLC.,05/13/2004, 3.110.0513.2004) loaded
[   82.080135] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   83.000428] wlan0: ethernet device 00:0f:66:e9:30:9d using NDIS driver: wusb11v4, version: 0x36e, NDIS version: 0x501, vendor: 'M4301 NDIS Miniport Driver', 13B1:000B.F.conf
[   83.001948] ndiswrapper (set_iw_encr_mode:717): setting encryption mode to 6 failed (C00000BB)
[   83.003458] wlan0: encryption modes supported: WEP; TKIP with WPA
[   83.004499] usbcore: registered new interface driver ndiswrapper
[   83.693408] lp: driver loaded but no devices found
[   83.749287] Adding 7245272k swap on /dev/cciss/c0d0p5.  Priority:-1 extents:1 across:7245272k
[   84.373695] EXT3 FS on cciss/c0d0p1, internal journal
[   85.586246] ip_tables: (C) 2000-2006 Netfilter Core Team

```

---

### Post by adman4054 on 2008-10-28
Locked up again after copy and pasting the above. Thanks

---

### Post by scragar on 2008-10-28
OK, stop posting those for now, I'm going to go out on a limb here and say it's most likely one of 2 already related bugs, both of which are reported, the first is a kernel problem, which has(although it's not been confirmed to have) been for Ibex, the other is related to NDIS wrapper, where it is unable to handle large levels of network activity(which sounds likely, since you are both running NDIS wrapper and have the same flashing capslock/numlock reported in the bug report).

The first bug should be fixed if you upgrade the kernel to the Ibex kernel if you copy/paste these lines 1 at a time to a terminal:```
sudo -i
echo "deb http://ppa.launchpad.net/kernel-ppa/ubuntu hardy main" > /etc/apt/sources.list.d/kernel-ppa.list
deb-src http://ppa.launchpad.net/kernel-ppa/ubuntu hardy main >> /etc/apt/sources.list.d/kernel-ppa.list
apt-get update
apt-get upgrade
rm /etc/apt/sources.list.d/kernel-ppa.list
apt-get update
exit
```
The second can be fixed by downloading the updated NDIS wrapper package from [HERE](http://packages.ubuntu.com/intrepid/all/ndiswrapper-common/download)

let me know how you get on.

---

### Post by adman4054 on 2008-10-28
Really appreciate you taking the time....

This is what I'm getting

adman4054@stuff2:~$ sudo -i
[sudo] password for adman4054: 
root@stuff2:~# sudo -i
root@stuff2:~# echo "deb [http://ppa.launchpad.net/kernel-ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ubuntu) hardy main" > /etc/apt/sources.list.d/kernel-ppa.list
root@stuff2:~# 
root@stuff2:~# deb-src [http://ppa.launchpad.net/kernel-ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ubuntu) hardy main >> /etc/apt/sources.list.d/kernel-ppa.list
-bash: deb-src: command not found
root@stuff2:~# echo "deb [http://ppa.launchpad.net/kernel-ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ubuntu) hardy main" > /etc/apt/sources.list.d/kernel-ppa.list
root@stuff2:~# deb-src [http://ppa.launchpad.net/kernel-ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ubuntu) hardy main >> /etc/apt/sources.list.d/kernel-ppa.list
-bash: deb-src: command not found








> **scragar said:**
> OK, stop posting those for now, I'm going to go out on a limb here and say it's most likely one of 2 already related bugs, both of which are reported, the first is a kernel problem, which has(although it's not been confirmed to have) been for Ibex, the other is related to NDIS wrapper, where it is unable to handle large levels of network activity(which sounds likely, since you are both running NDIS wrapper and have the same flashing capslock/numlock reported in the bug report).

The first bug should be fixed if you upgrade the kernel to the Ibex kernel if you copy/paste these lines 1 at a time to a terminal:```
sudo -i
echo "deb http://ppa.launchpad.net/kernel-ppa/ubuntu hardy main" > /etc/apt/sources.list.d/kernel-ppa.list
deb-src http://ppa.launchpad.net/kernel-ppa/ubuntu hardy main >> /etc/apt/sources.list.d/kernel-ppa.list
apt-get update
apt-get upgrade
rm /etc/apt/sources.list.d/kernel-ppa.list
apt-get update
exit
```
The second can be fixed by downloading the updated NDIS wrapper package from [HERE](http://packages.ubuntu.com/intrepid/all/ndiswrapper-common/download)

let me know how you get on.

---

### Post by scragar on 2008-10-28
oops, my fault, it should be:
```
echo "echo "deb-src http://ppa.launchpad.net/kernel-ppa/ubuntu hardy main" > /etc/apt/sources.list.d/kernel-ppa.list
```

---

### Post by adman4054 on 2008-10-28
Again, appreciate the help.
I performed the first fix,didnt receive any error messgaes, but didnt receive a confirmation either, is that ok?
NDIS Wrapper, I tried to do it through the Synaptic, but it didnt show up on the list, can you tell me how to do manually.
Thanks


> **scragar said:**
> oops, my fault, it should be:
```
echo "echo "deb-src http://ppa.launchpad.net/kernel-ppa/ubuntu hardy main" > /etc/apt/sources.list.d/kernel-ppa.list
```

---

### Post by adman4054 on 2008-10-28
I reinstalled the new NDIS wrapper and I lost my internet connection, then I got to thinking how I connected to begin with. I dropped a Linksys driver on the machine and I was able to connect to the Internet. Could that have been the issue all along? I'll search the forums for an answer, but with this new NDIS wrapper, am I suppose to do something other then using a Linksys driver?
Thanks. 



> **adman4054 said:**
> Again, appreciate the help.
I performed the first fix,didnt receive any error messgaes, but didnt receive a confirmation either, is that ok?
NDIS Wrapper, I tried to do it through the Synaptic, but it didnt show up on the list, can you tell me how to do manually.
Thanks

---

### Post by scragar on 2008-10-28
I think it's better to see how you go, I am only following the advice given on the bug reports(which I've now lost the links to, I'll find it again in the morning(almost midnight now so I'm off to bed)).

---

### Post by adman4054 on 2008-10-29
Scragar--
You have been very helpful and I think that your fixes may have solved the issue, but maybe you can assist me in fixing one last issue associated with the fix. First the update, I applied both of your fixes yesterday and worked the machine with many open browser windows and other tasks without a single lock up, yea! When I installed the new ndis wrapper I lost my wireless capability, thats ok, I know how I can fix that, but I lost my cd drive in the process. I held down the "mount" button for the cd through the file manager (I think thats where. Now the cd doesnt appear to be loading. I dont see it listed as a valid drive or any drive for that matter. I tried mounting the drive through the terminal, mount /dev/cd0 and I also tried to mount a usb drive mount /dev/sd1 (both these might not be exactly as I did them, it was getting late). I was following instructions on the web. Both said couldnt find them in fstabs. I checked the fstabs file (I added a line to that file for the usb drive) and the devices are in that file, but not loading. Any ideas? Thanks for being so helpful, the last thing I want to do is to be forced to go back to Windoze over a few small issues. 


> **scragar said:**
> I think it's better to see how you go, I am only following the advice given on the bug reports(which I've now lost the links to, I'll find it again in the morning(almost midnight now so I'm off to bed)).

---

### Post by scragar on 2008-10-29
[Have you tried following this documentation?](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper))

I have never had to get wireless working on any of my machines, so I'm not to good at offering advice on that sort of thing, sorry.

---

### Post by adman4054 on 2008-10-29
Thats quite allright. You have been a big help! Thanks!

> **scragar said:**
> [Have you tried following this documentation?](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper))

I have never had to get wireless working on any of my machines, so I'm not to good at offering advice on that sort of thing, sorry.

---

### Post by neobadandy on 2009-06-25
USE THIS TO INSTALL LAMP ON UBUNTU

 sudo apt-get install apache2 mysql-server mysql-client php5 php5-mysql


ALL DONE

SAVED MY LIFE

---

### Post by crohakon on 2010-09-01
Why does your server have wireless? And why not install the Ubuntu server edition as it IS for servers. Yes, no GUI, but Ubuntu offers a kicka$$ server guide with step by step directions. I have been hosting my own sites in my basement for over a year now with the help of dyndns. Uptime? Well, I had to restart maybe 4 times. The power going out was responsible for 3 of the 4. Once I had to restart after a coppermine installation went resource hungry (reboot, works like a charm now.)

Ubuntu desktop is great, but it is not streamlined for server usage.

---

### Post by bigboy_pdb on 2010-09-01
This thread is from a couple of years ago.

For anyone else reading this, responding is unnecessary and most likely unhelpful.

---

### Post by lisati on 2010-09-01
> **bigboy_pdb said:**
> This thread is from a couple of years ago.

For anyone else reading this, responding is unnecessary and most likely unhelpful.

Agreed, thread now closed.

If the original participants want to get back to us with an update, I'm sure one of the staff can re-open this thread. Otherwise we can let this thread rest and sink out of sight.

---

