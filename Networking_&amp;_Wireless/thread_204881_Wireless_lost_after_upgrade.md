---
title: "Wireless lost after upgrade"
date: 2006-06-27
forum: Networking &amp; Wireless
---

### Post by alastair lewis on 2006-06-27
Since upgrading to dapper I have lost wireless. I had been using a Netgear WG511v3 card with Ndiswrapper (Acer aspire 5002, i386 install of breezy and now dapper).

I used automatrix to install ndiswrapper utils and wireless-tools.

```
ndiswrapper -l

Installed ndis drivers:
netwg511                driver present, hardware present
```

```
lsmod

Module                  Size  Used by
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
powernow_k8            12680  0
cpufreq_userspace       4696  1
cpufreq_stats           5636  0
freq_table              4740  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
ndiswrapper           177364  0
nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
ipv6                  265728  6
af_packet              22920  4
dm_mod                 58936  1
md_mod                 72532  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
snd_intel8x0           33692  3
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
prism54                54152  0
snd_pcm                89864  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
joydev                 10048  0
tsdev                   8000  0
pcmcia                 40508  0
snd                    55268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
psmouse                36100  0
serio_raw               7300  0
yenta_socket           28428  2
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
pcspkr                  2180  0
rtc                    13492  0
sis900                 22912  0
mii                     5888  1 sis900
i2c_sis96x              5764  0
i2c_core               21904  2 i2c_acpi_ec,i2c_sis96x
amd64_agp              12356  0
sis_agp                 8708  1
agpgart                34888  2 amd64_agp,sis_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
evdev                   9856  1
ext3                  135688  2
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
ohci_hcd               21892  0
usbcore               130692  4 ndiswrapper,ehci_hcd,ohci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  5
sis5513                17032  1
generic                 5124  0
thermal                13576  0
processor              23360  2 powernow_k8,thermal
fan                     4868  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit
```
```
dmesg
[17179569.184000] Linux version 2.6.15-25-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[17179569.184000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001bef0000 (usable)
[17179569.184000]  BIOS-e820: 000000001bef0000 - 000000001befa000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001befa000 - 000000001bf00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001bf00000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 446MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000f7fd0
[17179569.184000] On node 0 totalpages: 114416
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 110320 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7f60
[17179569.184000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1bef61d6
[17179569.184000] ACPI: FADT (v001 SiS    755F     0x06040000 PTL  0x000f4240) @ 0x1bef9e5f
[17179569.184000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x1bef9ed3
[17179569.184000] ACPI: MADT (v001 PTLTD         APIC   0x06040000  LTP 0x00000000) @ 0x1bef9f88
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1bef9fd8
[17179569.184000] ACPI: DSDT (v001 PTLTD       755 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x8008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:4 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ11 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dff00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1600.340 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.768000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.768000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)[17179569.776000] Memory: 443188k/457664k available (1976k kernel code, 13896k reserved, 606k data, 288k init, 0k highmem)
[17179569.776000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.856000] Calibrating delay using timer specific routine.. 3202.32 BogoMIPS (lpj=6404650)
[17179569.856000] Security Framework v1.0.0 initialized
[17179569.856000] SELinux:  Disabled at boot.
[17179569.856000] Mount-cache hash table entries: 512
[17179569.856000] CPU: After generic identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179569.856000] CPU: After vendor identify, caps: 078bfbff e3d3fbff 00000000 00000000 00000001 00000000 00000001
[17179569.856000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.856000] CPU: L2 Cache: 1024K (64 bytes/line)
[17179569.856000] CPU: After all inits, caps: 078bfbff e3d3fbff 00000000 00000410 00000001 00000000 00000001
[17179569.856000] mtrr: v2.0 (20020519)
[17179569.856000] CPU: AMD Turion(tm) 64 Mobile Technology ML-30 stepping 02
[17179569.856000] Enabling fast FPU save and restore... done.
[17179569.856000] Enabling unmasked SIMD FPU exception support... done.
[17179569.856000] Checking 'hlt' instruction... OK.
[17179569.872000] checking if image is initramfs... it is
[17179570.480000] Freeing initrd memory: 6614k freed
[17179570.488000] ACPI: Looking for DSDT ... not found!
[17179570.492000] ENABLING IO-APIC IRQs
[17179570.492000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[17179570.636000] NET: Registered protocol family 16
[17179570.636000] EISA bus registered
[17179570.636000] ACPI: bus type pci registered
[17179570.636000] PCI: PCI BIOS revision 2.10 entry at 0xfd776, last bus=1
[17179570.636000] PCI: Using configuration type 1
[17179570.636000] ACPI: Subsystem revision 20051216
[17179570.636000] ACPI: Interpreter enabled
[17179570.636000] ACPI: Using IOAPIC for interrupt routing
[17179570.636000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.636000] PCI: Probing PCI hardware (bus 00)
[17179570.640000] Uncovering SIS963 that hid as a SIS503 (compatible=0)
[17179570.640000] Enabling SiS 96x SMBus.
[17179570.640000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179570.640000] Boot video device is 0000:01:00.0
[17179570.640000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.644000] ACPI: Embedded Controller [EC0] (gpe 25) interrupt mode.
[17179570.660000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 *7 9 10 11)
[17179570.660000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179570.660000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 7 9 10 11)
[17179570.660000] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 7 9 10 11)
[17179570.660000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *9 10 11)
[17179570.660000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11)
[17179570.660000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 11) *0, disabled.
[17179570.660000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 *10 11)
[17179570.660000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.660000] pnp: PnP ACPI init
[17179570.660000] pnp: PnP ACPI: found 7 devices
[17179570.660000] PnPBIOS: Disabled by ACPI PNP
[17179570.660000] PCI: Using ACPI for IRQ routing
[17179570.660000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.664000] pnp: 00:03: ioport range 0x8000-0x807f could not be reserved
[17179570.664000] pnp: 00:03: ioport range 0x8080-0x80ff has been reserved
[17179570.664000] pnp: 00:03: ioport range 0x8100-0x811f has been reserved
[17179570.664000] pnp: 00:03: ioport range 0x4d0-0x4d1 has been reserved
[17179570.664000] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[17179570.664000] PCI: Bridge: 0000:00:01.0
[17179570.664000]   IO window: a000-afff
[17179570.664000]   MEM window: e2100000-e21fffff
[17179570.664000]   PREFETCH window: e8000000-efffffff
[17179570.664000] PCI: Bus 2, cardbus bridge: 0000:00:06.0
[17179570.664000]   IO window: 00002400-000024ff
[17179570.664000]   IO window: 00002800-000028ff
[17179570.664000]   PREFETCH window: 30000000-31ffffff
[17179570.664000]   MEM window: 32000000-33ffffff
[17179570.664000] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
[17179570.664000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179570.664000] Simple Boot Flag at 0x38 set to 0x1
[17179570.664000] audit: initializing netlink socket (disabled)
[17179570.664000] audit(1151437155.664:1): initialized
[17179570.664000] VFS: Disk quotas dquot_6.5.1
[17179570.664000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.664000] Initializing Cryptographic API
[17179570.664000] io scheduler noop registered
[17179570.664000] io scheduler anticipatory registered
[17179570.664000] io scheduler deadline registered
[17179570.664000] io scheduler cfq registered
[17179570.664000] isapnp: Scanning for PnP cards...
[17179571.016000] isapnp: No Plug & Play device found
[17179571.028000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179571.036000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179571.040000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.040000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179571.040000] ACPI: PCI Interrupt 0000:00:02.6[C] -> GSI 18 (level, low) -> IRQ 177
[17179571.040000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[17179571.040000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.040000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.040000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.040000] mice: PS/2 mouse device common for all mice
[17179571.040000] EISA: Probing bus 0 at eisa.0
[17179571.040000] Cannot allocate resource for EISA slot 1
[17179571.040000] Cannot allocate resource for EISA slot 2
[17179571.040000] Cannot allocate resource for EISA slot 8
[17179571.040000] EISA: Detected 0 cards.
[17179571.040000] NET: Registered protocol family 2
[17179571.080000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.080000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.080000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[17179571.080000] TCP: Hash tables configured (established 16384 bind 16384)
[17179571.080000] TCP reno registered
[17179571.080000] TCP bic registered
[17179571.080000] NET: Registered protocol family 1
[17179571.080000] NET: Registered protocol family 8
[17179571.080000] NET: Registered protocol family 20
[17179571.080000] Using IPI Shortcut mode
[17179571.080000] ACPI wakeup devices:
[17179571.080000] PCI0  LAN MODM USB0 USB1 USB2 USB3
[17179571.080000] ACPI: (supports S0 S3 S4 S5)
[17179571.080000] Freeing unused kernel memory: 288k freed
[17179571.080000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179571.124000] vga16fb: initializing
[17179571.124000] vga16fb: mapped to 0xc00a0000
[17179571.200000] Console: switching to colour frame buffer device 80x25
[17179571.200000] fb0: VGA16 VGA frame buffer device
[17179572.244000] Capability LSM initialized
[17179572.276000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179572.276000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179572.280000] ACPI: Thermal Zone [THRM] (53 C)
[17179572.628000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179572.628000] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 185
[17179572.628000] SIS5513: chipset revision 0
[17179572.628000] SIS5513: not 100% native mode: will probe irqs later
[17179572.628000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179572.628000]     ide0: BM-DMA at 0x2000-0x2007, BIOS settings: hda:DMA, hdb:pio
[17179572.628000]     ide1: BM-DMA at 0x2008-0x200f, BIOS settings: hdc:DMA, hdd:pio
[17179572.628000] Probing IDE interface ide0...
[17179572.916000] hda: IC25N060ATMR04-0, ATA DISK drive
[17179573.588000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.612000] Probing IDE interface ide1...
[17179574.348000] hdc: PIONEER DVD-RW DVR-K15RA, ATAPI CD/DVD-ROM drive
[17179575.020000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.036000] hda: max request size: 1024KiB
[17179575.044000] hda: 117210240 sectors (60011 MB) w/7884KiB Cache, CHS=16383/255/63, UDMA(100)
[17179575.044000] hda: cache flushes supported
[17179575.044000]  hda: hda1 hda2 hda4 < hda5 hda6 >
[17179575.144000] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[17179575.144000] Uniform CD-ROM driver Revision: 3.20
[17179575.776000] usbcore: registered new driver usbfs
[17179575.776000] usbcore: registered new driver hub
[17179575.776000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179575.776000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 193
[17179575.776000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179575.996000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[17179575.996000] ohci_hcd 0000:00:03.0: irq 193, io mem 0xe2000000
[17179576.052000] hub 1-0:1.0: USB hub found
[17179576.052000] hub 1-0:1.0: 3 ports detected
[17179576.156000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 201
[17179576.156000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179576.360000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[17179576.360000] ohci_hcd 0000:00:03.1: irq 201, io mem 0xe2001000
[17179576.416000] hub 2-0:1.0: USB hub found
[17179576.416000] hub 2-0:1.0: 3 ports detected
[17179576.520000] ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 209
[17179576.520000] ehci_hcd 0000:00:03.2: EHCI Host Controller
[17179576.520000] PCI: cache line size of 64 is not supported by device 0000:00:03.2
[17179576.520000] ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[17179576.520000] ehci_hcd 0000:00:03.2: irq 209, io mem 0xe2002000
[17179576.520000] ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.520000] hub 3-0:1.0: USB hub found
[17179576.520000] hub 3-0:1.0: 6 ports detected
[17179576.836000] Attempting manual resume
[17179576.896000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.908000] kjournald starting.  Commit interval 5 seconds
[17179588.352000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.368000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.384000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.416000] agpgart: Detected SiS 760 chipset
[17179588.416000] agpgart: AGP aperture is 4M @ 0xe0000000
[17179588.528000] i2c-sis96x version 1.0.0
[17179588.528000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x8100
[17179588.620000] sis900.c: v1.08.09 Sep. 19 2005
[17179588.620000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179588.624000] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 13.
[17179588.632000] 0000:00:04.0: Using transceiver found at address 13 as default[17179588.632000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 169, 00:c0:9f:8d:44:15.
[17179588.992000] input: PC Speaker as /class/input/input1
[17179588.992000] Real Time Clock Driver v1.12
[17179589.024000] ACPI: PCI Interrupt 0000:00:06.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179589.024000] Yenta: CardBus bridge found at 0000:00:06.0 [1025:0083]
[17179589.024000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179589.024000] Yenta: Routing CardBus interrupts to PCI
[17179589.024000] Yenta TI: socket 0000:00:06.0, mfunc 0x00521d22, devctl 0x64
[17179589.256000] Yenta: ISA IRQ mask 0x06f8, PCI irq 169
[17179589.256000] Socket status: 30000020
[17179589.700000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[17179589.736000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179589.812000] ts: Compaq touchscreen protocol output
[17179589.916000] pccard: CardBus card inserted into slot 0
[17179590.016000] Loaded prism54 driver, version 1.2
[17179590.016000] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[17179590.016000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 19 (level, low) -> IRQ 169
[17179590.016000] eth1: uploading firmware...
[17179590.124000] cs: IO port probe 0x100-0x3af: clean.
[17179590.128000] cs: IO port probe 0x3e0-0x4ff: excluding 0x480-0x48f
[17179590.128000] cs: IO port probe 0x820-0x8ff: clean.
[17179590.128000] cs: IO port probe 0xc00-0xcf7: clean.
[17179590.128000] cs: IO port probe 0xa00-0xaff: clean.
[17179590.232000] eth1: firmware version: 1.0.4.3
[17179590.232000] eth1: firmware upload complete
[17179590.264000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 177
[17179590.324000] eth1: resetting device...
[17179590.324000] eth1: uploading firmware...
[17179590.404000] eth1: firmware version: 1.0.4.3
[17179590.404000] eth1: firmware upload complete
[17179591.084000] intel8x0_measure_ac97_clock: measured 55457 usecs
[17179591.084000] intel8x0: clocking to 48000
[17179591.332000] lp: driver loaded but no devices found
[17179591.376000] Adding 979920k swap on /dev/hda6.  Priority:-1 extents:1 across:979920k
[17179591.428000] eth1: no 'reset complete' IRQ seen - retrying
[17179591.428000] EXT3 FS on hda2, internal journal
[17179591.548000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179591.548000] md: bitmap version 4.39
[17179591.892000] eth0: Media Link On 100mbps full-duplex
[17179592.028000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179592.428000] eth1: no 'reset complete' IRQ seen - retrying
[17179592.428000] eth1: interface reset failure
[17179592.428000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[17179592.480000] eth1: resetting device...
[17179592.480000] eth1: uploading firmware...
[17179592.556000] NET: Registered protocol family 17
[17179592.628000] eth1: firmware version: 1.0.4.3
[17179592.628000] eth1: firmware upload complete
[17179592.684000] cdrom: open failed.
[17179593.628000] eth1: no 'reset complete' IRQ seen - retrying
[17179594.628000] eth1: no 'reset complete' IRQ seen - retrying
[17179594.628000] eth1: interface reset failure
[17179594.628000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[17179596.468000] NET: Registered protocol family 10
[17179596.468000] lo: Disabled Privacy Extensions
[17179596.468000] IPv6 over IPv4 tunneling driver
[17179598.584000] kjournald starting.  Commit interval 5 seconds
[17179598.588000] EXT3 FS on hda5, internal journal
[17179598.588000] EXT3-fs: mounted filesystem with ordered data mode.
[17179601.396000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17179603.016000] ACPI: AC Adapter [ACAD] (on-line)
[17179603.036000] ACPI: Battery Slot [BAT1] (battery present)
[17179603.108000] ACPI: Power Button (FF) [PWRF]
[17179603.108000] ACPI: Lid Switch [LID]
[17179603.108000] ACPI: Power Button (CM) [PWRB]
[17179603.108000] ACPI: Sleep Button (CM) [SLPB]
[17179603.192000] ibm_acpi: ec object not found
[17179603.220000] pcc_acpi: loading...
[17179603.660000] powernow-k8: Found 1 AMD Athlon 64 / Opteron processors (version 1.50.4)
[17179603.664000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x4 (1450 mV)
[17179603.664000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x16 (1000 mV)
[17179603.664000] cpu_init done, current fid 0x8, vid 0x4
[17179606.904000] eth0: no IPv6 routers present
[17179608.216000] ppdev: user-space parallel port driver
[17179608.516000] apm: BIOS not found.
[17179612.936000] eth1: resetting device...
[17179612.936000] eth1: uploading firmware...
[17179613.028000] eth1: firmware version: 1.0.4.3
[17179613.028000] eth1: firmware upload complete
[17179613.480000] Bluetooth: Core ver 2.8
[17179613.480000] NET: Registered protocol family 31
[17179613.480000] Bluetooth: HCI device and connection manager initialized
[17179613.480000] Bluetooth: HCI socket layer initialized
[17179613.780000] Bluetooth: L2CAP ver 2.8
[17179613.780000] Bluetooth: L2CAP socket layer initialized
[17179613.796000] Bluetooth: RFCOMM socket layer initialized
[17179613.796000] Bluetooth: RFCOMM TTY layer initialized
[17179613.796000] Bluetooth: RFCOMM ver 1.7
[17179614.028000] eth1: no 'reset complete' IRQ seen - retrying
[17179615.028000] eth1: no 'reset complete' IRQ seen - retrying
[17179615.028000] eth1: interface reset failure
[17179615.028000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[17179637.428000] eth0: no IPv6 routers present
[17181195.264000] eth1: resetting device...
[17181195.264000] eth1: uploading firmware...
[17181195.352000] eth1: firmware version: 1.0.4.3
[17181195.352000] eth1: firmware upload complete
[17181196.352000] eth1: no 'reset complete' IRQ seen - retrying
[17181197.352000] eth1: no 'reset complete' IRQ seen - retrying
[17181197.352000] eth1: interface reset failure
[17181197.352000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[17181204.680000] eth1: resetting device...
[17181204.680000] eth1: uploading firmware...
[17181204.764000] eth1: firmware version: 1.0.4.3
[17181204.764000] eth1: firmware upload complete
[17181205.768000] eth1: no 'reset complete' IRQ seen - retrying
[17181206.768000] eth1: no 'reset complete' IRQ seen - retrying
[17181206.768000] eth1: interface reset failure
[17181206.768000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[17181206.820000] eth1: resetting device...
[17181206.820000] eth1: uploading firmware...
[17181206.904000] eth1: firmware version: 1.0.4.3
[17181206.904000] eth1: firmware upload complete
[17181207.904000] eth1: no 'reset complete' IRQ seen - retrying
[17181208.904000] eth1: no 'reset complete' IRQ seen - retrying
[17181208.904000] eth1: interface reset failure
[17181208.904000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[17181711.620000] eth1: resetting device...
[17181711.620000] eth1: uploading firmware...
[17181711.744000] eth1: firmware version: 1.0.4.3
[17181711.744000] eth1: firmware upload complete
[17181712.744000] eth1: no 'reset complete' IRQ seen - retrying
[17181713.744000] eth1: no 'reset complete' IRQ seen - retrying
[17181713.744000] eth1: interface reset failure
[17181713.744000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[17181724.900000] eth1: resetting device...
[17181724.900000] eth1: uploading firmware...
[17181724.984000] eth1: firmware version: 1.0.4.3
[17181724.988000] eth1: firmware upload complete
[17181725.988000] eth1: no 'reset complete' IRQ seen - retrying
[17181726.988000] eth1: no 'reset complete' IRQ seen - retrying
[17181726.988000] eth1: interface reset failure
[17181726.988000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[17181727.040000] eth1: resetting device...
[17181727.040000] eth1: uploading firmware...
[17181727.124000] eth1: firmware version: 1.0.4.3
[17181727.124000] eth1: firmware upload complete
[17181728.124000] eth1: no 'reset complete' IRQ seen - retrying
[17181729.124000] eth1: no 'reset complete' IRQ seen - retrying
[17181729.124000] eth1: interface reset failure
[17181729.124000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[17181838.312000] eth1: resetting device...
[17181838.312000] eth1: uploading firmware...
[17181838.416000] eth1: firmware version: 1.0.4.3
[17181838.416000] eth1: firmware upload complete
[17181839.416000] eth1: no 'reset complete' IRQ seen - retrying
[17181840.416000] eth1: no 'reset complete' IRQ seen - retrying
[17181840.416000] eth1: interface reset failure
[17181840.416000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
[17181840.468000] eth1: resetting device...
[17181840.468000] eth1: uploading firmware...
[17181840.552000] eth1: firmware version: 1.0.4.3
[17181840.552000] eth1: firmware upload complete
[17181841.552000] eth1: no 'reset complete' IRQ seen - retrying
[17181842.552000] eth1: no 'reset complete' IRQ seen - retrying
[17181842.552000] eth1: interface reset failure
[17181842.552000] prism54: Your card/socket may be faulty, or IRQ line too busy :(
```

with iwconfig the wireless extension has become eth1 not wlan0 and it is apparently not ready.

Can anyone tell me what has happened to wlan0 and my wireless network.

Many thanks in advance

---

### Post by mosestruong on 2006-07-30
I had the problem too and someone suggested to blacklist the bcm43xx module.

Edit /etc/modprobe.d/blacklist, and add
```
blacklist bcm43xx
```

Hope this helps.

---

