---
title: "Yet another Jaunty breaks Nvidia driver post"
date: 2009-08-06
forum: Multimedia Software
---

### Post by kolibri on 2009-08-06
I don't know why I keep upgrading, this always happens.

I went from Hardy to Intrepid (applied any updates) to Jaunty and now can't get the Nvidia drivers to work.  I am running two monitors so I need to get twinview working through nvidia-settings (unless there is another way).

EnvyNg worked for me on previous installations, but it's not working now.

I've gone through every other thread I could find and none of the fixes work.

I've tried using backed up xorg.conf files

I've completely removed all Nvidia components and tried:

- installing drivers using system admin-hardware drivers.
-installing drivers through synaptic
-installing driver from NVIDIA's webpage after editing the files they recommend (setting DISABLED_MODULES="nv nvidia_new")
-using envyng
-using the 'avenard' repository fix instructions

after all of these tries I end up in the same place:

I try to run 'sudo nvidia-settings' and get the common error that "you do not appear to be using the NVIDIA X driver....." however, as it goes, editing my x config file as sudo nvidia-xconfig doesnt' do anything.

Upon start up I get the same error I've seen in several threads-
"Failed to initialize the NVIDIA graphics device
...
Run Ubuntu in low graphics mode"

and then I get:

"there already appears to be an x server running on display:0...."
answering yes to the next prompt or so I get to:

"The specified display number was busy so this server was started on display:1"

lspci says:
 VGA compatible controller:nvidia Corporation G71 [GeForce 7300](rev al)

lsmode | grep nvidia returns:
nvidia    9550692     0
agpgarat    42696     2 nvidia, intel_agp

I'm on another computer, so I can't copy and paste, but the relevant parts of xorg.conf would seem to me to be:
Section "Device"
Identifier "configured video device"
Driver "nvidia"

anyway, any help out there?  everything that I remember working for me after updating to Hardy isn't working now.

---

### Post by thenanodude on 2009-08-06
I don't have exactly the same nvidia card you have (I have a GeForce Go 6150), but I'll try to help.

Under Hardy, I used EnvyNG, as it was the only way I could reliably get my nvidia drivers to load.  However, the upgrade the Jaunty was slightly smoother for me, and allowed me to do without EnvyNG.  At first, I had a strange error similar to the "there already appears to be an x server running on display:0...." you saw.  Unfortunately, I do not remember exactly how I fixed it, but let me tell you the set up I have now and see if that helps.  

Using the Synaptic Package Manager, I have the following nvidia-related packages installed:

nvidia-settings  (version 180.25-0ubuntu1)
nvidia-180-kernel-source  (version 180.44-0ubuntu1)  (not sure if you need the source, but I do build my own kernel from time to time, so I have it)
nvidia-glx-180  (version 180.44-0ubuntu1)
nvidia-180-libvdpau  (version 180.44-0ubuntu1)

the relevant sections of my xorg.conf are:

```

Section "Module"
        Load            "glx"
EndSection

Section "Device"
        Identifier      "Videocard0"
        Vendorname      "NVIDIA Corporation"
        Boardname       "GeForce Go 6150"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "RenderAccel" "true"
        Option  "UseEvents" "false"
        Option  "TripleBuffer" "1"
        Option  "DamageEvents" "1"
        Option  "BackingStore" "1"
        Option  "DisableGLXRootClipping" "true"
        Option  "PixmapCacheSize" "70000"
        Option  "OnDemandVBlankInterrupts" "true"
EndSection

```

I didn't post my "Screen" section, because I have a laptop and use an external monitor, so I thought it may be a bit more than you need.  let me know if you think it would be useful.

Finally, I used to have to use the "Hardware Drivers" program (jockey) to turn on the nvidia driver, but it seems that Ubuntu has worked out the licensing with nvidia, so it is no longer necessary.

---

### Post by NotJustANewbie on 2009-08-06
Ok. In this situation, I would burn a Jaunty live CD, and boot up that. Install the required Nvidia driver (while in live mode) and get everything working there.
Then copy Xorg.conf to usb stick or online or whatever.
Then go back to the broken system and overwrite the working Xorg.conf file to the broken one.
Hope this helps :)

---

### Post by wojox on 2009-08-06
This always helps me:

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

---

