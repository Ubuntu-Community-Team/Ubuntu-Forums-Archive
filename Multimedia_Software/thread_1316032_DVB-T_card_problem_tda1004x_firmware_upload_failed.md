---
title: "DVB-T card problem: tda1004x: firmware upload failed"
date: 2009-11-05
forum: Multimedia Software
---

### Post by kem on 2009-11-05
Hi, I have problem to get working my DVB-T card in Karmic. I would appreciate any help as I am troubleshooting it for several days - so far without success.

Kernel: 2.6.31-14-generic

```
lspci
00:0d.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
```

```
[   17.487020] saa7133[0]/alsa: saa7133[0] at 0xea800000 irq 16 registered as card -2
[   17.588982] dvb_init() allocating 1 frontend
[   17.676301] DVB: registering new adapter (saa7133[0])
[   17.676317] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   17.812721] tda1004x: setting up plls for 48MHz sampling clock
[   17.986415] codec_read: codec 0 is not valid [0x87e5370]
[   17.992716] codec_read: codec 0 is not valid [0x87e5370]
[   17.998912] codec_read: codec 0 is not valid [0x87e5370]
[   18.005150] codec_read: codec 0 is not valid [0x87e5370]
[   20.096016] tda1004x: timeout waiting for DSP ready
[   20.136015] tda1004x: found firmware revision 0 -- invalid
[   20.136023] tda1004x: trying to boot from eeprom

...

[   22.468012] tda1004x: timeout waiting for DSP ready
[   22.508016] tda1004x: found firmware revision 0 -- invalid
[   22.508024] tda1004x: waiting for firmware upload...
[   22.508035] saa7134 0000:00:0d.0: firmware: requesting dvb-fe-tda10046.fw
[   22.529641] saa7134 0000:00:0d.0: firmware: requesting dvb-fe-tda10045.fw
[   22.545791] tda1004x: no firmware upload (timeout or file not found?)
[   22.545847] tda1004x: firmware upload failed
```

I believe it is firmware problem. Should I report it as a bug? I have found similar (not same) problem solved [here]("http://ubuntuforums.org/archive/index.php/t-1223720.html") by ddrichardson


Anyway. I tried to manually insert dvb-fe-tda10046.fw into /lib/firmware  according to a Google advice. Then I got another problems. Particularly 
- "timeout waiting for dsp" in dmesg
- MythTV was unable to find any channel though w_scan was working

Both problems seems to be common with this DVB-T chip according to Google and there are some outdated "hacking advices" to solve it. However, I believe it should work out-of-the-box. Should I report it as another bug?

Thanks.

---

### Post by Jose Catre-Vandis on 2009-11-06
Having problems too with this chip on Karmic. I can scan OK and watch TV, but the signal is degredated - lots of pops and clicks on the sound and screen artifacts and strange swirling effects, and I am getting a lot of errors/messages if I run mplayer through a terminal to see output. On wrong machine at the moment but will post output asap.

With regards to your problem, yes, it should just work out of the box, and has been the case for several revisions of Ubuntu

There is also a bug on this in luanchpad, along with a lot of other dvb related issues
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446575?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/446575?comments=all)

---

### Post by kem on 2009-11-08
Finally, I resolved this issue by installing dvb-fe-tda10046.fw
firmware manually. I have to increase timeout setting for channel scan timeout for proper installation in order to setup mythtv server properly.

---

### Post by Jose Catre-Vandis on 2009-11-08
Let me know what your output is like. I could scan OK but got poor quality picture/sound. I'll try the firmware fix.

EDIT

The firmware fix didn't make any difference to playback, artifacts and sound glitches still there.

If I do a dumpstream with mplayer the recorded file is almost perfect

Using the the mplayer-nogui:
```
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
```

---

### Post by kem on 2009-11-09
Jose,

the quality of picture and sound was perfect. Channel tunning, watching, recording, scheduled recording was working fine. However, after (several?) restart i got 
```

[   23.652206] saa7133[0]: registered device video1 [v4l2]
[   23.652254] saa7133[0]: registered device vbi0
[   23.664114]   alloc irq_desc for 22 on node -1
[   23.664122]   alloc kstat_irqs on node -1
[   23.664139] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   23.666928] saa7134 ALSA driver for DMA sound loaded
[   23.666964] IRQ 16/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   23.667012] saa7133[0]/alsa: saa7133[0] at 0xea800000 irq 16 registered as card -2
[   23.677242] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   23.809992] dvb_init() allocating 1 frontend
[   23.912407] DVB: registering new adapter (saa7133[0])
[   23.912427] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   24.068016] tda1004x: setting up plls for 48MHz sampling clock
[   24.197082] codec_read: codec 0 is not valid [0x87e5370]
[   24.206582] codec_read: codec 0 is not valid [0x87e5370]
[   24.213061] codec_read: codec 0 is not valid [0x87e5370]
[   24.238863] codec_read: codec 0 is not valid [0x87e5370]
[   25.636055] eth0: no IPv6 routers present
[   26.396079] tda1004x: timeout waiting for DSP ready
[   26.444001] tda1004x: found firmware revision 0 -- invalid
[   26.444096] tda1004x: trying to boot from eeprom
[   28.774554] tda1004x: timeout waiting for DSP ready
[   28.814081] tda1004x: found firmware revision 0 -- invalid
[   28.814092] tda1004x: waiting for firmware upload...
[   28.814105] saa7134 0000:00:0d.0: firmware: requesting dvb-fe-tda10046.fw
[   35.160032] tda1004x: setting up plls for 48MHz sampling clock
[   41.492017] tda1004x: timeout waiting for DSP ready
[   41.532018] tda1004x: found firmware revision 0 -- invalid
[   41.532027] tda1004x: trying to boot from eeprom
[   43.596019] tda1004x: timeout waiting for DSP ready
[   43.636020] tda1004x: found firmware revision 0 -- invalid
[   43.636027] tda1004x: firmware upload failed
[   43.912089] tda1004x: timeout waiting for DSP ready
[   43.968023] tda1004x: found firmware revision 80 -- invalid
[   43.968032] tda1004x: waiting for firmware upload...
[   43.968044] saa7134 0000:00:0d.0: firmware: requesting dvb-fe-tda10046.fw
[   44.216328] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   44.216366] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   44.216433] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   44.495721] [drm] Setting GART location based on new memory map
[   44.495738] [drm] Loading R200 Microcode
[   44.495792] [drm] writeback test succeeded in 1 usecs
[   60.728015] tda1004x: timeout waiting for DSP ready
[   60.768013] tda1004x: found firmware revision 80 -- invalid
[   60.768019] tda1004x: firmware upload failed
[   66.661750] glxinfo:2115 freeing invalid memtype f8102000-f8112000
[   66.661768] glxinfo:2115 freeing invalid memtype f8112000-f8122000
[   66.661781] glxinfo:2115 freeing invalid memtype f8122000-f8132000
[   66.661793] glxinfo:2115 freeing invalid memtype f8132000-f8142000
[   66.661805] glxinfo:2115 freeing invalid memtype f8142000-f8152000
[   66.661816] glxinfo:2115 freeing invalid memtype f8152000-f8162000
[   66.661828] glxinfo:2115 freeing invalid memtype f8162000-f8172000
[   66.661839] glxinfo:2115 freeing invalid memtype f8172000-f8182000

```

