---
title: "Mythtv - no sound"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by Chuckels550 on 2007-07-10
I have rebuilt my Mythtv install twice, but I cannot get the sound to work on Mythtv.  I know the cabling is correct and the soundcard works because the Ubuntu theme plays just fine when the machine boots up. I have the machine set up with WinTV 350 tv out and everything else works fine.

AMD Athlon64 3500+
Creative Labs Soundblaster Live 24 bit
Hauppauge WinTV PVR 350, model 990 (NTSC tuner) 

When I run dmesg, I get the following:

A
[   31.077020] Probing IDE interface ide0...
[   31.364387] hda: Maxtor 6L250R0, ATA DISK drive
[   32.038912] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   32.061413] Probing IDE interface ide1...
[   32.343789] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc00007c8395]
[   32.799473] hdc: HL-DT-ST DVDRAM GSA-H10N, ATAPI CD/DVD-ROM drive
[   33.136393] ide1 at 0x170-0x177,0x376 on irq 15
[   33.145704] hda: max request size: 512KiB
[   33.152757] hda: 490234752 sectors (251000 MB) w/16384KiB Cache, CHS=30515/255/63, UDMA(133)
[   33.154307] hda: cache flushes supported
[   33.154344]  hda: hda1 hda2 hda3
[   33.176010] hdc: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(33)
[   33.176018] Uniform CD-ROM driver Revision: 3.20
[   33.387563] Attempting manual resume
[   33.387567] swsusp: Resume From Partition 3:2
[   33.387568] PM: Checking swsusp image.
[   33.399393] PM: Resume from disk failed.
[   33.431711] kjournald starting.  Commit interval 5 seconds
[   33.431722] EXT3-fs: mounted filesystem with ordered data mode.
[   39.206021] r8169: eth1: link down
[   39.223806] eth0: no link during initialization.
[   40.553838] NET: Registered protocol family 17
[   40.673576] Linux agpgart interface v0.102 (c) Dave Jones
[   40.703695] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   40.712648] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   40.922153] agpgart: Detected AGP bridge 0
[   40.922168] agpgart: Setting up Nforce3 AGP.
[   40.926108] agpgart: AGP aperture is 128M @ 0xe8000000
[   41.070876] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   41.070900] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   41.217784] usbcore: registered new interface driver xpad
[   41.217788] drivers/usb/input/xpad.c: driver for Xbox controllers v0.1.6
[   41.250429] ath_hal: module license 'Proprietary' taints kernel.
[   41.250996] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   41.600886] wlan: 0.8.4.2 (0.9.3.1)
[   41.630201] input: PC Speaker as /class/input/input3
[   41.637437] parport: PnPBIOS parport detected.
[   41.637482] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   41.649022] Linux video capture interface: v2.00
[   41.721222] ivtv:  ==================== START INIT IVTV ====================
[   41.721226] ivtv:  version 0.10.1 (tagged release) loading
[   41.721227] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586
[   41.721229] ivtv:  In case of problems please include the debug info between
[   41.721231] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   41.721233] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   41.721563] ivtv0: Autodetected Hauppauge card (cx23415 based)
[   41.724494] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   41.724505] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 22
[   41.724514] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   41.773683] ath_pci: 0.9.4.5 (0.9.3.1)
[   42.394595] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   42.416336] ivtv0: loaded v4l-cx2341x-dec.fw firmware (262144 bytes)
[   42.637145] ivtv0: Encoder revision: 0x02050032
[   42.637148] ivtv0: Recommended firmware version is 0x02060039.
[   42.645157] ivtv0: Decoder revision: 0x02020023
[   42.712183] tveeprom 2-0050: Hauppauge model 48132, rev K168, serial# 8809696
[   42.712187] tveeprom 2-0050: tuner model is LG TAPE H001F MK3 (idx 68, type 47)
[   42.712190] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   42.712192] tveeprom 2-0050: audio processor is MSP4448 (idx 27)
[   42.712194] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[   42.712196] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[   42.712199] ivtv0: Autodetected Hauppauge WinTV PVR-350
[   42.735693] tuner 2-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   42.735720] tda9887 2-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   42.740176] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   42.819667] saa7115 2-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   43.056986] saa7127 2-0044: saa7127 found @ 0x88 (ivtv i2c driver #0)
[   43.081158] msp3400 2-0040: MSP4448G-B3 found @ 0x80 (ivtv i2c driver #0)
[   43.081162] msp3400 2-0040: MSP4448G-B3 supports radio, mode is autodetect and autoselect
[   43.081367] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   43.081504] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   43.081669] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   43.081732] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   43.081902] ivtv0: Registered device radio0 for encoder radio
[   43.081920] ivtv0: Registered device video16 for decoder MPEG (1 MB)
[   43.081960] ivtv0: Registered device vbi8 for decoder VBI (1 MB)
[   43.082240] ivtv0: Registered device vbi16 for decoder VOUT
[   43.082259] ivtv0: Registered device video48 for decoder YUV (1 MB)
[   43.148011] ivtv0: loaded v4l-cx2341x-init.mpg firmware (155648 bytes)
[   43.252801] tuner 2-0061: type set to 47 (LG NTSC (TAPE series))
[   43.661675] ivtv0: Initialized Hauppauge WinTV PVR-350, card #0
[   43.661691] ivtv:  ====================  END INIT IVTV  ====================
[   43.663340] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 20
[   44.283469] ath_rate_sample: 1.2 (0.9.3.1)
[   44.283696] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   44.283701] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   44.283708] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   44.283713] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   44.283716] wifi0: mac 7.9 phy 4.5 radio 5.6
[   44.283719] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   44.283721] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   44.283722] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   44.283724] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   44.283726] wifi0: Use hw queue 8 for CAB traffic
[   44.283727] wifi0: Use hw queue 9 for beacons
[   44.298493] wifi0: Atheros 5212: mem=0xfdfe0000, irq=20
[   44.298848] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   44.298857] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 23
[   44.298878] snd-ca0106: Model 1006 Rev 00000000 Serial 10061102
[   44.473549] fuse init (API version 7.8)
[   44.509783] lp0: using parport0 (interrupt-driven).
[   44.525650] NET: Registered protocol family 10
[   44.525736] lo: Disabled Privacy Extensions
[   44.525788] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.525790] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   44.832707] w83627hf 9191-0290: Reading VID from GPIO5
[   44.859778] ivtv0-fb: Framebuffer at 0xf5510000, mapped to 0xf9990000, size 1665k
[   44.936585] ivtv0-fb: === Validated display mode  ===
[   44.936593] ivtv0-fb: Display size 720x480 (720x480 Virtual) @ 32bpp
[   44.936595] ivtv0-fb: Display position 1,1
[   44.936597] ivtv0-fb: Display filter : on
[   44.936598] ivtv0-fb: Color space : RGB
[   44.939403] Console: switching to colour frame buffer device 90x30
[   44.975336] ivtv0-fb: === Display mode change ===
[   44.975339] ivtv0-fb: Display size 720x480 (720x480 Virtual) @ 32bpp
[   44.975341] ivtv0-fb: Display position 1,1
[   44.975343] ivtv0-fb: Display filter : on
[   44.975344] ivtv0-fb: Color space : RGB
[   44.983701] ivtv0-fb: Running in compatibility mode. Display resize & mode change disabled
[   44.999679] ivtv0-fb: Framebuffer registered on ivtv card id 0
[   45.029526] Adding 4883752k swap on /dev/disk/by-uuid/c2108504-e91f-4d64-8ddf-09bd3ef002b4.  Priority:-1 extents:1 across:4883752k
[   45.125460] EXT3 FS on hda1, internal journal
[   45.298432] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[   45.298575] SGI XFS Quota Management subsystem
[   45.325169] XFS mounting filesystem hda3
[   45.457902] Ending clean XFS mount for filesystem: hda3
[   55.285068] ath0: no IPv6 routers present
[   56.809609] eth0: no link during initialization.
[   56.810613] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   62.999776] ivtv0-fb: === Validated display mode  ===
[   62.999780] ivtv0-fb: Display size 720x480 (720x480 Virtual) @ 32bpp
[   62.999782] ivtv0-fb: Display position 1,1
[   62.999783] ivtv0-fb: Display filter : on
[   62.999785] ivtv0-fb: Color space : RGB
[   63.024191] ivtv0-fb: === Display mode change ===
[   63.024193] ivtv0-fb: Display size 720x480 (720x480 Virtual) @ 32bpp
[   63.024195] ivtv0-fb: Display position 1,1
[   63.024196] ivtv0-fb: Display filter : on
[   63.024197] ivtv0-fb: Color space : RGB
[   70.673227] r8169: eth1: link down
[   70.673249] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   93.230220] ibm_acpi: ec object not found
[   93.291004] No dock devices found.
[   93.342169] input: Power Button (FF) as /class/input/input4
[   93.345927] ACPI: Power Button (FF) [PWRF]
[   93.376429] input: Power Button (CM) as /class/input/input5
[   93.380116] ACPI: Power Button (CM) [PWRB]
[   93.394275] Using specific hotkey driver
[   93.485107] pcc_acpi: loading...
[   93.856448] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ processors (version 2.00.00)
[   93.863704] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   98.325319] ivtv0-fb: === Validated display mode  ===
[   98.325323] ivtv0-fb: Display size 720x480 (720x480 Virtual) @ 32bpp
[   98.325325] ivtv0-fb: Display position 1,1
[   98.325327] ivtv0-fb: Display filter : on
[   98.325328] ivtv0-fb: Color space : RGB
[   98.332515] ivtv0-fb: === Validated display mode  ===
[   98.332518] ivtv0-fb: Display size 720x480 (720x480 Virtual) @ 32bpp
[   98.332519] ivtv0-fb: Display position 1,1
[   98.332521] ivtv0-fb: Display filter : on
[   98.332522] ivtv0-fb: Color space : RGB
[   98.357611] ppdev: user-space parallel port driver
[   98.357687] ivtv0-fb: === Display mode change ===
[   98.357689] ivtv0-fb: Display size 720x480 (720x480 Virtual) @ 32bpp
[   98.357691] ivtv0-fb: Display position 1,1
[   98.357693] ivtv0-fb: Display filter : on
[   98.357694] ivtv0-fb: Color space : RGB
[   99.340166] lirc_dev: IR Remote Control driver registered, at major 61
[   99.342778] lirc_i2c: no version for "lirc_unregister_plugin" found: kernel tainted.
[   99.406289] bttv: driver version 0.9.16 loaded
[   99.406294] bttv: using 8 buffers with 2080k (520 pages) each for capture
[   99.448650] cx2388x v4l2 driver version 0.0.6 loaded
[   99.451932] lirc_i2c: chip found @ 0x18 (Hauppauge IR)
[   99.452225] lirc_dev: lirc_register_plugin: sample_rate: 10
[  101.399686] ath0: no IPv6 routers present
[  102.623037] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[  102.623042] apm: overridden by ACPI.
[  109.289591] Bluetooth: Core ver 2.11
[  109.289640] NET: Registered protocol family 31
[  109.289642] Bluetooth: HCI device and connection manager initialized
[  109.289645] Bluetooth: HCI socket layer initialized
[  109.386714] Bluetooth: L2CAP ver 2.8
[  109.386718] Bluetooth: L2CAP socket layer initialized
[  109.513416] Bluetooth: RFCOMM socket layer initialized
[  109.513429] Bluetooth: RFCOMM TTY layer initialized
[  109.513431] Bluetooth: RFCOMM ver 1.8
[  156.853998] ivtv0: Stereo mode changed
[  249.993751] ivtv0 warning: CX2341X_DEC_GET_TIMING_INFO took 35 jiffies (250 per HZ)
[  250.152349] ivtv0: Stereo mode changed
[  286.657628] ivtv0 warning: IVTV_IOC_DEC_FLUSH is obsolete!
[  287.548413] ivtv0: Stereo mode changed
[  300.317053] ivtv0 warning: IVTV_IOC_DEC_FLUSH is obsolete!
[  300.552825] ivtv0: Stereo mode changed
[  359.969328] ivtv0 warning: CX2341X_DEC_EXTRACT_VBI took 32 jiffies (250 per HZ)
[  360.156351] ivtv0: Stereo mode changed
[  546.450366] ivtv0 warning: CX2341X_DEC_GET_TIMING_INFO took 35 jiffies (250 per HZ)
[  546.652860] ivtv0: Stereo mode changed
[  849.321914] ivtv0: Stereo mode changed
[  873.843610] ivtv0 warning: IVTV_IOC_DEC_FLUSH is obsolete!
[  874.113641] ivtv0: Stereo mode changed
edowd@mythtv-host:~$

I have changed the cabling for mythtv so that instead of using my soundcard, I cable the audio directly from the TV card and to the TV.  The original cabling was from the TV card output to the soundcard input and then from the sound card to the TV.  The sound now works, but only for live TV and for playing back recorded TV.  I have MythTV set up so that DVD playback is through xine and it no longer works.

---

### Post by Chuckels550 on 2007-09-13
Issue resolved - the problem had nothing to do with IVTV.  The problem was caused by the audio system on my platform.  I re-installed the soundcard and configured ALSA (the default was mute with only the mic/line-in enabled).  

My cabling changed to cable the PVR 350 audio out from the cable backpanel connector to the soundcard mic/line-in and then from the soundcard to the TV.

---