### Post by kolibri on 2009-08-10
Well, I had a long post written over the weekend including lots of output from several often requested shell commands for these types of problems, but the computer froze up on me and I had to hard-restart.  I don't know if that is an independent jaunty problem or part of the video driver issue.

I've tried all the suggestions above (most before my first post), I've even done a clean reinstall, and I still can't get my computer to load the nvidia driver nor get to nvidia settings to set up twinview.  System-admin-hardware drivers says the driver is in use, but nvidia-settings says it isn't, and I always have to start my computer in low graphics mode.

---

### Post by Cope57 on 2009-08-10
Compile the video driver from source, seems to work every time.

---

### Post by Raffles10 on 2009-08-10
> **NotJustANewbie said:**
> Ok. In this situation, I would burn a Jaunty live CD, and boot up that. Install the required Nvidia driver (while in live mode) and get everything working there.
Then copy Xorg.conf to usb stick or online or whatever.
Then go back to the broken system and overwrite the working Xorg.conf file to the broken one.
Hope this helps :)

How is this possible ? To load the driver you have to reboot the system, you can't reboot a live cd.

---

### Post by kolibri on 2009-08-10
cope-

how do you compile the driver from source?  You mean downloading and installing the driver directly from NVIDIA?  I tried that before the doing the clean install, it didn't work,  I could try it again.

Well, that didn't work.  Still says it can't load the nvidia kernal, then tells me there already appears to by an x server running on display :0.

