---
title: "Problem with Azalia audio"
date: 2006-05-23
forum: Multimedia &amp; Video
---

### Post by bjtuna on 2006-05-23
On my AMD64 system with Azalia HD audio I am seeing difficulties getting sound to work. To preface this, note that I had to go through some contortions when I first installed Breezy because it was hanging at the 'Starting Hotplug Subsystem', and these things caused the system to boot properly:
```


You need to blacklist the snd-hda-intel kernel module from being
loaded automatically by appending it to /etc/hotplug/blacklist .

From a clean boot, make sure the universe repository is enabled, then:

$ sudo apt-get install build-essential gcc-3.4 linux-headers-$(uname -r) module-assistant
$ wget http://archive.ubuntu.com/ubuntu/pool/universe/a/alsa-driver/alsa-source_1.0.10-3_all.deb && sudo dpkg -i alsa-source_1.0.10-3_all.deb ; sudo apt-get -f install
$ sudo dpkg-reconfigure alsa-source

Choose "Yes" for both Plug n' play support and debugging symbols, then
deselect "all" cards and select only "hda-intel". Then:

$ sudo module-assistant a-i alsa-source

At this point you'll need to remove snd-hda-intel from
/etc/hotplug/blacklist , and reboot. 

```

However now, everything but sound works. Here are my symptoms:

```

root@surreal:~# alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument

```

```

root@surreal:~# /etc/init.d/alsa-utils restart
 * Shutting down ALSA...  * /etc/init.d/alsa-utils: Warning: 'alsactl store' failed with error message 'alsactl: get_control:149: Cannot read control info '2,0,0,Front Playback Volume,0': Invalid argument'.
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
                                                                                                                                                     [fail]
 * Setting up ALSA... amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument
amixer: Mixer hw:0 load error: Invalid argument

```

