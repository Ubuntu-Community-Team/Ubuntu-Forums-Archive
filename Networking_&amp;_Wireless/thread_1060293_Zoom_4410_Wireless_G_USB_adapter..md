---
title: "Zoom 4410 Wireless G USB adapter."
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by Jimmymcnulty on 2009-02-04
Hi Im trying to find out if Zoom 4410 USB adapter is compatible with ubuntu. I have a BT homehub (dont ask why) but as I have no box upstairs where I wish the computer to be I would like to use a wireless connection. As per request on how to post a fault I am enclosing as much info as possible. Many thanks.


-desktop:~$  lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:08.0 Communication controller: Intel Corporation 536EP Data Fax Modem
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AR [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary)


desktop:~$ lsusb
Bus 004 Device 004: ID 046d:0a06 Logitech, Inc. 
Bus 004 Device 003: ID 046d:c51c Logitech, Inc. 
Bus 004 Device 002: ID 0451:2036 Texas Instruments, Inc. TUSB2036 Hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0803:4410 Zoom Telephonics, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:2f:85:af:f1  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe85:aff1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10865 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11277069 (11.2 MB)  TX bytes:1697976 (1.6 MB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 


-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


-desktop:~$ lsmod
Module                  Size  Used by
ipv6                  263972  8 
af_packet              25728  2 
binfmt_misc            16904  1 
radeon                147616  2 
drm                    86056  3 radeon
rfcomm                 44432  0 
sco                    18308  2 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 rfcomm,sco,bnep,l2cap
ppdev                  15620  0 
cpufreq_stats          13188  0 
cpufreq_userspace      11396  0 
cpufreq_conservative    14600  0 
cpufreq_powersave       9856  0 
cpufreq_ondemand       14988  0 
freq_table             12672  2 cpufreq_stats,cpufreq_ondemand
wmi                    14504  0 
video                  25104  0 
output                 11008  1 video
pci_slot               12552  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
lp                     17156  0 
joydev                 18368  0 
evdev                  17696  8 
psmouse                45200  0 
pcspkr                 10624  0 
serio_raw              13444  0 
snd_usb_audio          89728  1 
snd_usb_lib            24192  1 snd_usb_audio
snd_hwdep              15236  1 snd_usb_audio
snd_via82xx            32536  3 
gameport               19468  1 snd_via82xx
snd_ac97_codec        111652  1 snd_via82xx
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  4 snd_usb_audio,snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16136  2 snd_via82xx,snd_pcm
snd_mpu401_uart        15360  1 snd_via82xx
snd_seq_dummy          10884  0 
parport_pc             39204  1 
snd_seq_oss            38528  0 
parport                42604  3 ppdev,lp,parport_pc
snd_seq_midi           14336  0 
snd_rawmidi            29824  3 snd_usb_lib,snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  21 snd_usb_audio,snd_hwdep,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_viapro             15764  0 
soundcore              15328  1 snd
i2c_core               31892  1 i2c_viapro
via_ircc               32020  0 
button                 14224  0 
irda                  199612  1 via_ircc
crc_ccitt              10112  1 irda
via_agp                16256  1 
shpchp                 37908  0 
pci_hotplug            35236  1 shpchp
agpgart                42184  2 drm,via_agp
ext3                  133256  1 
jbd                    55444  1 ext3
mbcache                16004  1 ext3
usbhid                 35840  0 
hid                    50560  1 usbhid
sd_mod                 42264  3 
crc_t10dif              9984  1 sd_mod
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sg                     39732  0 
ata_generic            12932  0 
pata_via               16132  2 
pata_acpi              12160  0 
libata                177312  3 ata_generic,pata_via,pata_acpi
via_rhine              30216  0 
mii                    13440  1 via_rhine
scsi_mod              155212  4 sd_mod,sr_mod,sg,libata
dock                   16656  1 libata
uhci_hcd               30736  0 
ehci_hcd               43276  0 
usbcore               148848  6 snd_usb_audio,snd_usb_lib,usbhid,uhci_hcd,ehci_hcd
thermal                23708  0 
processor              42156  2 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

desktop:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-generic (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 06:42:44 UTC 2008 (Ubuntu 2.6.27-7.14-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fff0000 (usable)
[    0.000000]  BIOS-e820: 000000001fff0000 - 000000001fff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001fff3000 - 0000000020000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] last_pfn = 0x1fff0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 1fff0000 @ 7000-d000
[    0.000000] RAMDISK: 1f813000 - 1ffdff9e
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP 000F76E0, 0014 (r0 KM266P)
[    0.000000] ACPI: RSDT 1FFF3000, 002C (r1 KM266P AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 1FFF3040, 0074 (r1 KM266P AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 1FFF30C0, 4004 (r1 KM266P AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 1FFF0000, 0040
[    0.000000] ACPI: APIC 1FFF7100, 005A (r1 KM266P AWRDACPI 42302E31 AWRD        0)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 1fff0000
[    0.000000]   low ram: 00000000 - 1fff0000
[    0.000000]   bootmap 00002000 - 00006000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 001fff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c0a20]    TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[    0.000000]   #4 [001f813000 - 001ffdff9e]          RAMDISK ==> [001f813000 - 001ffdff9e]
[    0.000000]   #5 [00005c1000 - 00005c4000]    INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[    0.000000]   #6 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
[    0.000000]   #8 [0000002000 - 0000006000]          BOOTMAP ==> [0000002000 - 0000006000]
[    0.000000] found SMP MP-table at [c00f5bc0] 000f5bc0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0001fff0
[    0.000000]   HighMem  0x0001fff0 -> 0x0001fff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0001fff0
[    0.000000] On node 0 totalpages: 130959
[    0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c1000000
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 125844 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 129807
[    0.000000] Kernel command line: root=UUID=ef12d77e-0202-428a-bf50-6b7f1c2c3942 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.

googaw@googaw-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:11:2f:85:af:f1
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=192.168.1.64 latency=32 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2a:03:03:c2:74:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


desktop:~$ lsb_release -d
Description:	Ubuntu 8.10


desktop:~$ uname -mr
2.6.27-7-generic i686


desktop:~$ sudo /etc/init.d/networking restart
[sudo] password for : 
 * Reconfiguring network interfaces...                                                                                                       Ignoring unknown interface eth0=eth0.

I realise this is now an obscenely long message and Im sure a lot of the information is irrelevent but I wasnt sure what to leave in or out so just followed the guide to the letter. Any help would be greatfully recieved.

James.

---

### Post by Jimmymcnulty on 2009-02-05
Anyone please?

---

### Post by hkfczrqj on 2009-02-26
It seems that it is supported by ndiswrapper... 

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/zoom-4410-wireless-g-usb-adapter-any-chance-ill-get-this-working-544431/]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/zoom-4410-wireless-g-usb-adapter-any-chance-ill-get-this-working-544431/")

---

### Post by RealGomer on 2010-07-26
If you have the same usb in windows, check the driver info for it. Then go to [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2). This is the link for RALINK drivers for Linux. I finally found the drivers for their 4411 Wireless-N there. Now to figure out how to install them.

---