Can someone help me decipher my dmesg output?
[HTML][    0.464846] pci 0000:02:01.0: PME# supported from D0 D1 D2 D3hot
[    0.464850] pci 0000:02:01.0: PME# disabled
[    0.464884] pci 0000:02:03.0: reg 10 32bit mmio: [0xeffd0000-0xeffdffff]
[    0.464959] pci 0000:02:04.0: reg 10 32bit mmio: [0xe8000000-0xebffffff]
[    0.465025] pci 0000:02:05.0: reg 10 32bit mmio: [0xeffe0000-0xeffeffff]
[    0.465031] pci 0000:02:05.0: reg 14 io port: [0xef00-0xef07]
[    0.465063] pci 0000:02:05.0: PME# supported from D3hot D3cold
[    0.465067] pci 0000:02:05.0: PME# disabled
[    0.465100] pci 0000:02:08.0: reg 10 32bit mmio: [0xefffe000-0xefffefff]
[    0.465106] pci 0000:02:08.0: reg 14 io port: [0xee00-0xee3f]
[    0.465138] pci 0000:02:08.0: supports D1 D2
[    0.465139] pci 0000:02:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.465143] pci 0000:02:08.0: PME# disabled
[    0.465178] pci 0000:00:1e.0: transparent bridge
[    0.465182] pci 0000:00:1e.0: bridge io port: [0xe000-0xefff]
[    0.465185] pci 0000:00:1e.0: bridge 32bit mmio: [0xe8000000-0xefffffff]
[    0.465198] bus 00 -> node 0
[    0.465205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.465440] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.475512] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.475630] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[    0.475746] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[    0.475862] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.475978] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.476105] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.476222] ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.476338] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.476524] ACPI: WMI: Mapper loaded
[    0.476581] SCSI subsystem initialized
[    0.476581] libata version 3.00 loaded.
[    0.476581] usbcore: registered new interface driver usbfs
[    0.476581] usbcore: registered new interface driver hub
[    0.476581] usbcore: registered new device driver usb
[    0.476581] PCI: Using ACPI for IRQ routing
[    0.484011] Bluetooth: Core ver 2.13
[    0.484028] NET: Registered protocol family 31
[    0.484028] Bluetooth: HCI device and connection manager initialized
[    0.484028] Bluetooth: HCI socket layer initialized
[    0.484028] NET: Registered protocol family 8
[    0.484028] NET: Registered protocol family 20
[    0.484041] NetLabel: Initializing
[    0.484043] NetLabel:  domain hash size = 128
[    0.484045] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.484060] NetLabel:  unlabeled traffic allowed by default
[    0.484074] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.484080] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.488072] AppArmor: AppArmor Filesystem Enabled
[    0.496030] pnp: PnP ACPI init
[    0.496040] ACPI: bus type pnp registered
[    0.497856] pnp: PnP ACPI: found 11 devices
[    0.497858] ACPI: ACPI bus type pnp unregistered
[    0.497862] PnPBIOS: Disabled by ACPI PNP
[    0.497870] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.497872] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.497875] system 00:01: ioport range 0x294-0x297 has been reserved
[    0.497877] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.497884] system 00:07: ioport range 0x400-0x4bf has been reserved
[    0.497890] system 00:09: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.497895] system 00:0a: iomem range 0xd4800-0xd7fff has been reserved
[    0.497898] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
[    0.497900] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.497902] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.497905] system 00:0a: iomem range 0xfed00000-0xfed000ff has been reserved
[    0.497907] system 00:0a: iomem range 0x7fee0000-0x7fefffff could not be reserved
[    0.497910] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.497912] system 00:0a: iomem range 0x100000-0x7fedffff could not be reserved
[    0.497915] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.497917] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.497920] system 00:0a: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.497922] system 00:0a: iomem range 0xfff00000-0xffffffff has been reserved
[    0.497924] system 00:0a: iomem range 0xe0000-0xeffff has been reserved
[    0.500503] Switched to high resolution mode on CPU 1
[    0.504033] Switched to high resolution mode on CPU 0
[    0.532590] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.532592] pci 0000:00:01.0:   IO window: disabled
[    0.532596] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfcffffff
[    0.532599] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.532604] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.532607] pci 0000:00:1e.0:   IO window: 0xe000-0xefff
[    0.532611] pci 0000:00:1e.0:   MEM window: 0xe8000000-0xefffffff
[    0.532615] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.532626] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.532630] pci 0000:00:01.0: setting latency timer to 64
[    0.532636] pci 0000:00:1e.0: setting latency timer to 64
[    0.532639] bus: 00 index 0 io port: [0x00-0xffff]
[    0.532641] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.532643] bus: 01 index 0 mmio: [0x0-0x0]
[    0.532645] bus: 01 index 1 mmio: [0xfa000000-0xfcffffff]
[    0.532647] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.532649] bus: 01 index 3 mmio: [0x0-0x0]
[    0.532651] bus: 02 index 0 io port: [0xe000-0xefff]
[    0.532653] bus: 02 index 1 mmio: [0xe8000000-0xefffffff]
[    0.532654] bus: 02 index 2 mmio: [0x0-0x0]
[    0.532656] bus: 02 index 3 io port: [0x00-0xffff]
[    0.532658] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.532665] NET: Registered protocol family 2
[    0.548082] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.548334] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.548638] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.548813] TCP: Hash tables configured (established 131072 bind 65536)
[    0.548816] TCP reno registered
[    0.556128] NET: Registered protocol family 1
[    0.556264] checking if image is initramfs... it is
[   10.142737] Freeing initrd memory: 7368k freed
[   10.142954] cpufreq: No nForce2 chipset.
[   10.143086] audit: initializing netlink socket (disabled)
[   10.143110] type=2000 audit(1249930767.140:1): initialized
[   10.149724] highmem bounce pool size: 64 pages
[   10.149729] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[   10.150943] VFS: Disk quotas dquot_6.5.1
[   10.150997] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   10.151544] fuse init (API version 7.10)
[   10.151622] msgmni has been set to 1698
[   10.151789] alg: No test for stdrng (krng)
[   10.151799] io scheduler noop registered
[   10.151801] io scheduler anticipatory registered
[   10.151803] io scheduler deadline registered
[   10.151815] io scheduler cfq registered (default)
[   10.151915] pci 0000:01:00.0: Boot video device
[   10.151936] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[   10.153781] pcieport-driver 0000:00:01.0: setting latency timer to 64
[   10.153811] pcieport-driver 0000:00:01.0: found MSI capability
[   10.153833] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[   10.153842] pci_express 0000:00:01.0:pcie00: allocate port service
[   10.153896] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   10.153905] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[   10.154031] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[   10.154033] ACPI: Power Button (FF) [PWRF]
[   10.154071] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[   10.154074] ACPI: Power Button (CM) [PWRB]
[   10.154120] fan PNP0C0B:00: registered as cooling_device0
[   10.154125] ACPI: Fan [FAN] (on)
[   10.154455] ACPI: SSDT 7FEE7F80, 0175 (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
[   10.154676] processor ACPI_CPU:00: registered as cooling_device1
[   10.154819] ACPI: SSDT 7FEE8390, 00CE (r1 HPQOEM SLIC-CPC 42302E31 AWRD        0)
[   10.155025] processor ACPI_CPU:01: registered as cooling_device2
[   10.156816] thermal LNXTHERM:01: registered as thermal_zone0
[   10.157088] ACPI: Thermal Zone [THRM] (28 C)
[   10.157131] isapnp: Scanning for PnP cards...
[   10.510027] isapnp: No Plug & Play device found
[   10.516757] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[   10.517708] brd: module loaded
[   10.517991] loop: module loaded
[   10.518049] Fixed MDIO Bus: probed
[   10.518054] PPP generic driver version 2.4.2
[   10.518104] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[   10.518131] Driver 'sd' needs updating - please use bus_type methods
[   10.518141] Driver 'sr' needs updating - please use bus_type methods
[   10.518175] ahci 0000:00:1f.2: version 3.0
[   10.518187] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   10.518214] ahci 0000:00:1f.2: irq 2302 for MSI/MSI-X
[   10.518267] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl RAID mode
[   10.518270] ahci 0000:00:1f.2: flags: 64bit ncq led clo 
[   10.518274] ahci 0000:00:1f.2: setting latency timer to 64
[   10.518499] scsi0 : ahci
[   10.518576] scsi1 : ahci
[   10.518633] scsi2 : ahci
[   10.518686] scsi3 : ahci
[   10.518773] ata1: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe100 irq 2302
[   10.518775] ata2: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe180 irq 2302
[   10.518778] ata3: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe200 irq 2302
[   10.518781] ata4: SATA max UDMA/133 abar m1024@0xfdffe000 port 0xfdffe280 irq 2302
[   10.836035] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   10.836510] ata1.00: ATA-7: WDC WD2500JS-60NCB1, 10.02E02, max UDMA/100
[   10.836513] ata1.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   10.837100] ata1.00: configured for UDMA/100
[   11.560033] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   11.560518] ata2.00: ATA-7: WDC WD2500JS-60NCB1, 10.02E02, max UDMA/100
[   11.560521] ata2.00: 488397168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[   11.561112] ata2.00: configured for UDMA/100
[   12.284033] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   12.297047] ata3.00: ATAPI: ATAPI   DVD A  DH16A1L, KH15, max UDMA/33, ATAPI AN
[   12.310439] ata3.00: configured for UDMA/33
[   12.628033] ata4: SATA link down (SStatus 0 SControl 300)
[   12.628151] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JS-60N 10.0 PQ: 0 ANSI: 5
[   12.628260] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   12.628286] sd 0:0:0:0: [sda] Write Protect is off
[   12.628288] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.628311] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.628365] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   12.628378] sd 0:0:0:0: [sda] Write Protect is off
[   12.628380] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   12.628403] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.628406]  sda: sda1 sda2 < sda5 > sda3
[   12.682080] sd 0:0:0:0: [sda] Attached SCSI disk
[   12.682128] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   12.682216] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500JS-60N 10.0 PQ: 0 ANSI: 5
[   12.682290] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   12.682304] sd 1:0:0:0: [sdb] Write Protect is off
[   12.682306] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   12.682329] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.682375] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   12.682388] sd 1:0:0:0: [sdb] Write Protect is off
[   12.682390] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   12.682413] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   12.682416]  sdb: sdb1
[   12.703692] sd 1:0:0:0: [sdb] Attached SCSI disk
[   12.703736] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   12.704815] scsi 2:0:0:0: CD-ROM            ATAPI    DVD A  DH16A1L   KH15 PQ: 0 ANSI: 5
[   12.710274] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[   12.710277] Uniform CD-ROM driver Revision: 3.20
[   12.710380] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   12.710422] sr 2:0:0:0: Attached scsi generic sg2 type 5
[   12.710478] ata_piix 0000:00:1f.1: version 2.12
[   12.710488] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.710531] ata_piix 0000:00:1f.1: setting latency timer to 64
[   12.710594] scsi4 : ata_piix
[   12.710647] scsi5 : ata_piix
[   12.710995] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xfb00 irq 14
[   12.710997] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xfb08 irq 15
[   12.864106] ata6: port disabled. ignoring.
[   12.864733] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[   12.864752] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   12.864765] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   12.864768] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   12.864823] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[   12.868735] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[   12.868746] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdfff000
[   12.884041] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[   12.884121] usb usb1: configuration #1 chosen from 1 choice
[   12.884157] hub 1-0:1.0: USB hub found
[   12.884165] hub 1-0:1.0: 8 ports detected
[   12.884296] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[   12.884310] uhci_hcd: USB Universal Host Controller Interface driver
[   12.884329] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[   12.884334] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   12.884337] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   12.884376] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[   12.884397] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000ff00
[   12.884459] usb usb2: configuration #1 chosen from 1 choice
[   12.884481] hub 2-0:1.0: USB hub found
[   12.884487] hub 2-0:1.0: 2 ports detected
[   12.884561] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   12.884566] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[   12.884568] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   12.884604] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[   12.884630] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fe00
[   12.884690] usb usb3: configuration #1 chosen from 1 choice
[   12.884712] hub 3-0:1.0: USB hub found
[   12.884718] hub 3-0:1.0: 2 ports detected
[   12.884790] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   12.884795] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[   12.884797] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.884833] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[   12.884859] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000fd00
[   12.884921] usb usb4: configuration #1 chosen from 1 choice
[   12.884943] hub 4-0:1.0: USB hub found
[   12.884949] hub 4-0:1.0: 2 ports detected
[   12.885023] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[   12.885028] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   12.885031] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   12.885074] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[   12.885102] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000fc00
[   12.885166] usb usb5: configuration #1 chosen from 1 choice
[   12.885188] hub 5-0:1.0: USB hub found
[   12.885193] hub 5-0:1.0: 2 ports detected
[   12.885316] PNP: No PS/2 controller found. Probing ports directly.
[   12.887533] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.887538] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.888064] mice: PS/2 mouse device common for all mice
[   12.888236] rtc_cmos 00:04: RTC can wake from S4
[   12.888282] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[   12.888304] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[   12.888355] device-mapper: uevent: version 1.0.3
[   12.888430] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[   12.888496] device-mapper: multipath: version 1.0.5 loaded
[   12.888499] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.888564] EISA: Probing bus 0 at eisa.0
[   12.888590] EISA: Detected 0 cards.
[   12.888635] cpuidle: using governor ladder
[   12.888636] cpuidle: using governor menu
[   12.889097] TCP cubic registered
[   12.889184] NET: Registered protocol family 10
[   12.889573] lo: Disabled Privacy Extensions
[   12.889875] NET: Registered protocol family 17
[   12.889890] Bluetooth: L2CAP ver 2.11
[   12.889892] Bluetooth: L2CAP socket layer initialized
[   12.889894] Bluetooth: SCO (Voice Link) ver 0.6
[   12.889896] Bluetooth: SCO socket layer initialized
[   12.889925] Bluetooth: RFCOMM socket layer initialized
[   12.889932] Bluetooth: RFCOMM TTY layer initialized
[   12.889934] Bluetooth: RFCOMM ver 1.10
[   12.890907] Using IPI No-Shortcut mode
[   12.890989] registered taskstats version 1
[   12.891101]   Magic number: 5:116:999
[   12.891112] block sda1: hash matches
[   12.891132] system 00:01: hash matches
[   12.891134]  pnp0: hash matches
[   12.891170] rtc_cmos 00:04: setting system clock to 2009-08-10 18:59:30 UTC (1249930770)
[   12.891172] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   12.891174] EDD information not available.
[   12.891340] Freeing unused kernel memory: 532k freed
[   12.891455] Write protecting the kernel text: 4116k
[   12.891496] Write protecting the kernel read-only data: 1524k
[   13.103694] ohci1394 0000:02:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   13.155434] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[effff000-effff7ff]  Max Packet=[1024]  IR/IT contexts=[8/8]
[   13.168221] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[   13.168224] e100: Copyright(c) 1999-2006 Intel Corporation
[   13.168263] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   13.193682] e100 0000:02:08.0: PME# disabled
[   13.195839] e100: eth0: e100_probe: addr 0xefffe000, irq 20, MAC addr 00:1a:92:69:da:5c
[   13.272146] usb 1-7: new high speed USB device using ehci_hcd and address 3
[   13.406129] usb 1-7: configuration #1 chosen from 1 choice
[   13.410691] Initializing USB Mass Storage driver...
[   13.411398] scsi6 : SCSI emulation for USB Mass Storage devices
[   13.411535] usb-storage: device found at 3
[   13.411537] usb-storage: waiting for device to settle before scanning
[   13.411544] usbcore: registered new interface driver usb-storage
[   13.411547] USB Mass Storage support registered.
[   13.644059] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   13.730397] PM: Starting manual resume from disk
[   13.730400] PM: Resume from partition 8:5
[   13.730401] PM: Checking hibernation image.
[   13.730500] PM: Resume from disk failed.
[   13.759246] kjournald starting.  Commit interval 5 seconds
[   13.759253] EXT3-fs: mounted filesystem with ordered data mode.
[   13.824719] usb 3-1: configuration #1 chosen from 1 choice
[   14.436178] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d8000125fe09]
[   17.521038] udev: starting version 141
[   18.034557] usbcore: registered new interface driver hiddev
[   18.049945] input: BTC USB Multimedia Cordless Kit   as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.0/input/input3
[   18.052757] generic-usb 0003:03F0:0B0C.0001: input,hidraw0: USB HID v1.00 Keyboard [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:1d.1-1/input0
[   18.101291] input: BTC USB Multimedia Cordless Kit   as /devices/pci0000:00/0000:00:1d.1/usb3/3-1/3-1:1.1/input/input4
[   18.103930] generic-usb 0003:03F0:0B0C.0002: input,hiddev96,hidraw1: USB HID v1.00 Mouse [BTC USB Multimedia Cordless Kit  ] on usb-0000:00:1d.1-1/input1
[   18.103950] usbcore: registered new interface driver usbhid
[   18.103971] usbhid: v2.6:USB HID core driver
[   18.141407] Linux agpgart interface v0.103
[   18.142413] iTCO_vendor_support: vendor-support=0
[   18.256188] input: PC Speaker as /devices/platform/pcspkr/input/input5
[   18.404474] cfg80211: Calling CRDA to update world regulatory domain
[   18.408585] usb-storage: device scan complete
[   18.409145] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   18.409768] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   18.410393] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   18.411018] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   18.412365] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   18.412430] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   18.413771] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[   18.413824] sd 6:0:0:1: Attached scsi generic sg4 type 0
[   18.416110] sd 6:0:0:2: [sde] Attached SCSI removable disk
[   18.416162] sd 6:0:0:2: Attached scsi generic sg5 type 0
[   18.416977] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[   18.417030] sd 6:0:0:3: Attached scsi generic sg6 type 0
[   18.896812] cfg80211: World regulatory domain updated:
[   18.896815] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.896817] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.896819] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.896821] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.896824] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.896826] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.921966] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   18.922195] iTCO_wdt: Found a ICH7DH TCO device (Version=2, TCOBASE=0x0460)
[   18.922245] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   19.048224] Linux video capture interface: v2.00
[   19.078841] ath5k_pci 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   19.078900] ath5k_pci 0000:02:03.0: registered as 'phy0'
[   19.114176] cx18:  Start initialization, version 1.0.1
[   19.164863] phy0: Selected rate control algorithm 'pid'
[   19.214515] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa2, PHY: 0x61)
[   19.214551] cx18-0: Initializing card #0
[   19.214555] cx18-0: Autodetected Hauppauge card
[   19.214923] cx18 0000:02:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.214932] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   19.216989] cx18-0: cx23418 revision 01010000 (B)
[   19.236677] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.236718] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.269953] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   19.440637] tveeprom 0-0050: Hauppauge model 74551, rev C1A3, serial# 1678293
[   19.440640] tveeprom 0-0050: MAC address is 00-0D-FE-19-9B-D5
[   19.440643] tveeprom 0-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   19.440645] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   19.440647] tveeprom 0-0050: audio processor is CX23418 (idx 38)
[   19.440649] tveeprom 0-0050: decoder processor is CX23418 (idx 31)
[   19.440651] tveeprom 0-0050: has radio
[   19.440653] cx18-0: Autodetected Hauppauge HVR-1600
[   19.440654] cx18-0: VBI is not yet supported
[   19.567554] tuner 1-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
[   19.575396] tda9887 1-0043: creating new instance
[   19.575399] tda9887 1-0043: tda988[5/6/7] found
[   19.576763] tuner 1-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   19.576788] cs5345 0-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   19.586190] tuner-simple 1-0061: creating new instance
[   19.586193] tuner-simple 1-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   19.588437] cx18-0: Disabled encoder IDX device
[   19.588543] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   19.588546] DVB: registering new adapter (cx18)
[   19.671985] MXL5005S: Attached at address 0x63
[   19.671989] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   19.672056] cx18-0: DVB Frontend registered
[   19.672084] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   19.672107] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   19.672133] cx18-0: Registered device radio0 for encoder radio
[   19.672135] cx18-0: Initialized card #0: Hauppauge HVR-1600
[   19.672157] cx18:  End initialization
[   19.817110] lp: driver loaded but no devices found
[   19.881861] Adding 6048432k swap on /dev/sda5.  Priority:-1 extents:1 across:6048432k
[   20.414379] EXT3 FS on sda1, internal journal
[   21.150971] kjournald starting.  Commit interval 5 seconds
[   21.151228] EXT3 FS on sdb1, internal journal
[   21.151234] EXT3-fs: mounted filesystem with ordered data mode.
[   21.393742] type=1505 audit(1249930779.000:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2181
[   21.435061] type=1505 audit(1249930779.041:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2185
[   21.435156] type=1505 audit(1249930779.041:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2185
[   21.435195] type=1505 audit(1249930779.041:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2185
[   21.435229] type=1505 audit(1249930779.041:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2185
[   21.549907] type=1505 audit(1249930779.157:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2190
[   21.550073] type=1505 audit(1249930779.157:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2190
[   21.574530] type=1505 audit(1249930779.181:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2194
[   23.021473] cx18 0000:02:04.0: firmware: requesting v4l-cx23418-apu.fw
[   23.276538] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   23.776142] cx18 0000:02:04.0: firmware: requesting v4l-cx23418-cpu.fw
[   23.894139] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   23.900454] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   24.096516] cx18 0000:02:04.0: firmware: requesting v4l-cx23418-apu.fw
[   24.696090] cx18 0000:02:04.0: firmware: requesting v4l-cx23418-cpu.fw
[   25.008067] cx18 0000:02:04.0: firmware: requesting v4l-cx23418-dig.fw
[   25.195119] cx18-0: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   25.297403] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.297405] Bluetooth: BNEP filters: protocol multicast
[   25.311330] Bridge firewalling registered
[   26.212752] ppdev: user-space parallel port driver
[   30.407588] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.408128] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   30.434409] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   30.435540] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   40.508022] eth0: no IPv6 routers present
[   73.345391] mtrr: no MTRR for d0000000,10000000 found
[  121.228925] nvidia: module license 'NVIDIA' taints kernel.
[  121.484706] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  121.484715] nvidia 0000:01:00.0: setting latency timer to 64
[  121.485721] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.31  Tue Jul 28 15:43:22 PDT 2009
[  174.463198] nvidia 0000:01:00.0: setting latency timer to 64
[  174.464278] NVRM: loading NVIDIA UNIX x86 Kernel Module  185.18.31  Tue Jul 28 15:43:22 PDT 2009
[  174.489601] vmap allocation failed: use vmalloc=<size> to increase size.
[  174.489656] NVRM: RmInitAdapter failed! (0x23:0xffffffff:683)
[  174.489660] NVRM: rm_init_adapter(0) failed
[  177.645619] vmap allocation failed: use vmalloc=<size> to increase size.
[  177.645695] NVRM: RmInitAdapter failed! (0x23:0xffffffff:683)
[  177.645700] NVRM: rm_init_adapter(0) failed
[  180.835566] vmap allocation failed: use vmalloc=<size> to increase size.
[  180.835634] NVRM: RmInitAdapter failed! (0x23:0xffffffff:683)
[  180.835638] NVRM: rm_init_adapter(0) failed
[  502.248911] glxinfo[6865]: segfault at 0 ip 0804ad46 sp bf845f80 error 4 in glxinfo[8048000+5000]
[  502.280098] glxinfo[6868]: segfault at 0 ip 0804ad46 sp bfaf2a00 error 4 in glxinfo[8048000+5000]
[/HTML]