```

root@surreal:~# dmesg
w) -> IRQ 19
[  192.274288] ohci_hcd 0000:00:13.1: PCI device 1002:4375 (ATI Technologies Inc)
[  192.295268] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[  192.295273] ohci_hcd 0000:00:13.1: irq 19, io mem 0xfe9f9000
[  192.350196] hub 2-0:1.0: USB hub found
[  192.350207] hub 2-0:1.0: 4 ports detected
[  192.363732] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19
[  192.363748] ehci_hcd 0000:00:13.2: PCI device 1002:4373 (ATI Technologies Inc)
[  192.363796] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[  192.363803] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfe9f8000
[  192.363841] ehci_hcd 0000:00:13.2: USB 2.0 initialized, EHCI 1.00, driver 10 Dec 2004
[  192.363904] hub 3-0:1.0: USB hub found
[  192.363911] hub 3-0:1.0: 8 ports detected
[  192.427807] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 20 (level, low) -> IRQ 20
[  192.427813] 3c59x: Donald Becker and others. www.scyld.com/network/vortex.html
[  192.427818] 0000:02:00.0: 3Com PCI 3c905C Tornado at 0xe800. Vers LK1.1.19
[  192.455628] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[  192.455656] 8139cp: pci dev 0000:02:03.0 (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[  192.455659] 8139cp: Try the "8139too" driver instead.
[  192.457366] 8139too Fast Ethernet driver 0.9.27
[  192.457408] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 20 (level, low) -> IRQ 20
[  192.458037] eth1: RealTek RTL8139 at 0xffffc20000048800, 00:13:d3:de:f3:ee, IRQ 20
[  192.458040] eth1:  Identified 8139 chip type 'RTL-8100B/8139D'
[  194.789200] ACPI: CPU0 (power states: C1[C1])
[  194.948932] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[  194.979803] cdrom: open failed.
[  195.054800] Attempting manual resume
[  195.073479] swsusp: Suspend partition has wrong signature?
[  195.097561] kjournald starting.  Commit interval 5 seconds
[  195.097569] EXT3-fs: mounted filesystem with ordered data mode.
[  196.376716] md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
[  199.479338] Adding 839672k swap on /dev/mapper/Ubuntu-swap_1.  Priority:-1 extents:1
[  199.733183] EXT3 FS on dm-0, internal journal
[  204.354747] APIC error on CPU0: 00(40)
[  207.334521] parport: PnPBIOS parport detected.
[  207.334586] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  207.420263] lp0: using parport0 (interrupt-driven).
[  207.438020] mice: PS/2 mouse device common for all mice
[  207.467105] Real Time Clock Driver v1.12
[  207.478511] ieee1394: Initialized config rom entry `ip1394'
[  207.482506] sbp2: $Rev: 1219 $ Ben Collins <bcollins@debian.org>
[  207.638166] logips2pp: Detected unknown logitech mouse model 86
[  207.683314] input: ImExPS/2 Logitech Explorer Mouse on isa0060/serio1
[  208.134312] ts: Compaq touchscreen protocol output
[  211.279668] cdrom: open failed.
[  212.028887] kjournald starting.  Commit interval 5 seconds
[  212.029883] EXT3 FS on hda1, internal journal
[  212.029888] EXT3-fs: mounted filesystem with ordered data mode.
[  214.161124] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  214.170085] shpchp: shpc_init : shpc_cap_offset == 0
[  214.170095] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  214.706740] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16
[  214.712161] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:633: codec_mask = 0x8
[  214.724148] hda_codec: Unknown model for ALC880, trying auto-probe from BIOS...
[  214.952886] hda_codec: num_steps = 0 for NID=0x8
[  215.375426] hda_codec: num_steps = 0 for NID=0xb
[  215.378847] hda_codec: num_steps = 0 for NID=0xb
[  215.383260] hda_codec: num_steps = 0 for NID=0xb
[  215.387664] hda_codec: num_steps = 0 for NID=0xb
[  215.392071] hda_codec: num_steps = 0 for NID=0xb
[  215.396618] hda_codec: num_steps = 0 for NID=0xb
[  215.400979] hda_codec: num_steps = 0 for NID=0xb
[  215.405335] hda_codec: num_steps = 0 for NID=0xb
[  215.409724] hda_codec: num_steps = 0 for NID=0xb
[  215.414103] hda_codec: num_steps = 0 for NID=0xb
[  215.418516] hda_codec: num_steps = 0 for NID=0xb
[  215.422895] hda_codec: num_steps = 0 for NID=0xb
[  215.427307] hda_codec: num_steps = 0 for NID=0xb
[  215.431713] hda_codec: num_steps = 0 for NID=0xb
[  215.436110] hda_codec: num_steps = 0 for NID=0xb
[  215.440549] hda_codec: num_steps = 0 for NID=0xb
[  215.444950] hda_codec: num_steps = 0 for NID=0xb
[  215.449343] hda_codec: num_steps = 0 for NID=0xb
[  216.101642] ohci1394: $Rev: 1250 $ Ben Collins <bcollins@debian.org>
[  216.101666] ACPI: PCI Interrupt 0000:02:04.0[A] -> GSI 21 (level, low) -> IRQ 21
[  216.101674] PCI: Via IRQ fixup for 0000:02:04.0, from 9 to 5
[  216.157781] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[febff000-febff7ff]  Max Packet=[2048]
[  217.420937] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0010dc0000dd5392]
[  217.517045] input: PC Speaker
[  217.571146] Floppy drive(s): fd0 is 1.44M
[  217.640645] FDC 0 is a post-1991 82077
[  218.775050] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  219.870827] hda_codec: num_steps = 0 for NID=0xb
[  219.875035] hda_codec: num_steps = 0 for NID=0xb
[  219.879214] hda_codec: num_steps = 0 for NID=0xb
[  219.883406] hda_codec: num_steps = 0 for NID=0xb
[  219.887586] hda_codec: num_steps = 0 for NID=0xb
[  219.891793] hda_codec: num_steps = 0 for NID=0xb
[  219.895978] hda_codec: num_steps = 0 for NID=0xb
[  219.900434] hda_codec: num_steps = 0 for NID=0xb
[  219.904437] hda_codec: num_steps = 0 for NID=0xb
[  219.908579] hda_codec: num_steps = 0 for NID=0xb
[  219.912714] hda_codec: num_steps = 0 for NID=0xb
[  219.916877] hda_codec: num_steps = 0 for NID=0xb
[  219.921015] hda_codec: num_steps = 0 for NID=0xb
[  219.925158] hda_codec: num_steps = 0 for NID=0xb
[  219.929269] hda_codec: num_steps = 0 for NID=0xb
[  219.933445] hda_codec: num_steps = 0 for NID=0xb
[  219.937560] hda_codec: num_steps = 0 for NID=0xb
[  219.941725] hda_codec: num_steps = 0 for NID=0xb
[  220.834626] NET: Registered protocol family 10
[  220.834714] Disabled Privacy Extensions on device ffffffff8035a840(lo)
[  220.834832] IPv6 over IPv4 tunneling driver
[  222.594629] ACPI: Power Button (FF) [PWRF]
[  222.594658] ACPI: Power Button (CM) [PWRB]
[  222.672053] ibm_acpi: ec object not found
[  229.673024] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[  229.677276] [fglrx] Maximum main memory to use for locked dma buffers: 1820 MBytes.
[  229.677299] ACPI: PCI Interrupt 0000:01:05.0[A] -> GSI 17 (level, low) -> IRQ 17
[  229.677337] [fglrx] module loaded - fglrx 8.16.20 [Aug 16 2005] on minor 0
[  229.696115] [fglrx] free  PCIe = 54804480
[  229.696120] [fglrx] max   PCIe = 54804480
[  229.696123] [fglrx] free  LFB = 49213440
[  229.696125] [fglrx] max   LFB = 49213440
[  229.696128] [fglrx] free  Inv = 0
[  229.696130] [fglrx] max   Inv = 0
[  229.696132] [fglrx] total Inv = 0
[  229.696134] [fglrx] total TIM = 0
[  229.696136] [fglrx] total FB  = 0
[  229.696139] [fglrx] total PCIe = 16384
[  231.233736] eth0: no IPv6 routers present
[  232.774146] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.40.4)
[  232.780332] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[  233.765203] Bluetooth: Core ver 2.7
[  233.765209] NET: Registered protocol family 31
[  233.765212] Bluetooth: HCI device and connection manager initialized
[  233.765224] Bluetooth: HCI socket layer initialized
[  233.834734] Bluetooth: L2CAP ver 2.7
[  233.834738] Bluetooth: L2CAP socket layer initialized
[  233.883748] Bluetooth: RFCOMM ver 1.5
[  233.883757] Bluetooth: RFCOMM socket layer initialized
[  233.883769] Bluetooth: RFCOMM TTY layer initialized
[  234.144716] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1094: azx_pcm_prepare: bufsize=0x10000, fragsize=0x1000, format=0x11
[  234.150490] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x11
[  234.152489] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0xfffe, stream=0x5, channel=0, format=0x11
[  234.154486] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x1, stream=0x5, channel=0, format=0x11
[  234.156484] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0xffff, stream=0x5, channel=0, format=0x11
[  234.659248] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0xfffe, stream=0x0, channel=0, format=0x0
[  234.660933] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x1, stream=0x0, channel=0, format=0x0
[  234.662934] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0xffff, stream=0x0, channel=0, format=0x0
[  234.665727] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x6, stream=0x0, channel=0, format=0x0
[  237.891314] APIC error on CPU0: 40(40)
[  242.038279] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1094: azx_pcm_prepare: bufsize=0x10000, fragsize=0x1000, format=0x11
[  242.043724] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x6, stream=0x5, channel=0, format=0x11
[  242.045727] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0xfffe, stream=0x5, channel=0, format=0x11
[  242.047723] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x1, stream=0x5, channel=0, format=0x11
[  242.049724] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0xffff, stream=0x5, channel=0, format=0x11
[  247.302996] hda_codec: num_steps = 0 for NID=0xb
[  247.312272] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1094: azx_pcm_prepare: bufsize=0xc030, fragsize=0x6018, format=0x11
[  247.312316] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x11
[  247.313787] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x7, stream=0x0, channel=0, format=0x0
[  252.693437] [fglrx:firegl_mmap] *ERROR* No map found!
[  263.565338] hda_codec: num_steps = 0 for NID=0xb
[  263.567048] ALSA /usr/src/modules/alsa-driver/pci/hda/../../alsa-kernel/pci/hda/hda_intel.c:1094: azx_pcm_prepare: bufsize=0xc030, fragsize=0x6018, format=0x11
[  263.567091] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x7, stream=0x1, channel=0, format=0x11
[  263.568728] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x7, stream=0x0, channel=0, format=0x0
[  274.581551] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0xfffe, stream=0x0, channel=0, format=0x0
[  274.583217] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x1, stream=0x0, channel=0, format=0x0
[  274.585214] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0xffff, stream=0x0, channel=0, format=0x0
[  274.587213] ALSA /usr/src/modules/alsa-driver/pci/hda/hda_codec.c:586: hda_codec_setup_stream: NID=0x6, stream=0x0, channel=0, format=0x0
[  778.276649] APIC error on CPU0: 40(40)
[ 1038.055138] hda_codec: num_steps = 0 for NID=0xb
[ 1068.990104] APIC error on CPU0: 40(40)
[ 1219.739327] APIC error on CPU0: 40(40)
[ 1291.625362] APIC error on CPU0: 40(40)
[ 1632.236698] hda_codec: num_steps = 0 for NID=0x8
[ 1632.280852] hda_codec: num_steps = 0 for NID=0xb
[ 1632.317767] hda_codec: num_steps = 0 for NID=0xb
[ 1632.354917] hda_codec: num_steps = 0 for NID=0xb
[ 1632.391890] hda_codec: num_steps = 0 for NID=0xb
[ 1632.429240] hda_codec: num_steps = 0 for NID=0xb
[ 1632.465859] hda_codec: num_steps = 0 for NID=0xb
[ 1632.502333] hda_codec: num_steps = 0 for NID=0xb
[ 1632.538732] hda_codec: num_steps = 0 for NID=0xb
[ 1632.575943] hda_codec: num_steps = 0 for NID=0xb
[ 1632.611817] hda_codec: num_steps = 0 for NID=0xb
[ 1632.647558] hda_codec: num_steps = 0 for NID=0xb
[ 1632.684585] hda_codec: num_steps = 0 for NID=0xb
[ 1632.722897] hda_codec: num_steps = 0 for NID=0xb
[ 1632.755598] hda_codec: num_steps = 0 for NID=0xb
[ 1632.791519] hda_codec: num_steps = 0 for NID=0xb
[ 1632.826453] hda_codec: num_steps = 0 for NID=0xb
[ 1632.861618] hda_codec: num_steps = 0 for NID=0xb
[ 1632.897018] hda_codec: num_steps = 0 for NID=0xb
[ 1632.994916] hda_codec: num_steps = 0 for NID=0xb
[ 1633.029091] hda_codec: num_steps = 0 for NID=0xb
[ 1633.062882] hda_codec: num_steps = 0 for NID=0xb
[ 1633.097014] hda_codec: num_steps = 0 for NID=0xb
[ 1633.130232] hda_codec: num_steps = 0 for NID=0xb
[ 1633.163438] hda_codec: num_steps = 0 for NID=0xb
[ 1633.196717] hda_codec: num_steps = 0 for NID=0xb
[ 1633.229731] hda_codec: num_steps = 0 for NID=0xb
[ 1633.263658] hda_codec: num_steps = 0 for NID=0xb
[ 1633.296709] hda_codec: num_steps = 0 for NID=0xb
[ 1633.329349] hda_codec: num_steps = 0 for NID=0xb
[ 1633.363712] hda_codec: num_steps = 0 for NID=0xb
[ 1633.399738] hda_codec: num_steps = 0 for NID=0xb
[ 1633.429146] hda_codec: num_steps = 0 for NID=0xb
[ 1633.461305] hda_codec: num_steps = 0 for NID=0xb
[ 1633.493078] hda_codec: num_steps = 0 for NID=0xb
[ 1633.525247] hda_codec: num_steps = 0 for NID=0xb
[ 1633.556526] hda_codec: num_steps = 0 for NID=0xb
[ 1839.636799] hda_codec: num_steps = 0 for NID=0xb
[ 1843.319530] hda_codec: num_steps = 0 for NID=0xb
[ 1869.972160] hda_codec: num_steps = 0 for NID=0x8
[ 1870.006300] hda_codec: num_steps = 0 for NID=0xb
[ 1870.033638] hda_codec: num_steps = 0 for NID=0xb
[ 1870.060720] hda_codec: num_steps = 0 for NID=0xb
[ 1870.088756] hda_codec: num_steps = 0 for NID=0xb
[ 1870.116059] hda_codec: num_steps = 0 for NID=0xb
[ 1870.143317] hda_codec: num_steps = 0 for NID=0xb
[ 1870.171774] hda_codec: num_steps = 0 for NID=0xb
[ 1870.199475] hda_codec: num_steps = 0 for NID=0xb
[ 1870.227358] hda_codec: num_steps = 0 for NID=0xb
[ 1870.256276] hda_codec: num_steps = 0 for NID=0xb
[ 1870.284755] hda_codec: num_steps = 0 for NID=0xb
[ 1870.312535] hda_codec: num_steps = 0 for NID=0xb
[ 1870.340922] hda_codec: num_steps = 0 for NID=0xb
[ 1870.371023] hda_codec: num_steps = 0 for NID=0xb
[ 1870.400541] hda_codec: num_steps = 0 for NID=0xb
[ 1870.428933] hda_codec: num_steps = 0 for NID=0xb
[ 1870.457606] hda_codec: num_steps = 0 for NID=0xb
[ 1870.486099] hda_codec: num_steps = 0 for NID=0xb
[ 1870.572571] hda_codec: num_steps = 0 for NID=0xb
[ 1870.601327] hda_codec: num_steps = 0 for NID=0xb
[ 1870.630122] hda_codec: num_steps = 0 for NID=0xb
[ 1870.660333] hda_codec: num_steps = 0 for NID=0xb
[ 1870.691244] hda_codec: num_steps = 0 for NID=0xb
[ 1870.721927] hda_codec: num_steps = 0 for NID=0xb
[ 1870.752116] hda_codec: num_steps = 0 for NID=0xb
[ 1870.783177] hda_codec: num_steps = 0 for NID=0xb
[ 1870.813718] hda_codec: num_steps = 0 for NID=0xb
[ 1870.843740] hda_codec: num_steps = 0 for NID=0xb
[ 1870.875085] hda_codec: num_steps = 0 for NID=0xb
[ 1870.905915] hda_codec: num_steps = 0 for NID=0xb
[ 1870.935438] hda_codec: num_steps = 0 for NID=0xb
[ 1870.965612] hda_codec: num_steps = 0 for NID=0xb
[ 1870.996149] hda_codec: num_steps = 0 for NID=0xb
[ 1871.026396] hda_codec: num_steps = 0 for NID=0xb
[ 1871.056614] hda_codec: num_steps = 0 for NID=0xb
[ 1871.087332] hda_codec: num_steps = 0 for NID=0xb