... and card is not working. Well, I should start again to solve it. The worst is I don't know what to do. Should I try to install a firmware manually using mercurial as indicated [here]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers") or should I work with V4L drivers located in Ubuntu repos? I am quite tired with it - I have been trying to resolve it for two weeks. :(

---

### Post by kem on 2009-11-09
> **Jose Catre-Vandis said:**
> 
The firmware fix didn't make any difference to playback, artifacts and sound glitches still there.

If I do a dumpstream with mplayer the recorded file is almost perfect


According to my experience the good and quick method to test it is 
1) generate channels.conf using this command (use your country abbreviation instead of cz)
```
w_scan -c cz -X >> channels.conf
```
It takes several minutes but it should be done just one time.

2) play this channels.conf using vlc
```
vlc channels.conf
```

---

### Post by xc3RnbFO8P on 2009-11-09
Mine is OK.
lspci:
> 02:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
dmesg:
```
[   12.841613] saa7134 0000:02:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.841619] saa7133[0]: found at 0000:02:01.0, rev: 209, irq: 17, latency: 84, mmio: 0xfddff000
[   12.841624] saa7133[0]: subsystem: 16be:000d, board: Medion Md8800 Quadro [card=96,autodetected]
[   12.841638] saa7133[0]: board init: gpio is 0
[   12.841644] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   12.992571] saa7133[0]: i2c eeprom 00: be 16 0d 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   12.992587] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff 00 01 50 32 79 01 3c ca 50
[   12.992601] saa7133[0]: i2c eeprom 20: 01 40 01 02 02 03 01 00 06 ff 00 29 02 51 96 2b
[   12.992615] saa7133[0]: i2c eeprom 30: a7 58 7a 1f 03 8e 84 5e da 7a 04 b3 05 87 b2 3c
[   12.992629] saa7133[0]: i2c eeprom 40: ff 28 00 c0 96 10 03 00 c0 1c fd 79 44 9f c2 8f
[   12.992643] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992657] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992671] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992695] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992705] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992714] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992723] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992732] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992742] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992751] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992760] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   12.992771] i2c-adapter i2c-0: Invalid 7-bit address 0x7a
[   13.544637] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[   13.624552] tda829x 0-004b: setting tuner address to 60
[   13.692549] tda829x 0-004b: type set to tda8290+75a
[   14.661700]   alloc irq_desc for 22 on node -1
[   14.661703]   alloc kstat_irqs on node -1
[   14.661710] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   14.661751] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   14.731643] hda_codec: Unknown model for ALC1200, trying auto-probe from BIOS...
[   14.731915] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
[   15.087207] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.089769] rtusb init --->
[   15.089818] usbcore: registered new interface driver rt2870
[   15.091065] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[   15.093624] rtusb init --->
[   15.093627] Error: Driver 'rt2870' is already registered, aborting...
[   15.093631] usbcore: error -17 registering interface 	driver rt2870
[   15.784340] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
[   15.840087] e1000e 0000:00:19.0: irq 26 for MSI/MSI-X
[   15.840336] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.201910] rt2800usb 1-5:1.0: firmware: requesting rt2870.bin
[   16.317181] input: rt2800usb as /devices/pci0000:00/0000:00:1a.7/usb1/1-5/1-5:1.0/input/input10
[   16.502733] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.202177] ppdev: user-space parallel port driver
[   17.404769] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: None
[   17.404773] 0000:00:19.0: eth0: 10/100 speed: disabling TSO
[   17.404970] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.560301] saa7133[0]: dsp access error
[   17.560312] saa7133[0]: dsp access error
[   17.624105] saa7133[0]: registered device video0 [v4l2]
[   17.624138] saa7133[0]: registered device vbi0
[   17.628164] saa7134 ALSA driver for DMA sound loaded
[   17.628174] IRQ 17/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   17.628193] saa7133[0]/alsa: saa7133[0] at 0xfddff000 irq 17 registered as card -2
[   17.669608] dvb_init() allocating 1 frontend
[   17.685186] DVB: registering new adapter (saa7133[0])
[   17.685190] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   17.757109] tda1004x: setting up plls for 48MHz sampling clock
[   19.745030] tda1004x: found firmware revision 26 -- ok
```