I guess only the end is relevant, does this provide info as to why I can't get it working?

---

### Post by dagrump on 2009-08-10
What are you running for hardware? That could help to isolate the problem.

---

### Post by kolibri on 2009-08-10
Output from lspci, right?  I had done all this and the computer froze up when i went to post:

[HTML]00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA RAID Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
02:01.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:03.0 Ethernet controller: Atheros Communications Inc. AR5413 802.11abg NIC (rev 01)
02:04.0 Multimedia video controller: Conexant Systems, Inc. CX23418 Single-Chip MPEG-2 Encoder with Integrated Analog Video/Broadcast Audio Decoder
02:05.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
[/HTML]

I found this on the nvidia manual, but i don't know exactly how to do what nividia suggests, anyone got an idiots guide to doing this?

[HTML]The kernel virtual address space still available after the creation of the direct system memory mapping is used by both the kernel and by drivers to map I/O resources, and for some memory allocations. Depending on the number of consumers and their respective requirements, the Linux kernel's virtual address space may be exhausted. Newer Linux kernels print an error message of the form below when this happens:

allocation failed: out of vmalloc space - use vmalloc=<size> to increase size.

The NVIDIA kernel module requires portions of the kernel's virtual address space for each GPU and for certain memory allocations. If no more than 128MB are available to the kernel and device drivers at boot time, the NVIDIA kernel module may be unable to initialize all GPUs, or fail memory allocations. This is not usually a problem with only 1 or 2 GPUs, however depending on the number of other drivers and their usage patterns, it can be; it is likely to be a problem with 3 or more GPUs.

