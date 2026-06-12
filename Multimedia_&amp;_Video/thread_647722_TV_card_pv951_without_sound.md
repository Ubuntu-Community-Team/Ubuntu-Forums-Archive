---
title: "TV card pv951 without sound"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by kolage on 2007-12-22
Hi,

I have this problem... I have TV card Mediaforte PV-951 in Ubuntu 7.10. I was following some guides I've found and did this:

modprobe bttv card=42 tuner=5 radio=1

So in tvtime i've tuned all programs I needed without any problems, but problem is with sound which don't work. I have cable connected from audio-out in TV card to LINE-IN in my sound card. I've looked if I have something MUTE in alsa-mixer, but I haven't. I have got also checked capture from line-in (not from mic). And if i connect my headphones straight to the tv card, there isn't any sound too.

There is my dmesg output: 
```

[   34.550051] bttv: driver version 0.9.17 loaded
[   34.550057] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   34.550130] bttv: Bt8xx card found (0).
[   34.550161] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 19 (level, low) -> IRQ 19
[   34.550173] bttv0: Bt878 (rev 17) at 0000:00:0b.0, irq: 19, latency: 32, mmio: 0xea000000
[   34.550182] bttv0: using: ProVideo PV951 [card=42,insmod option]
[   34.550221] bttv0: gpio: en=00000000, out=00000000 in=00ffffff [init]
[   34.920824] hda: max request size: 128KiB
[   34.978225] hda: Host Protected Area detected.
[   34.978228]  current capacity is 58631231 sectors (30019 MB)
[   34.978229]  native  capacity is 58633344 sectors (30020 MB)
[   34.978402] bttv0: using tuner=5
[   34.978406] bttv0: i2c: checking for TDA9875 @ 0xb0... <6>hda: Host Protected Area disabled.
[   35.078889] hda: 58633344 sectors (30020 MB) w/512KiB Cache, CHS=58168/16/63, UDMA(100)
[   35.078897] hda: cache flushes not supported
[   35.078961]  hda: hda1
[   35.207304] hdb: max request size: 512KiB
[   35.437948] hdb: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   35.513320] usbcore: registered new interface driver hiddev
[   35.528758] input: Chicony USB Keyboard as /class/input/input1
[   35.528810] input: USB HID v1.10 Keyboard [Chicony USB Keyboard] on usb-0000:00:10.3-1
[   35.565494] input: Chicony USB Keyboard as /class/input/input2
[   35.565631] input,hiddev96: USB HID v1.10 Device [Chicony USB Keyboard] on usb-0000:00:10.3-1
[   35.579634] input: A4Tech Wireless Battery Free Optical Mouse as /class/input/input3
[   35.579706] input: USB HID v1.10 Mouse [A4Tech Wireless Battery Free Optical Mouse] on usb-0000:00:10.3-2
[   35.579725] usbcore: registered new interface driver usbhid
[   35.579730] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   35.581206] hdb: cache flushes supported
[   35.581286]  hdb:<6>input: PC Speaker as /class/input/input4
[   35.674292] usbcore: registered new interface driver xpad
[   35.674299] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   35.696629]  hdb1
[   35.696965] not found
[   35.696969] bttv0: i2c: checking for TDA7432 @ 0x8a... <6>hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   35.711521] Uniform CD-ROM driver Revision: 3.20
[   35.724745] hdd: max request size: 512KiB
[   35.731403] hdd: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
[   35.736625] hdd: cache flushes supported
[   35.736695]  hdd:not found
[   35.756386]  hdd1
[   35.778568] parport_pc 00:0b: reported by Plug and Play ACPI
[   35.778614] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   36.346313] bttv0: i2c: checking for TDA9887 @ 0x86... not found
[   36.374655] i2c-adapter i2c-0: sendbytes: error - bailout.
[   36.375244] i2c-adapter i2c-0: sendbytes: error - bailout.
[   36.376716] tuner 0-004b: chip found @ 0x96 (bt878 #0 [sw])
[   36.376756] tda9887 0-004b: tda988[5/6/7] found @ 0x4b (tuner)
[   36.377712] tuner 0-0060: All bytes are equal. It is not a TEA5767
[   36.377714] tuner 0-0060: chip found @ 0xc0 (bt878 #0 [sw])
[   36.377728] tuner 0-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   36.377731] tuner 0-0060: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   36.385749] bttv0: registered device video0
[   36.385783] bttv0: registered device vbi0
[   36.385816] bttv0: registered device radio0
[   36.385837] bttv0: PLL: 28636363 => 35468950 .. ok
[   36.417821] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 20
[   36.418927] mpu401_uart: unable to grab port 0x330 size 2
[   36.418937] cmipci: no UART401 device at 0x330
[   36.440592] bt878: AUDIO driver version 0.0.0 loaded
[   36.440643] bt878: Bt878 AUDIO function found (0).
[   36.440664] ACPI: PCI Interrupt 0000:00:0b.1[A] -> GSI 19 (level, low) -> IRQ 19
[   36.440671] bt878_probe: card id=[0x0], Unknown card.
[   36.440673] Exiting..
[   36.440677] ACPI: PCI interrupt for device 0000:00:0b.1 disabled
[   36.440682] bt878: probe of 0000:00:0b.1 failed with error -22
[   37.117134] lp0: using parport0 (interrupt-driven).
[   37.171626] Adding 1244996k swap on /dev/sda5.  Priority:-1 extents:1 across:1244996k
[   37.191954] Adding 1020088k swap on /dev/sda6.  Priority:-2 extents:1 across:1020088k
[   37.727942] EXT3 FS on sda8, internal journal
[   39.091802] kjournald starting.  Commit interval 5 seconds
[   39.091959] EXT3 FS on sda9, internal journal
[   39.091966] EXT3-fs: mounted filesystem with ordered data mode.
[   39.417093] kjournald starting.  Commit interval 5 seconds
[   39.417249] EXT3 FS on sda1, internal journal
[   39.417255] EXT3-fs: mounted filesystem with ordered data mode.
[   39.442502] kjournald starting.  Commit interval 5 seconds
[   39.442650] EXT3 FS on sda10, internal journal
[   39.442656] EXT3-fs: mounted filesystem with ordered data mode.
[   41.959636] No dock devices found.
[   42.048869] input: Power Button (FF) as /class/input/input5
[   42.054377] ACPI: Power Button (FF) [PWRF]
[   42.088381] input: Power Button (CM) as /class/input/input6
[   42.093869] ACPI: Power Button (CM) [PWRB]
[   43.573773] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1
[   43.875524] NET: Registered protocol family 10
[   43.875740] lo: Disabled Privacy Extensions
[   44.547443] ppdev: user-space parallel port driver
[   44.687152] audit(1197743137.648:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4854 profile="/usr/sbin/cupsd"
[   46.515472] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   46.515479] apm: overridden by ACPI.
[   46.894052] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   47.053496] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   47.076245] NFSD: starting 90-second grace period
[   47.784895] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   47.784902] vboxdrv: Successfully done.
[   48.437636] Failure registering capabilities with primary security module.
[   50.275074] Bluetooth: Core ver 2.11
[   50.275226] NET: Registered protocol family 31
[   50.275229] Bluetooth: HCI device and connection manager initialized
[   50.275234] Bluetooth: HCI socket layer initialized
[   50.325520] Bluetooth: L2CAP ver 2.8
[   50.325526] Bluetooth: L2CAP socket layer initialized
[   50.584458] Bluetooth: RFCOMM socket layer initialized
[   50.584568] Bluetooth: RFCOMM TTY layer initialized
[   50.584571] Bluetooth: RFCOMM ver 1.8
[   52.763117] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   52.768866] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[   52.769231] [fglrx] module loaded - fglrx 8.37.6 [May 25 2007] on minor 0
[   53.010556] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   53.253816] NET: Registered protocol family 17
[   56.129007] /dev/vmmon[5873]: VMCI: Driver initialized.
[   56.132324] /dev/vmmon[5873]: Module vmmon: registered with major=10 minor=165
[   56.132674] /dev/vmmon[5873]: Initial HV check: anyNotCapable=1 anyUnlocked=0 anyEnabled=0 anyDisabled=0
[   56.132679] /dev/vmmon[5873]: Module vmmon: initialized
[   56.165703] [fglrx] Internal AGP support requested, but kernel AGP support active.
[   56.165712] [fglrx] Have to use kernel AGP support to avoid conflicts.
[   56.165717] [fglrx] AGP detected, AgpState   = 0x1f000a1b (hardware caps of chipset)
[   56.166501] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   56.166699] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   56.166926] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   56.167157] [fglrx] AGP enabled,  AgpCommand = 0x1f000312 (selected caps)
[   56.177179] [fglrx] total      GART = 134217728
[   56.177189] [fglrx] free       GART = 118222848
[   56.177192] [fglrx] max single GART = 118222848
[   56.177194] [fglrx] total      LFB  = 134217728
[   56.177196] [fglrx] free       LFB  = 116002816
[   56.177198] [fglrx] max single LFB  = 116002816
[   56.177200] [fglrx] total      Inv  = 134217728
[   56.177202] [fglrx] free       Inv  = 134217728
[   56.177203] [fglrx] max single Inv  = 134217728
[   56.177205] [fglrx] total      TIM  = 0
[   56.864141] /dev/vmnet: open called by PID 5918 (vmnet-bridge)
[   56.864515] /dev/vmnet: hub 0 does not exist, allocating memory.
[   56.864696] /dev/vmnet: port on hub 0 successfully opened
[   56.864870] bridge-eth0: enabling the bridge
[   56.865021] bridge-eth0: up
[   56.865144] bridge-eth0: already up
[   56.865149] bridge-eth0: attached
[   57.644474] /dev/vmnet: open called by PID 5934 (vmnet-dhcpd)
[   57.644705] /dev/vmnet: hub 1 does not exist, allocating memory.
[   57.644888] /dev/vmnet: port on hub 1 successfully opened
[   57.680082] /dev/vmnet: open called by PID 5947 (vmnet-dhcpd)
[   57.680317] /dev/vmnet: hub 8 does not exist, allocating memory.
[   57.680507] /dev/vmnet: port on hub 8 successfully opened
[   57.708701] /dev/vmnet: open called by PID 5952 (vmnet-natd)
[   57.709017] /dev/vmnet: port on hub 8 successfully opened
[   65.835696] eth0: no IPv6 routers present
[   67.621926] /dev/vmnet: open called by PID 6172 (vmnet-netifup)
[   67.621949] /dev/vmnet: port on hub 1 successfully opened
[   67.647913] /dev/vmnet: open called by PID 6183 (vmnet-netifup)
[   67.648038] /dev/vmnet: port on hub 8 successfully opened
[   78.370107] vmnet8: no IPv6 routers present
[   78.550021] vmnet1: no IPv6 routers present
[   91.316248] i2c-adapter i2c-0: sendbytes: error - bailout.
[   91.316273] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  132.881401] i2c-adapter i2c-0: sendbytes: error - bailout.
[  132.881427] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  132.883272] i2c-adapter i2c-0: sendbytes: error - bailout.
[  132.883290] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  132.883652] i2c-adapter i2c-0: sendbytes: error - bailout.
[  132.883671] tuner 0-0060: i2c i/o error: rc == -14 (should be 4)
[  134.201094] tda9887 0-004b: i2c i/o error: rc == -121 (should be 4)
[  134.201426] i2c-adapter i2c-0: sendbytes: error - bailout.
[  134.201446] tuner 0-0060: i2c i/o error: rc == -14 (should be 4)
[  134.201837] i2c-adapter i2c-0: sendbytes: error - bailout.
[  134.201855] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  134.920761] i2c-adapter i2c-0: sendbytes: error - bailout.
[  134.920786] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  134.922359] i2c-adapter i2c-0: sendbytes: error - bailout.
[  134.922377] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  135.480260] i2c-adapter i2c-0: sendbytes: error - bailout.
[  135.480286] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  135.482088] tda9887 0-004b: i2c i/o error: rc == -121 (should be 4)
[  136.000378] i2c-adapter i2c-0: sendbytes: error - bailout.
[  136.000406] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  136.001970] i2c-adapter i2c-0: sendbytes: error - bailout.
[  136.001988] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  136.002368] i2c-adapter i2c-0: sendbytes: error - bailout.
[  136.002386] tuner 0-0060: i2c i/o error: rc == -14 (should be 4)
[  136.519884] i2c-adapter i2c-0: sendbytes: error - bailout.
[  136.519910] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  136.520360] i2c-adapter i2c-0: sendbytes: error - bailout.
[  136.520378] tuner 0-0060: i2c i/o error: rc == -14 (should be 4)
[  136.520754] i2c-adapter i2c-0: sendbytes: error - bailout.
[  136.520772] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  143.317383] i2c-adapter i2c-0: sendbytes: error - bailout.
[  143.317408] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  143.319201] tda9887 0-004b: i2c i/o error: rc == -121 (should be 4)
[  144.277221] i2c-adapter i2c-0: sendbytes: error - bailout.
[  144.277247] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  144.277644] i2c-adapter i2c-0: sendbytes: error - bailout.
[  144.277662] tuner 0-0060: i2c i/o error: rc == -14 (should be 4)
[  144.278054] i2c-adapter i2c-0: sendbytes: error - bailout.
[  144.278071] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  145.276655] i2c-adapter i2c-0: sendbytes: error - bailout.
[  145.276681] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)
[  145.277126] i2c-adapter i2c-0: sendbytes: error - bailout.
[  145.277145] tuner 0-0060: i2c i/o error: rc == -14 (should be 4)
[  145.278202] i2c-adapter i2c-0: sendbytes: error - bailout.
[  145.278221] tda9887 0-004b: i2c i/o error: rc == -14 (should be 4)


```

Please, have anyone some idea? Thanks in advance for any reply.

P.S. Sorry for my bad english, I am czech :-)

---

### Post by reidy90 on 2007-12-23
I have a Leadtek Winfast 2000xp which is based on the same chipset as yours and had a similar problem.

Right click the speaker icon in the top right corner of the screen.
Click Open volume control. Leave the line in muted. 
Click file, change device, and there should be an option like "Brooktree bt878". Select it. 
Tick the box marked line in. 

It should be all good now.

---

### Post by kolage on 2007-12-23
Unfortunately, I haven't got any "Brooktree" menu item there :-(

---

### Post by stager on 2007-12-27
Hi!

 I have the same tv-card (MediaForte PV951) and the same problem - no sound. Yesterday I solved a problem using "i2c_udelay=128" paremeter for bttv module. You can find more complete answer here:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29789/comments/40]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/29789/comments/40")

 Hope this helps...

---

### Post by kolage on 2007-12-27
thanks a lot. now it works perfectly !!! =D>

---

### Post by hasplu on 2008-03-19
hey,

worked perfectly for my hercules smart tv 2 stereo :lolflag:

thanks alot, man, 2 days trying to fix this :)

cheers !!!!!!!!!

---