---

### Post by kem on 2009-11-09
0) Thanks Ringi!

1) I have found useful advice to install firmware in [http://ubuntuforums.org/showthread.php?p=8283460](http://ubuntuforums.org/showthread.php?p=8283460)

2) Maybe my problems are derived from Radeon 9200 card bug which is solved here [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139)

3) Here is my complete dmesg. 

```
[    0.110232] usbcore: registered new device driver usb
[    0.110489] ACPI: WMI: Mapper loaded
[    0.110493] PCI: Using ACPI for IRQ routing
[    0.110750] Bluetooth: Core ver 2.15
[    0.110820] NET: Registered protocol family 31
[    0.110824] Bluetooth: HCI device and connection manager initialized
[    0.110830] Bluetooth: HCI socket layer initialized
[    0.110834] NetLabel: Initializing
[    0.110837] NetLabel:  domain hash size = 128
[    0.110840] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.110869] NetLabel:  unlabeled traffic allowed by default
[    0.115150] pnp: PnP ACPI init
[    0.115204] ACPI: bus type pnp registered
[    0.121820] pnp: PnP ACPI: found 15 devices
[    0.121825] ACPI: ACPI bus type pnp unregistered
[    0.121833] PnPBIOS: Disabled by ACPI PNP
[    0.121856] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[    0.121863] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.121868] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[    0.121874] system 00:00: iomem range 0xfec00000-0xfec000ff could not be reserved
[    0.121880] system 00:00: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.121893] system 00:02: ioport range 0xe400-0xe47f has been reserved
[    0.121898] system 00:02: ioport range 0xe800-0xe81f could not be reserved
[    0.121904] system 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.121910] system 00:02: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.121920] system 00:03: ioport range 0x4d0-0x4d1 has been reserved
[    0.121933] system 00:0e: ioport range 0x290-0x297 has been reserved
[    0.121938] system 00:0e: ioport range 0x370-0x375 has been reserved
[    0.156740] AppArmor: AppArmor Filesystem Enabled
[    0.156771] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.156777] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.156787] pci 0000:00:01.0:   MEM window: 0xeb000000-0xebffffff
[    0.156794] pci 0000:00:01.0:   PREFETCH window: 0xec000000-0xf7ffffff
[    0.156817] pci 0000:00:01.0: setting latency timer to 64
[    0.156827] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.156832] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.156837] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.156842] pci_bus 0000:01: resource 1 mem: [0xeb000000-0xebffffff]
[    0.156847] pci_bus 0000:01: resource 2 pref mem [0xec000000-0xf7ffffff]
[    0.156922] NET: Registered protocol family 2
[    0.157096] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.157609] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.157941] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.158274] TCP: Hash tables configured (established 16384 bind 16384)
[    0.158279] TCP reno registered
[    0.158457] NET: Registered protocol family 1
[    0.158619] Trying to unpack rootfs image as initramfs...
[    0.514982] Freeing initrd memory: 7466k freed
[    0.534665] Simple Boot Flag at 0x3a set to 0x1
[    0.534883] cpufreq-nforce2: No nForce2 chipset.
[    0.534979] Scanning for low memory corruption every 60 seconds
[    0.535220] audit: initializing netlink socket (disabled)
[    0.535257] type=2000 audit(1257828061.532:1): initialized
[    0.549074] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.551715] VFS: Disk quotas dquot_6.5.2
[    0.551816] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.552844] fuse init (API version 7.12)
[    0.552992] msgmni has been set to 993
[    0.553434] alg: No test for stdrng (krng)
[    0.553461] io scheduler noop registered
[    0.553465] io scheduler anticipatory registered
[    0.553469] io scheduler deadline registered
[    0.553544] io scheduler cfq registered (default)
[    0.553571] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.553672] pci 0000:01:00.0: Boot video device
[    0.553834] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.553879] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.554132] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.554142] ACPI: Power Button [PWRF]
[    0.554234] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.554240] ACPI: Power Button [PWRB]
[    0.554556] processor LNXCPU:00: registered as cooling_device0
[    0.559067] isapnp: Scanning for PnP cards...
[    0.660087] Switched to high resolution mode on CPU 0
[    0.913038] isapnp: No Plug & Play device found
[    0.915096] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.915247] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.915694] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.917603] brd: module loaded
[    0.918449] loop: module loaded
[    0.918635] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.919605] pata_via 0000:00:11.1: version 0.3.4
[    0.919640] pata_via 0000:00:11.1: can't derive routing for PCI INT A
[    0.920109] scsi0 : pata_via
[    0.920325] scsi1 : pata_via
[    0.921472] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xa800 irq 14
[    0.921479] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xa808 irq 15
[    0.922147] Fixed MDIO Bus: probed
[    0.922214] PPP generic driver version 2.4.2
[    0.922440] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.922486]   alloc irq_desc for 21 on node -1
[    0.922491]   alloc kstat_irqs on node -1
[    0.922505] ehci_hcd 0000:00:10.3: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.922543] ehci_hcd 0000:00:10.3: EHCI Host Controller
[    0.922669] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 1
[    0.922779] ehci_hcd 0000:00:10.3: irq 21, io mem 0xea000000
[    0.932015] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00
[    0.932176] usb usb1: configuration #1 chosen from 1 choice
[    0.932233] hub 1-0:1.0: USB hub found
[    0.932256] hub 1-0:1.0: 6 ports detected
[    0.932379] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.932416] uhci_hcd: USB Universal Host Controller Interface driver
[    0.932526] uhci_hcd 0000:00:10.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    0.932543] uhci_hcd 0000:00:10.0: UHCI Host Controller
[    0.932609] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[    0.932639] uhci_hcd 0000:00:10.0: irq 21, io base 0x0000b800
[    0.932786] usb usb2: configuration #1 chosen from 1 choice
[    0.932842] hub 2-0:1.0: USB hub found
[    0.932861] hub 2-0:1.0: 2 ports detected
[    0.932942] uhci_hcd 0000:00:10.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.932952] uhci_hcd 0000:00:10.1: UHCI Host Controller
[    0.933016] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[    0.933042] uhci_hcd 0000:00:10.1: irq 21, io base 0x0000b400
[    0.933212] usb usb3: configuration #1 chosen from 1 choice
[    0.933267] hub 3-0:1.0: USB hub found
[    0.933285] hub 3-0:1.0: 2 ports detected
[    0.933353] uhci_hcd 0000:00:10.2: PCI INT C -> GSI 21 (level, low) -> IRQ 21
[    0.933363] uhci_hcd 0000:00:10.2: UHCI Host Controller
[    0.933429] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[    0.933455] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000b000
[    0.933606] usb usb4: configuration #1 chosen from 1 choice
[    0.933651] hub 4-0:1.0: USB hub found
[    0.933668] hub 4-0:1.0: 2 ports detected
[    0.933845] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.936203] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.936217] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.936343] mice: PS/2 mouse device common for all mice
[    0.936499] rtc_cmos 00:05: RTC can wake from S4
[    0.936589] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.936652] rtc0: alarms up to one month, 242 bytes nvram
[    0.936847] device-mapper: uevent: version 1.0.3
[    0.937055] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.937229] device-mapper: multipath: version 1.1.0 loaded
[    0.937236] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.937495] EISA: Probing bus 0 at eisa.0
[    0.937538] EISA: Detected 0 cards.
[    0.937644] cpuidle: using governor ladder
[    0.937649] cpuidle: using governor menu
[    0.938544] TCP cubic registered
[    0.938801] NET: Registered protocol family 10
[    0.939583] lo: Disabled Privacy Extensions
[    0.940164] NET: Registered protocol family 17
[    0.940206] Bluetooth: L2CAP ver 2.13
[    0.940209] Bluetooth: L2CAP socket layer initialized
[    0.940215] Bluetooth: SCO (Voice Link) ver 0.6
[    0.940218] Bluetooth: SCO socket layer initialized
[    0.940318] Bluetooth: RFCOMM TTY layer initialized
[    0.940325] Bluetooth: RFCOMM socket layer initialized
[    0.940328] Bluetooth: RFCOMM ver 1.11
[    0.940363] powernow-k8: Processor cpuid 6a0 not supported
[    0.940411] Using IPI No-Shortcut mode
[    0.940561] PM: Resume from disk failed.
[    0.940601] registered taskstats version 1
[    0.940815]   Magic number: 1:336:666
[    0.941006] rtc_cmos 00:05: setting system clock to 2009-11-10 04:41:02 UTC (1257828062)
[    0.941013] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.941017] EDD information not available.
[    0.964536] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.260555] ata1.00: ATA-6: ST340014A, 3.54, max UDMA/100
[    1.260560] ata1.00: 78165360 sectors, multi 16: LBA48 
[    1.260741] ata1.01: ATA-6: WDC WD800JB-00JJC0, 05.01C05, max UDMA/100
[    1.260746] ata1.01: 156301488 sectors, multi 16: LBA 
[    1.276431] ata1.00: configured for UDMA/100
[    1.284366] ata1.01: configured for UDMA/100
[    1.284618] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        3.54 PQ: 0 ANSI: 5
[    1.284864] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.284978] scsi 0:0:1:0: Direct-Access     ATA      WDC WD800JB-00JJ 05.0 PQ: 0 ANSI: 5
[    1.285159] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.285244] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.285341] sd 0:0:0:0: [sda] Write Protect is off
[    1.285346] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.285396] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.285663]  sda: sda1 sda2 sda3 < sda5 >
[    1.324812] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.324833] sd 0:0:1:0: [sdb] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.324916] sd 0:0:1:0: [sdb] Write Protect is off
[    1.324922] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.324967] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.325198]  sdb: sdb1 < sdb5 >
[    1.335590] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.448381] ata2.00: ATAPI: HL-DT-ST RW/DVD GCC-4480B, 1.00, max UDMA/33
[    1.464260] ata2.00: configured for UDMA/33
[    1.465039] scsi 1:0:0:0: CD-ROM            HL-DT-ST RW/DVD GCC-4480B 1.00 PQ: 0 ANSI: 5
[    1.466982] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.466989] Uniform CD-ROM driver Revision: 3.20
[    1.467186] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.467297] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.467352] Freeing unused kernel memory: 540k freed
[    1.468748] Write protecting the kernel text: 4568k
[    1.468802] Write protecting the kernel read-only data: 1836k
[    1.640202] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    1.806929] Linux agpgart interface v0.103
[    1.811484] agpgart: Detected VIA KT400/KT400A/KT600 chipset
[    1.820929] Floppy drive(s): fd0 is 1.44M
[    1.842597] FDC 0 is a post-1991 82077
[    1.843018] usb 3-2: configuration #1 chosen from 1 choice
[    1.868468] via-rhine.c:v1.10-LK1.4.3 2007-03-06 Written by Donald Becker
[    1.933330] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xf8000000
[    1.933474]   alloc irq_desc for 23 on node -1
[    1.933479]   alloc kstat_irqs on node -1
[    1.933496] via-rhine 0000:00:12.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.934670] eth0: VIA Rhine II at 0xe9800000, 00:0c:6e:78:48:18, IRQ 23.
[    1.935387] eth0: MII PHY found at address 1, status 0x786d advertising 01e1 Link 45e1.
[    2.157369] [drm] Initialized drm 1.1.0 20060810
[    2.197404] [drm] radeon default to kernel modesetting DISABLED.
[    2.197583]   alloc irq_desc for 16 on node -1
[    2.197588]   alloc kstat_irqs on node -1
[    2.197604] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.197889] [drm] Initialized radeon 1.31.0 20080528 for 0000:01:00.0 on minor 0
[    3.897487] PM: Starting manual resume from disk
[    3.897499] PM: Resume from partition 8:5
[    3.897502] PM: Checking hibernation image.
[    3.897835] PM: Resume from disk failed.
[    3.933994] EXT4-fs (sda2): barriers enabled
[    3.954026] kjournald2 starting: pid 337, dev sda2:8, commit interval 5 seconds
[    3.954062] EXT4-fs (sda2): delayed allocation enabled
[    3.954068] EXT4-fs: file extents enabled
[    3.959372] EXT4-fs: mballoc enabled
[    3.959404] EXT4-fs (sda2): mounted filesystem with ordered data mode
[    4.665862] type=1505 audit(1257828066.223:2): operation="profile_load" pid=360 name=/usr/share/gdm/guest-session/Xsession
[    4.670674] type=1505 audit(1257828066.227:3): operation="profile_load" pid=361 name=/sbin/dhclient3
[    4.671187] type=1505 audit(1257828066.227:4): operation="profile_load" pid=361 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.671479] type=1505 audit(1257828066.227:5): operation="profile_load" pid=361 name=/usr/lib/connman/scripts/dhclient-script
[    4.708420] type=1505 audit(1257828066.267:6): operation="profile_load" pid=362 name=/usr/bin/evince
[    4.718035] type=1505 audit(1257828066.275:7): operation="profile_load" pid=362 name=/usr/bin/evince-previewer
[    4.724035] type=1505 audit(1257828066.279:8): operation="profile_load" pid=362 name=/usr/bin/evince-thumbnailer
[    4.741635] type=1505 audit(1257828066.299:9): operation="profile_load" pid=364 name=/usr/lib/cups/backend/cups-pdf
[    4.742292] type=1505 audit(1257828066.299:10): operation="profile_load" pid=364 name=/usr/sbin/cupsd
[    6.099771] Adding 1397612k swap on /dev/sda5.  Priority:-1 extents:1 across:1397612k 
[    6.450482] udev: starting version 147
[    6.948118] EXT4-fs (sda2): internal journal on sda2:8
[    7.569892] irda_init()
[    7.569929] NET: Registered protocol family 23
[    7.934619] EXT4-fs (sdb5): barriers enabled
[    7.950051] kjournald2 starting: pid 603, dev sdb5:8, commit interval 5 seconds
[    7.950471] EXT4-fs (sdb5): internal journal on sdb5:8
[    7.950478] EXT4-fs (sdb5): delayed allocation enabled
[    7.950484] EXT4-fs: file extents enabled
[    7.959916] EXT4-fs: mballoc enabled
[    7.959959] EXT4-fs (sdb5): mounted filesystem with ordered data mode
[    8.452586] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    8.650729] parport_pc 00:09: reported by Plug and Play ACPI
[    8.650808] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[    8.702527] lp: driver loaded but no devices found
[    8.706731] ppdev: user-space parallel port driver
[    8.744425] lp0: using parport0 (interrupt-driven).
[    8.870802] ip_tables: (C) 2000-2006 Netfilter Core Team
[    9.749145] Linux video capture interface: v2.00
[    9.752381] gameport: NS558 PnP Gameport is pnp00:0d/gameport0, io 0x200, speed 1104kHz
[   10.102054]   alloc irq_desc for 22 on node -1
[   10.102062]   alloc kstat_irqs on node -1
[   10.102078] VIA 82xx Audio 0000:00:11.5: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[   10.104381] VIA 82xx Audio 0000:00:11.5: setting latency timer to 64
[   10.477126] saa7130/34: v4l2 driver version 0.2.15 loaded
[   10.567945] gspca: main v2.6.0 registered
[   10.591597] gspca: probing 05a9:4519
[   10.621226] codec_read: codec 0 is not valid [0x87e5370]
[   10.628060] codec_read: codec 0 is not valid [0x87e5370]
[   10.635367] codec_read: codec 0 is not valid [0x87e5370]
[   10.641937] codec_read: codec 0 is not valid [0x87e5370]
[   10.657841] saa7134 0000:00:0d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.657856] saa7133[0]: found at 0000:00:0d.0, rev: 209, irq: 16, latency: 32, mmio: 0xea800000
[   10.657868] saa7133[0]: subsystem: 1461:f01d, board: Avermedia Super 007 [card=117,autodetected]
[   10.657906] saa7133[0]: board init: gpio is 40000
[   10.657932] IRQ 16/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   10.765496] psmouse serio1: ID: 10 00 64
[   10.823898] ov519: I2C synced in 0 attempt(s)
[   10.823908] ov519: starting OV7xx0 configuration
[   10.824876] saa7133[0]: i2c eeprom 00: 61 14 1d f0 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   10.824894] saa7133[0]: i2c eeprom 10: ff ff ff ff ff 20 ff ff ff ff ff ff ff ff ff ff
[   10.824909] saa7133[0]: i2c eeprom 20: 01 40 01 32 32 01 01 43 88 ff 00 55 ff ff ff ff
[   10.824923] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.824937] saa7133[0]: i2c eeprom 40: ff 21 00 c0 96 10 03 02 15 16 ff ff ff ff ff ff
[   10.824952] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.824966] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.824980] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.824994] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.825008] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.825022] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.825036] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.825050] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.825064] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.825078] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.825092] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   10.825113] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[   10.837400] ov519: Sensor is an OV7648
[   10.856603] gspca: probe ok
[   10.856636] gspca: probing 05a9:4519
[   10.856656] gspca: probing 05a9:4519
[   10.856695] usbcore: registered new interface driver ov519
[   10.856701] ov519: registered
[   10.972386] __ratelimit: 9 callbacks suppressed
[   10.972394] type=1505 audit(1257824472.531:14): operation="profile_replace" pid=742 name=/usr/share/gdm/guest-session/Xsession
[   10.982220] type=1505 audit(1257824472.539:15): operation="profile_replace" pid=743 name=/sbin/dhclient3
[   10.982738] type=1505 audit(1257824472.539:16): operation="profile_replace" pid=743 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.983031] type=1505 audit(1257824472.539:17): operation="profile_replace" pid=743 name=/usr/lib/connman/scripts/dhclient-script
[   11.016957] type=1505 audit(1257824472.575:18): operation="profile_replace" pid=746 name=/usr/bin/evince
[   11.027122] type=1505 audit(1257824472.582:19): operation="profile_replace" pid=746 name=/usr/bin/evince-previewer
[   11.033040] type=1505 audit(1257824472.590:20): operation="profile_replace" pid=746 name=/usr/bin/evince-thumbnailer
[   11.044883] type=1505 audit(1257824472.603:21): operation="profile_replace" pid=750 name=/usr/lib/cups/backend/cups-pdf
[   11.045546] type=1505 audit(1257824472.603:22): operation="profile_replace" pid=750 name=/usr/sbin/cupsd
[   11.050103] type=1505 audit(1257824472.607:23): operation="profile_replace" pid=751 name=/usr/sbin/mysqld
[   11.424996] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   11.540331] tuner 1-004b: chip found @ 0x96 (saa7133[0])
[   11.620026] tda829x 1-004b: setting tuner address to 60
[   11.665394] usbcore: registered new interface driver snd-usb-audio
[   11.786061] tda829x 1-004b: type set to tda8290+75a
[   15.704219] saa7133[0]: registered device video1 [v4l2]
[   15.704268] saa7133[0]: registered device vbi0
[   15.727979] saa7134 ALSA driver for DMA sound loaded
[   15.728035] IRQ 16/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   15.728077] saa7133[0]/alsa: saa7133[0] at 0xea800000 irq 16 registered as card -2
[   15.969524] dvb_init() allocating 1 frontend
[   16.187042] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   16.373620] __ratelimit: 9 callbacks suppressed
[   16.373628] type=1503 audit(1257824477.931:27): operation="open" pid=997 parent=996 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   16.385193] DVB: registering new adapter (saa7133[0])
[   16.385210] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   16.484036] tda1004x: setting up plls for 48MHz sampling clock
[   17.643637] type=1503 audit(1257824479.199:28): operation="open" pid=1183 parent=1009 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   17.787960] type=1503 audit(1257824479.343:29): operation="open" pid=1197 parent=1196 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   18.752087] tda1004x: timeout waiting for DSP ready
[   18.792045] tda1004x: found firmware revision 0 -- invalid
[   18.792055] tda1004x: trying to boot from eeprom
[   18.901527] type=1503 audit(1257824480.459:30): operation="open" pid=1232 parent=1231 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   19.936502] type=1503 audit(1257824481.494:31): operation="open" pid=1260 parent=1259 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   20.240023] 
[   20.240035] floppy driver state
[   20.240037] -------------------
[   20.240046] now=4294897356 last interrupt=4294892756 diff=4600 last called handler=e086a770
[   20.240052] timeout_message=lock fdc
[   20.240054] last output bytes:
[   20.240058]  8 80 4294892751
[   20.240061]  8 80 4294892751
[   20.240064]  8 80 4294892751
[   20.240067]  8 80 4294892756
[   20.240070]  8 80 4294892756
[   20.240073]  8 80 4294892756
[   20.240075]  8 80 4294892756
[   20.240078]  e 80 4294892756
[   20.240081] 13 80 4294892756
[   20.240084]  0 90 4294892756
[   20.240087] 1a 90 4294892756
[   20.240090]  0 90 4294892756
[   20.240093] 12 90 4294892756
[   20.240096]  0 90 4294892756
[   20.240099] 14 90 4294892756
[   20.240102] 18 80 4294892756
[   20.240105]  8 80 4294892756
[   20.240108]  8 80 4294892756
[   20.240111]  8 80 4294892756
[   20.240113]  8 80 4294892756
[   20.240116] last result at 4294892756
[   20.240119] last redo_fd_request at 4294892756
[   20.240122] 
[   20.240132] status=80
[   20.240134] fdc_busy=1
[   20.240138] floppy_work.func=e086e140
[   20.240140] cont=e0873c38
[   20.240143] current_req=(null)
[   20.240146] command_status=-1
[   20.240148] 
[   20.240155] floppy0: floppy timeout called
[   20.986889] type=1503 audit(1257824482.543:32): operation="open" pid=1272 parent=1271 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   21.120013] tda1004x: timeout waiting for DSP ready
[   21.160026] tda1004x: found firmware revision 0 -- invalid
[   21.160036] tda1004x: waiting for firmware upload...
[   21.160050] saa7134 0000:00:0d.0: firmware: requesting dvb-fe-tda10046.fw
[   22.299598] type=1503 audit(1257824483.855:33): operation="open" pid=1303 parent=1302 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   22.524243] type=1503 audit(1257824484.083:34): operation="open" pid=1324 parent=1323 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   26.268059] eth0: no IPv6 routers present
[   27.544107] tda1004x: setting up plls for 48MHz sampling clock
[   31.606836] tda1004x: timeout waiting for DSP ready
[   35.204015] tda1004x: found firmware revision 0 -- invalid
[   35.204024] tda1004x: trying to boot from eeprom
[   37.284015] tda1004x: timeout waiting for DSP ready
[   37.324011] tda1004x: found firmware revision 0 -- invalid
[   37.324016] tda1004x: firmware upload failed
[   37.592058] tda1004x: timeout waiting for DSP ready
[   37.637374] tda1004x: found firmware revision 80 -- invalid
[   37.637383] tda1004x: waiting for firmware upload...
[   37.637396] saa7134 0000:00:0d.0: firmware: requesting dvb-fe-tda10046.fw
[   38.224673] agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   38.224711] agpgart-via 0000:00:00.0: putting AGP V3 device into 8x mode
[   38.224775] pci 0000:01:00.0: putting AGP V3 device into 8x mode
[   38.506938] [drm] Setting GART location based on new memory map
[   38.506956] [drm] Loading R200 Microcode
[   38.507008] [drm] writeback test succeeded in 0 usecs
[   54.608012] tda1004x: timeout waiting for DSP ready
[   54.648010] tda1004x: found firmware revision 80 -- invalid
[   54.648015] tda1004x: firmware upload failed
[   65.838343] glxinfo:2107 freeing invalid memtype f8102000-f8112000
[   65.838360] glxinfo:2107 freeing invalid memtype f8112000-f8122000
[   65.838386] glxinfo:2107 freeing invalid memtype f8122000-f8132000
[   65.838399] glxinfo:2107 freeing invalid memtype f8132000-f8142000
[   65.838411] glxinfo:2107 freeing invalid memtype f8142000-f8152000
[   65.838422] glxinfo:2107 freeing invalid memtype f8152000-f8162000

```