Possible solutions for this problem include:

    *

      If available, the 'vmalloc' kernel parameter can be used to increase the size of the kernel virtual address space reserved by the Linux kernel (the default is 128MB). Incrementally raising this to find the best balance between the size of the kernel virtual address space made available and the size of the direct system memory mapping is recommended. You can achieve this by passing 'vmalloc=192M', 'vmalloc=256MB', ..., to the kernel and checking if the above error message continues to be printed.

      Note that some versions of the GRUB boot loader have problems calculating the memory layout and loading the initrd if the 'vmalloc' kernel parameter is used. The 'uppermem' GRUB command can be used to force GRUB to load the initrd into a lower region of system memory to work around this problem. This will not adversely affect system performance once the kernel has been loaded. The suggested syntax is:

      title     Kernel Title
      uppermem  524288
      kernel    (hdX,Y)/boot/vmlinuz...

      Also note that the 'vmalloc' kernel parameter only exists on Linux 2.6.9 and later kernels. On older kernels, the amount of system memory used by the kernel can be reduced with the 'mem' kernel parameter, which also reduces the size of the direct mapping and thus increases the size of the kernel virtual address space available. For example, 'mem=512M' instructs the kernel to ignore all but the first 512MB of system memory. Although it is undesirable to reduce the amount of usable system memory, this approach can be used to check if initialization problems are caused by kernel virtual address space exhaustion.
[/HTML]

---

### Post by kolibri on 2009-08-11
I gave up.

I rolled back to a clean install of Hardy, where I was a week ago.  I was hoping for the jaunty versions of a few programs, but I need both my monitors.

Envyng works on a clean install of hardy for me, it didn't work on a clean install of jaunty.

---

### Post by surreaslylph on 2009-08-22
It sounds like I'm having the same problem, but I'm not sure if this is the right place to put this.  After quite a bit of hair pulling, I was able to get the drivers (and thus world of warcraft to work), but every time I reboot the xorg.conf file gets overwritten and I'm not sure why.  I have a Dell Vostro 1500 with a nvidia 8400M GS and I am using 2.6.24-24 generic.  I used the information on installing the drivers from this link [http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368) to help me find the work around.  I have tried a ton of other variable and this seems to be the only thing that works.

1. ctrl+alt+f1
2. sudo /etc/init.d/gdm stop
3. copy/overwrite existing xorg.conf file with one from before I updated.
4. run the script to install the driver.  make sure to say no to when it asks if you    want to run nvidia-xconfig.
5. sudo nvidia-xconfig (yeah go figure :-p)
6. sudo /etc/init.d/gdm start

I'd really appreciate any help you guys/gals can give!

Thanks!

---

