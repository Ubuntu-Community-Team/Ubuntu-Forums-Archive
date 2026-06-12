---
title: "Onboard wired NIC not recognized in 6.06"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by RotorHead on 2006-06-14
I just installed Dapper from the live CD, so far all is well except for one thing. My onboard wired NIC is not being recognized by the OS. It worked fine under Breezy 5.10

It is an onboard intigrated NIC from Via on a DVD266u-RN Motherboard. 

South Bridge integrated VT8231, VT8233, VT8235 & VT8237 (Rhine & Rhine II) ( VT8237 VT8235 VT8231 VT8233/A/C VT6107 )

I can get the driver for it, in sorce form, from here [http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2590&SubCatID=124](http://www.viaarena.com/default.aspx?PageID=420&OSID=25&CatID=2590&SubCatID=124)

Any help with this problem would be great. 
Thanks

---

### Post by ns2048 on 2006-06-14
Can you post the output of the following commands.
* lspci -vv
* lspci -n
* lsmod
* cat -b /var/log/dmesg

--ns2048

---

### Post by RotorHead on 2006-06-14
[QUOTE=ns2048]Can you post the output of the following commands.
* lspci -vv
* lspci -n
* lsmod
* cat -b /var/log/dmesg

--ns2048[/QUOTE]

lspci -vv returns nothing
lspci -n returns nothing

lsmod .......I get a list of stuff, nothing relating to a network card 

cat -b /var/log/dmesg .......samething here nothing showing any network related info.

Sorry but I can't actually post what is in the logs. I am posting this from my windows box because the linux one cannot connect. 

Will loading the driver I linked above help in any way?

---

### Post by ns2048 on 2006-06-14
Something is very strange if lspci doesn't output anything. It's difficult to render help if we don't know any details about your system.
--ns2048

---

### Post by RotorHead on 2006-06-15
Here is the output from lsmod

eugene@eugene-desktop:~$ lsmod
Module                  Size  Used by
sg                     37920  0
scsi_mod              139496  1 sg
nls_cp437               5888  0
isofs                  37688  0
udf                    88452  0
ipv6                  265600  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
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
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
af_packet              22920  0
dm_mod                 58936  1
md_mod                 72532  0
parport_pc             35780  0
lp                     11844  0
parport                36296  3 ppdev,parport_pc,lp
floppy                 62148  0
pcspkr                  2180  0
tsdev                   8000  0
psmouse                36228  0
serio_raw               7300  0
rtc                    13492  0
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
ide_generic             1536  0
thermal                13576  0
processor              23360  1 thermal
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
eugene@eugene-desktop:~$

---

### Post by RotorHead on 2006-06-15
Here is the output from cat

eugene@eugene-desktop:~$ cat -b /var/log/dmesg
     1  [4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
     2  [4294667.296000] BIOS-provided physical RAM map:
     3  [4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
     4  [4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
     5  [4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
     6  [4294667.296000]  BIOS-e820: 0000000000100000 - 0000000017ff0000 (usable)
     7  [4294667.296000]  BIOS-e820: 0000000017ff0000 - 0000000017ff3000 (ACPI NVS)
     8  [4294667.296000]  BIOS-e820: 0000000017ff3000 - 0000000018000000 (ACPI data)
     9  [4294667.296000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
    10  [4294667.296000] 0MB HIGHMEM available.
    11  [4294667.296000] 383MB LOWMEM available.
    12  [4294667.296000] found SMP MP-table at 000f4f80
    13  [4294667.296000] On node 0 totalpages: 98288
    14  [4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
    15  [4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
    16  [4294667.296000]   Normal zone: 94192 pages, LIFO batch:31
    17  [4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
    18  [4294667.296000] DMI 2.2 present.
    19  [4294667.296000] ACPI: RSDP (v000 VIA694 ) @ 0x000f68f0
    20  [4294667.296000] ACPI: RSDT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x17ff3000
    21  [4294667.296000] ACPI: FADT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x17ff3040
    22  [4294667.296000] ACPI: MADT (v001 VIA694 AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x17ff6580
    23  [4294667.296000] ACPI: DSDT (v001 VIA694 AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
    24  [4294667.296000] ACPI: PM-Timer IO Port: 0x4008
    25  [4294667.296000] ACPI: Local APIC address 0xfee00000
    26  [4294667.296000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
    27  [4294667.296000] Processor #0 6:8 APIC version 17
    28  [4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
    29  [4294667.296000] Processor #1 6:8 APIC version 17
    30  [4294667.296000] WARNING: NR_CPUS limit of 1 reached.  Processor ignored.
    31  [4294667.296000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])    
    32  [4294667.296000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
    33  [4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
    34  [4294667.296000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
    35  [4294667.296000] ACPI: IRQ0 used by override.
    36  [4294667.296000] ACPI: IRQ2 used by override.
    37  [4294667.296000] ACPI: IRQ9 used by override.
    38  [4294667.296000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
    39  [4294667.296000] Using ACPI (MADT) for SMP configuration information
    40  [4294667.296000] Allocating PCI resources starting at 20000000 (gap: 18000000:e6c00000)
    41  [4294667.296000] Built 1 zonelists
    42  [4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
    43  [4294667.296000] mapped APIC to ffffd000 (fee00000)
    44  [4294667.296000] mapped IOAPIC to ffffc000 (fec00000)
    45  [4294667.296000] Initializing CPU#0
    46  [4294667.296000] PID hash table entries: 2048 (order: 11, 32768 bytes)
    47  [4294667.296000] Detected 1011.824 MHz processor.
    48  [4294667.296000] Using pmtmr for high-res timesource
    49  [4294667.296000] Console: colour VGA+ 80x25
    50  [4294670.875000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
    51  [4294670.876000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
    52  [4294670.903000] Memory: 378932k/393152k available (1976k kernel code, 13616k reserved, 606k data, 288k init, 0k highmem)
    53  [4294670.903000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
    54  [4294670.964000] Calibrating delay using timer specific routine.. 2023.96 BogoMIPS (lpj=1011981)
    55  [4294670.964000] Security Framework v1.0.0 initialized
    56  [4294670.964000] SELinux:  Disabled at boot.
    57  [4294670.964000] Mount-cache hash table entries: 512
    58  [4294670.964000] CPU: After generic identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
    59  [4294670.964000] CPU: After vendor identify, caps: 0383fbff 00000000 00000000 00000000 00000000 00000000 00000000
    60  [4294670.964000] CPU: L1 I cache: 16K, L1 D cache: 16K
    61  [4294670.964000] CPU: After all inits, caps: 0383fbff 00000000 00000000 00000040 00000000 00000000 00000000
    62  [4294670.964000] mtrr: v2.0 (20020519)
    63  [4294670.964000] CPU: Intel Pentium III (Coppermine) stepping 0a
    64  [4294670.964000] Enabling fast FPU save and restore... done.
    65  [4294670.964000] Enabling unmasked SIMD FPU exception support... done.
    66  [4294670.964000] Checking 'hlt' instruction... OK.
    67  [4294670.968000] checking if image is initramfs... it is
    68  [4294672.908000] Freeing initrd memory: 6836k freed
    69  [4294672.930000] ACPI: Looking for DSDT ... not found!
    70  [4294672.938000] ENABLING IO-APIC IRQs
    71  [4294672.938000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
    72  [4294673.049000] NET: Registered protocol family 16
    73  [4294673.049000] EISA bus registered
    74  [4294673.049000] ACPI: bus type pci registered
    75  [4294673.060000] PCI: PCI BIOS revision 2.10 entry at 0xfb3c0, last bus=1
    76  [4294673.060000] PCI: Using configuration type 1
    77  [4294673.061000] ACPI: Subsystem revision 20051216
    78  [4294673.075000] ACPI: Interpreter enabled
    79  [4294673.075000] ACPI: Using IOAPIC for interrupt routing
    80  [4294673.078000] ACPI: PCI Root Bridge [PCI0] (0000:00)
    81  [4294673.078000] PCI: Probing PCI hardware (bus 00)
    82  [4294673.078000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
    83  [4294673.088000] Boot video device is 0000:01:00.0
    84  [4294673.088000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
    85  [4294673.092000] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
    86  [4294673.094000] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
    87  [4294673.096000] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 11 12 14 15) *0, disabled.
    88  [4294673.097000] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
    89  [4294673.112000] Linux Plug and Play Support v0.97 (c) Adam Belay
    90  [4294673.112000] pnp: PnP ACPI init
    91  [4294673.128000] pnp: PnP ACPI: found 11 devices
    92  [4294673.128000] PnPBIOS: Disabled by ACPI PNP
    93  [4294673.128000] PCI: Using ACPI for IRQ routing
    94  [4294673.128000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
    95  [4294673.131000] PCI: Bridge: 0000:00:01.0
    96  [4294673.131000]   IO window: disabled.
    97  [4294673.131000]   MEM window: dc000000-ddffffff
    98  [4294673.131000]   PREFETCH window: d0000000-d7ffffff
    99  [4294673.131000] PCI: Setting latency timer of device 0000:00:01.0 to 64   
   100  [4294673.135000] audit: initializing netlink socket (disabled)
   101  [4294673.135000] audit(1150325084.134:1): initialized
   102  [4294673.135000] VFS: Disk quotas dquot_6.5.1
   103  [4294673.135000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
   104  [4294673.135000] Initializing Cryptographic API
   105  [4294673.135000] io scheduler noop registered
   106  [4294673.135000] io scheduler anticipatory registered
   107  [4294673.135000] io scheduler deadline registered
   108  [4294673.135000] io scheduler cfq registered
   109  [4294673.136000] isapnp: Scanning for PnP cards...
   110  [4294673.493000] isapnp: No Plug & Play device found
   111  [4294673.617000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
   112  [4294673.619000] serio: i8042 AUX port at 0x60,0x64 irq 12
   113  [4294673.620000] serio: i8042 KBD port at 0x60,0x64 irq 1
   114  [4294673.620000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
   115  [4294673.620000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
   116  [4294673.621000] serial8250: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
   117  [4294673.634000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
   118  [4294673.635000] 00:08: ttyS3 at I/O 0x2e8 (irq = 3) is a 16550A
   119  [4294673.638000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
   120  [4294673.638000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
   121  [4294673.638000] ide: Assuming 50MHz system bus speed for PIO modes; override with idebus=xx
   122  [4294673.639000] mice: PS/2 mouse device common for all mice
   123  [4294673.640000] EISA: Probing bus 0 at eisa.0
   124  [4294673.640000] Cannot allocate resource for EISA slot 1
   125  [4294673.640000] Cannot allocate resource for EISA slot 4
   126  [4294673.640000] EISA: Detected 0 cards.
   127  [4294673.640000] NET: Registered protocol family 2
   128  [4294673.650000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
   129  [4294673.650000] TCP established hash table entries: 16384 (order: 4, 65536 bytes)
   130  [4294673.650000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
   131  [4294673.650000] TCP: Hash tables configured (established 16384 bind 16384)
   132  [4294673.650000] TCP reno registered
   133  [4294673.651000] TCP bic registered
   134  [4294673.651000] NET: Registered protocol family 1
   135  [4294673.651000] NET: Registered protocol family 8
   136  [4294673.651000] NET: Registered protocol family 20
   137  [4294673.651000] Using IPI Shortcut mode
   138  [4294673.651000] ACPI wakeup devices:
   139  [4294673.651000] PCI0 USB0 USB1 USB2 LAN0 UAR1
   140  [4294673.651000] ACPI: (supports S0 S1 S4 S5)
   141  [4294673.651000] Freeing unused kernel memory: 288k freed
   142  [4294673.668000] input: AT Translated Set 2 keyboard as /class/input/input0
   143  [4294673.830000] vga16fb: initializing
   144  [4294673.830000] vga16fb: mapped to 0xc00a0000
   145  [4294673.949000] Console: switching to colour frame buffer device 80x25
   146  [4294673.949000] fb0: VGA16 VGA frame buffer device
   147  [4294675.123000] Capability LSM initialized
   148  [4294675.226000] ACPI: Fan [FAN] (on)
   149  [4294675.256000] ACPI: Thermal Zone [THRM] (36 C)
   150  [4294676.886000] Probing IDE interface ide0...
   151  [4294677.272000] hda: WDC WD600BB-00CAA1, ATA DISK drive
   152  [4294677.680000] hdb: LITE-ON LTR-48246S, ATAPI CD/DVD-ROM drive
   153  [4294677.731000] Probing IDE interface ide1...
   154  [4294678.250000] Probing IDE interface ide2...
   155  [4294678.763000] Probing IDE interface ide3...
   156  [4294679.276000] Probing IDE interface ide4...
   157  [4294679.789000] Probing IDE interface ide5...
   158  [4294680.302000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
   159  [4294680.330000] hda: max request size: 128KiB
   160  [4294680.343000] hda: 117231408 sectors (60022 MB) w/2048KiB Cache, CHS=65535/16/63
   161  [4294680.343000] hda: cache flushes not supported
   162  [4294680.343000]  hda: hda1 hda2 < hda5 >
   163  [4294680.381000] hdb: ATAPI 48X CD-ROM CD-R/RW drive, 2048kB Cache
   164  [4294680.381000] Uniform CD-ROM driver Revision: 3.20
   165  [4294680.770000] Attempting manual resume
   166  [4294680.852000] EXT3-fs: mounted filesystem with ordered data mode.
   167  [4294680.873000] kjournald starting.  Commit interval 5 seconds
   168  [4294713.354000] Real Time Clock Driver v1.12
   169  [4294713.603000] input: PS2++ Logitech MX Mouse as /class/input/input1
   170  [4294713.736000] ts: Compaq touchscreen protocol output
   171  [4294713.742000] input: PC Speaker as /class/input/input2
   172  [4294714.464000] Floppy drive(s): fd0 is 1.44M
   173  [4294714.479000] FDC 0 is a post-1991 82077
   174  [4294715.300000] lp: driver loaded but no devices found
   175  [4294715.466000] Adding 1132540k swap on /dev/hda5.  Priority:-1 extents:1 across:1132540k
   176  [4294715.568000] EXT3 FS on hda1, internal journal
   177  [4294715.956000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
   178  [4294715.956000] md: bitmap version 4.39
   179  [4294716.711000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
   180  [4294717.461000] cdrom: open failed.
   181  [4294719.977000] NET: Registered protocol family 17
eugene@eugene-desktop:~$

---

### Post by ns2048 on 2006-06-15
The output of 'lsmod' and 'dmesg' helps -- have you tried to manually load the 'via-rhine' module which is standard with the stock Ubuntu kernel.
--ns2048

---

### Post by RotorHead on 2006-06-15
No I have not tyied that yet. 

I'm sorry to say that I will need help to load the module. If you could advise, that would be great.

---

### Post by ns2048 on 2006-06-15
Oops, sorry -- just run 'modprobe via-rhine', then run 'dmesg' to see if your adapter was detected by the module.

This module is located in '/lib/modules/2.6.15-23-386/kernel/drivers/net'
--ns2048

---

### Post by RotorHead on 2006-06-15
I get the following errors when trying to load the module

eugene@eugene-desktop:~$ modprobe via-rhine
WARNING: Error inserting mii (/lib/modules/2.6.15-23-386/kernel/drivers/net/mii.ko): Operation not permitted
FATAL: Error inserting via_rhine (/lib/modules/2.6.15-23-386/kernel/drivers/net/via-rhine.ko): Operation not permitted
eugene@eugene-desktop:~$

---

### Post by ns2048 on 2006-06-15
Oops again -- run 'sudo modprobe via-rhine'. Type your password when prompted.
--ns2048

---

### Post by RotorHead on 2006-06-15
Ok cool, it shows in the dmesg as

[4318959.79400] via-rhine.c:v1.10-lk1.2.0-2.6 june-10-2004 Written by Donald Beker

---

### Post by RotorHead on 2006-06-15
It's also showing in the lsmod output as

via_rhine 23940 0

---

### Post by ns2048 on 2006-06-15
Does 'ifconfig' show an eth0 interface?
--ns2048

---

### Post by RotorHead on 2006-06-15
No, it just has one entry for 'lo'

---

### Post by ns2048 on 2006-06-15
Can you post the contents of '/etc/network/interfaces'?
--ns2048

---

### Post by RotorHead on 2006-06-15
it look like this....

auto lo 
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

---

### Post by ns2048 on 2006-06-15
I'm stumped... can't guess what hardware is in your system. Maybe you can search Google.
--ns2048

---

### Post by RotorHead on 2006-06-15
There is a link to the sorce file for the driver in my first post. If I could get that installed, I think I might be able to get the nic working.

Problem is, I dont know how to compile a driver from sorce code and install it.

---

### Post by RotorHead on 2006-06-15
Under Breezy this Nic was identified as (Via Technologies, Inc. VT6102 [Rhine-II]) 

It worked with no problems under Breezy.

---

### Post by RotorHead on 2006-06-16
Problem solved.......I just did a fresh install of Breezy :( 

It looks like Dapper is not quite ready for prime time......I will wait until things have been ironed out. 

Thanks for your time.

---

### Post by lighty14 on 2006-07-06
I have a VIA Rhine on my laptop. I haven't been able to experiment too heavily, but the fault probably doesn't lie directly in Dapper (I have the same problem), I believe that the problem may be something that got botched in that particular kernel version. When I have some more time I will be looking into this problem and maybe post some advice here.

---

### Post by rosserver on 2008-02-25
I also have 2 of the DVD266u-RN mobo (the via apollo Pro266T chipset) and while the onboard nic will not detect, thru experimenting I have noticed that NO nic card of any type will auto detect in 6.06 or 7.04.  It always says that "firewire is installed" but this workstation/serverboard (ofcourse) has no firewire.  The network interface must be improperly identified as firewire.

I have tried Intel, Lynksys, realtec, and znxy cards as well as the onboard nic.

I am having no such problems with any other Motherboard and even my other Iwill boards w/different chipsets work fine.

---

### Post by rosserver on 2008-02-25
Yes, 7.10 (while it has all sorts of new issues w/this mobo) seems to have the NIC issue worked out.

---