I don't have time for experimenting now. I will come back later.

---

### Post by Jose Catre-Vandis on 2009-11-10
> **kem said:**
> According to my experience the good and quick method to test it is 
1) generate channels.conf using this command (use your country abbreviation instead of cz)
```
w_scan -c cz -X >> channels.conf
```
It takes several minutes but it should be done just one time.

2) play this channels.conf using vlc
```
vlc channels.conf
```

Get the same video artifacts and audio pops and clicks with vlc, so its not an "mplayer" only issue. But thanks for the vlc dvb howto :)

---

### Post by kem on 2009-11-10
I removed completely mythtv, restarted and ... BINGO - card is working. At least it is working in vlc.

Indeed, video is jerky (frequency 3-5x per minute). I am getting following messages during show ..
```

libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 13) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 1) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 6, expected 15) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 8) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 4, expected 3) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 3, expected 5) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 6, expected 5) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 12) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 0) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 4, expected 11) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 11, expected 5) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 4) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 4, expected 11) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 5) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 13) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 7) for PID 0
libdvbpsi error (PSI decoder): TS discontinuity (received 11, expected 10) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 13) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 2) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 0) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 10, expected 1) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 1, expected 12) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 5) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 15) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 6) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 7, expected 8) for PID 18
libdvbpsi error (misc PSI): Bad CRC_32 (0x3affd936) !!!
libdvbpsi error (PSI decoder): TS discontinuity (received 10, expected 9) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 7) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 14) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 15) for PID 18
libdvbpsi error (EIT decoder): 'version_number' differs whereas no discontinuity has occurred
libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 12) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 10) for PID 18
libdvbpsi error (EIT decoder): 'version_number' differs whereas no discontinuity has occurred
libdvbpsi error (PSI decoder): TS discontinuity (received 13, expected 5) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 6, expected 14) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 3) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 3, expected 13) for PID 18
libdvbpsi error (EIT decoder): 'version_number' differs whereas no discontinuity has occurred
libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 6) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 13) for PID 18
libdvbpsi error (EIT decoder): 'version_number' differs whereas no discontinuity has occurred
libdvbpsi error (PSI decoder): TS discontinuity (received 14, expected 6) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 6, expected 15) for PID 18
libdvbpsi error (EIT decoder): 'version_number' differs whereas no discontinuity has occurred
libdvbpsi error (EIT decoder): 'version_number' differs whereas no discontinuity has occurred
libdvbpsi error (PSI decoder): TS discontinuity (received 8, expected 10) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 11, expected 9) for PID 18
libdvbpsi error (PSI decoder): TS duplicate (received 6, expected 7) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 0, expected 12) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 1) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 9, expected 14) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 15, expected 10) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 5, expected 12) for PID 18
libdvbpsi error (PSI decoder): TS discontinuity (received 12, expected 6) for PID 18

```