```

```

root@surreal:~# lspci
0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5950 (rev 10)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:11.0 IDE interface: ATI Technologies Inc: Unknown device 437a (rev 80)
0000:00:12.0 IDE interface: ATI Technologies Inc: Unknown device 4379 (rev 80)
0000:00:13.0 USB Controller: ATI Technologies Inc: Unknown device 4374 (rev 80)
0000:00:13.1 USB Controller: ATI Technologies Inc: Unknown device 4375 (rev 80)
0000:00:13.2 USB Controller: ATI Technologies Inc: Unknown device 4373 (rev 80)
0000:00:14.0 SMBus: ATI Technologies Inc: Unknown device 4372 (rev 81)
0000:00:14.1 IDE interface: ATI Technologies Inc: Unknown device 4376 (rev 80)
0000:00:14.2 0403: ATI Technologies Inc: Unknown device 437b (rev 01)
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 4377 (rev 80)
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4371 (rev 80)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5974
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
0000:02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:02:04.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)


```

---

### Post by italian_boy on 2006-09-12
I have the same error messages about "hda intel" and "invalid argument", the difference is I actually have sound working properly.
Oh, of course I cannot store my volume settings (errors with alsamixer and alsactl prevent them to start)

---

### Post by Cynical on 2006-09-12
Strange, I dont have any problems at all with azailia audio. I'm using a 32-bit dapper install though

---

### Post by floobit on 2007-05-08
I am experiencing similar, but seemingly less extreme problems.  On my Edgy install (now upgraded to feisty), hardware detection and driver installation was automatic and painless, giving me support for my ALC880 chip, with aplay -l yielding: 

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Physically, I have both a SPDIF optical and a headphone jack plugged in (the windows driver for the chip notices when something is plugged in).  

However, I get no signal from either plug.  alsamixer lists nothing as muted, and all my volume is at full.  Any suggestions?

Dylan

---

### Post by lokanetra on 2007-07-18
I've found a solution, albeit inelegant, for the Azalia/intel8x0 problem.

Grab fresh drivers from alsa
Compile with all cards and all options
Reboot

Now as I've mentioned this might not be the tailored solution to compile the alsa drivers, but on every ubuntu install it's worked properly without adding or removing anything else to ubuntu.  

[B]wget [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.14.tar.bz2)
tar -xvf alsa-driver-1.0.14.tar.bz2
cd alsa-driver-1.0.14
./configure --with-cards=all --with-card-options=all
sudo make
sudo make install[/B]

Be sure to unmute the correct outputs on the mixer.  You may need to add the **front** slider to the mixer.

It's crude but effective, just to get things working for now.

---

### Post by dmatej on 2008-04-04
I have a little actualization (but not fullpercent solution): [http://ubuntuforums.org/showpost.php?p=4653915&postcount=6](http://ubuntuforums.org/showpost.php?p=4653915&postcount=6)

---