---

### Post by Jose Catre-Vandis on 2009-11-11
Some additional - if I play live tv for a while, say five minutes or more, with mplayer it eventually gives up on the video leaving a static picture, although the audio continues.

---

### Post by Jose Catre-Vandis on 2009-11-21
Not getting any movement on this bug on launchpad - what next?

---

### Post by kem on 2009-11-21
My recent findings are:

1) Video quality is much more better on mythtv than on mplayer or vlc.
2) "tda1004x: firmware upload failed" issue can be temporary resolved by uninstalling and re-installing mythtv package. I filled a new bug report here [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/486264]("https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/486264")

---

### Post by Jose Catre-Vandis on 2009-11-21
So what is mythtv using to playback dvb tv. I thought it _was_ mplayer? If so, what is going on in mythtv that is different?

---

### Post by kem on 2009-11-22
> **Jose Catre-Vandis said:**
> So what is mythtv using to playback dvb tv. I thought it _was_ mplayer? If so, what is going on in mythtv that is different?

I believe mythtv has own rendering engine. 

BTW - I contacted dvb-fe-tda10046.fw firmware developer and he offered me a newer firmware v2.6 which should  be more stable at poor signals. If you want I will send you e-mail contact to him.

---

### Post by Jose Catre-Vandis on 2009-11-22
I stand corrected - myth does have its own interenal player - but you can point to an external player like mplayer or xine if you want to.

re updated firmware, sounds good - but the issue is that **I don't have a weak signal... on Jaunty/XP/7 on the same machine have perfect picture and audio**, only on Karmic do I experience weak signal characterstics and eventual mplayer crash. Anything is worth a try though, so when you get a copy of it, post it back here, or PM to me if preferred.

---

### Post by Emil Kjer on 2009-11-22
I've got the same error: [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/486264](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/486264)
It might be a problem with the distro...

---

### Post by Jose Catre-Vandis on 2009-11-24
Got excited, as a new kernel version 31.15 was available for download last night. A couple of references to saa7134 and dvb. I also installed x264, ffmpeg and mplayer from source. Unfortunatley the poor signal problem persists on Karmic.

---

### Post by Philip Farrugia on 2009-12-05
Just for info. But may help locate your issues.

I have ubuntu 9.10 and Kaffeine installed via synaptic with linux-firmware-nonfree and libxine1-all-plugins.  My Asus MyCinema-tv card works fine (unless I turn on the low energy light about 1 metre from an indoor ariel which scrambles the picture!).

My current problem since Karmic is when booting, most of the time booting halts for about 30secs with "waiting for tda1004x dsp timeout". so much for faster boot times!

---

### Post by Jose Catre-Vandis on 2009-12-30
Here is a workaround as posted by Vink on Launchpad:

[http://ubuntuforums.org/showthread.php?t=1327337](http://ubuntuforums.org/showthread.php?t=1327337)

---

### Post by Jose Catre-Vandis on 2009-12-30
Sorry to double post, but I may have an alternative solution. One of two things:

EITHER:
I installed linux dvb tv from source.

I grabbed **[v4l-dvb-9defbd461e5f.tar.gz]("http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz")** from linuxtv.org
and did the .configure, make and sudo make install on it. I went a bit over the top and chose to install everything.
(The version may be different now due to updates by developers)

This didn't work immediately, nor on reboot, in fact it killed my dvb completely.
But I revisited after a cold boot and I now get a perfect picture with no errors.

OR:
I did run another set of updates so this may also have had the same effect.

So not sure which one fixed it, but it is fixed, with no need to regress the kernel.

**[COLOR="Red"]EDIT (A BIG ONE!)[/COLOR]**

Sorry, its been a long day.

I do not believe it was either of the above that fixed it, but this did.

Insert this file [ATTACH]141816[/ATTACH] to /etc/udev/rules.d/

Reboot

Card working :)

The contents of the file are from [this]("http://ubuntuforums.org/showpost.php?p=8329657&postcount=6") post as linked to above

---

### Post by Eksilius on 2010-02-07
I tried your trick and so far, it seems to work. In my case the dsp timeout messages have ocurred kind of intermittently, so I'll have to use this setup for a while before I can tell for sure.

Another thing is that the boot screen messages (when I disable the "quiet" boot option) seem to be trying to tell me that this might not work for a future kernel release. Has anybody been running this with different kernels? I have 2.6.31-19.

---

### Post by L_V on 2010-02-28
Read this, it can help

[https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/486264](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/486264)

---

### Post by trazart on 2010-05-26
I could watch TV with Hardy but couldn't with Lucid so I mounted my Hardy partition, copied dvb-fe-tda10046.fw to /lib/firmware/ and ... bingo! Me-TV works again.

I have uploaded the file so you can get it ;)

---

### Post by justiceandfreedom on 2010-10-13
I have never used Myth TV, only vlc. I had two problems with Lucid: the timeout and the strange artifacts on screen. The timeout only happens at cold boot, when the firmware has to be uploaded; no problem at warm reboot. No more strange artifacts with Maverick, but I still have the timeout which causes a 30s freeze during startup. The things I tried:
1. Created /etc/udev/rules.d/50-udev.rules - did not help
2. Included saa7134-dvb in /etc/modules - it did not help, but at least the 30s freeze happens before the login screen shows up.
3. I blacklisted tda10046 and reloaded it in rc.local (/sbin/modprobe tda1004x /sbin/modprobe -r saa7134_dvb /sbin/modprobe saa7134_dvb), it did not help
4. I copied the tda10046.fw from archlinux AUR to /lib/firmware, it did not help, although it works in Archlinux. No problem with Fedora either.
5. I tried the test1 version of the new linux-firmware-nonfree1.10, it did not help
Any ideas?

---

### Post by kem on 2010-10-17
I cannot recommend to upgrade to Maverick. After upgrade my DVB-T card is no longer working

```

[   23.728072] tda1004x: timeout waiting for DSP ready
[   23.768046] tda1004x: found firmware revision 0 -- invalid
[   23.768056] tda1004x: waiting for firmware upload...
[   23.822744] tda1004x: no firmware upload (timeout or file not found?)
[   23.822755] tda1004x: firmware upload failed

```

My card is Avermedia AVerTV Super 007:
00:0d.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)


EDIT: I just forgot to install linux-firmware-nonfree. Now, it works (with Me TV).

---

