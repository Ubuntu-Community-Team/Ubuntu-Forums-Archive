---
title: "HELP! No Ethernet or Wireless!"
date: 2009-06-20
forum: Networking &amp; Wireless
---

### Post by Webtiger on 2009-06-20
WARNING.... COMPLETE NOOBIE!!!!!
 
I am using a Forensics CD, DEFT, and have installed it on my HD as well. It runs Ubuntu 8.10 with Xfce as the desktop GUI.
I'm having a LOT of problems with the networking.
 
THERE IS NONE!!!!
No LAN or wireless is available on this machine and it's driving me completely insane.
 
The hardware is being identified, etc but when I go to find the Network Manager and net-tools there not in the GUI toolbar even though Package Mangler shows them as installed.
 
I don't care if wireless works via the Linksys USB adapter or the onboard Broadcom radio as long as it works.
I'm rather suprised the LAN doesn't work
 
I have spent the past 2 days futzing around with re-installing, following threads to "fix" networking, but with zero success.
 
This machine is a dual boot setup, Windows 7 Beta and Ubuntu. 
Naturally I have none of this nonsense when in Windows.
 
The sorry details:
 
HP dv8000 Notebook
AMD Turion64 CPU
2 Gigs Ram
Dual HD's
4 USB ports
SD slot, etc, etc, etc
On board "BroadCom" wireless
On board Realtek NIC
LinkSys USB WUSB54GC wireless adapter
 
 
**lspci -nn | grep "Broadcom"**
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
 
**lsusb**
Bus 003 Device 003: ID 13fe:1f00 Kingston Technology Company Inc. DataTraveler 2.0 4GB Flash Drive
Bus 003 Device 002: ID 13b1:0020 Linksys WUSB54GC 802.11g Adapter [ralink rt73]
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
**ifconfig**
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:6 errors:0 dropped:0 overruns:0 frame:0
TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:300 (300.0 B) TX bytes:300 (300.0 B)
 
 
**iwconfig**
lo no wireless extensions.
eth0 no wireless extensions.
wmaster0 no wireless extensions.
wlan0 IEEE 802.11bg ESSID:"" 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Tx-Power=0 dBm 
Retry min limit:7 RTS thr:off Fragment thr=2352 B 
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
wmaster1 no wireless extensions.
wlan1 IEEE 802.11bg ESSID:"" 
Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated 
Tx-Power=0 dBm 
Retry min limit:7 RTS thr:off Fragment thr=2352 B 
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
 
**lsmod** 
Module Size Used by
nls_iso8859_1 12032 1 
vfat 18816 1 
fat 57376 1 vfat
ipv6 263972 8 
radeon 147616 2 
drm 86056 3 radeon
usb_storage 81728 1 
libusual 27156 1 usb_storage
powernow_k8 22148 0 
cpufreq_userspace 11396 0 
cpufreq_stats 13188 0 
cpufreq_powersave 9856 0 
cpufreq_ondemand 14988 1 
freq_table 12672 3 powernow_k8,cpufreq_stats,cpufreq_ondemand
cpufreq_conservative 14600 0 
sbs 19464 0 
sbshc 13440 1 sbs
pci_slot 12552 0 
container 11520 0 
iptable_filter 10752 0 
ip_tables 19600 1 iptable_filter
x_tables 22916 1 ip_tables
joydev 18368 0 
pcmcia 43052 0 
arc4 9984 4 
ecb 10880 4 
crypto_blkcipher 25476 1 ecb
rt73usb 30464 0 
crc_itu_t 10112 1 rt73usb
rt2x00usb 18816 1 rt73usb
b43 131356 0 
rt2x00lib 36224 2 rt73usb,rt2x00usb
rfkill 17176 2 b43,rt2x00lib
mac80211 216820 3 rt2x00usb,b43,rt2x00lib
cfg80211 32392 2 rt2x00lib,mac80211
led_class 12164 2 b43,rt2x00lib
input_polldev 11912 1 b43
snd_atiixp_modem 20360 0 
snd_atiixp 24204 2 
snd_ac97_codec 111652 2 snd_atiixp_modem,snd_atiixp
ac97_bus 9856 1 snd_ac97_codec
snd_pcm_oss 46848 0 
snd_pcm 83204 4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
video 25104 0 
snd_mixer_oss 22784 1 snd_pcm_oss
output 11008 1 video
snd_seq_dummy 10884 0 
snd_seq_oss 38528 0 
snd_seq_midi 14336 0 
snd_rawmidi 29824 1 snd_seq_midi
battery 18436 0 
snd_seq_midi_event 15232 2 snd_seq_oss,snd_seq_midi
snd_seq 57776 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
tifm_7xx1 13824 0 
psmouse 45200 0 
sdhci_pci 15360 0 
sdhci 23940 1 sdhci_pci
snd_timer 29960 2 snd_pcm,snd_seq
yenta_socket 31756 1 
rsrc_nonstatic 19072 1 yenta_socket
snd_seq_device 15116 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ac 12292 0 
tifm_core 16028 1 tifm_7xx1
mmc_core 58268 1 sdhci
serio_raw 13444 0 
ati_agp 14988 0 
pcmcia_core 43412 3 pcmcia,yenta_socket,rsrc_nonstatic
wmi 14504 0 
snd 63268 15 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
button 14224 0 
i2c_piix4 16144 0 
shpchp 37908 0 
agpgart 42184 2 drm,ati_agp
pcspkr 10624 0 
evdev 17696 10 
k8temp 12416 0 
i2c_core 31892 1 i2c_piix4
soundcore 15328 1 snd
pci_hotplug 35236 1 shpchp
snd_page_alloc 16136 3 snd_atiixp_modem,snd_atiixp,snd_pcm
aufs 169892 1 
exportfs 12544 1 aufs
squashfs 46600 1 
loop 23180 2 
nls_cp437 13696 2 
isofs 40100 1 
ext3 133256 0 
jbd 55444 1 ext3
mbcache 16004 1 ext3
sr_mod 22212 1 
cdrom 43168 1 sr_mod
sd_mod 42264 2 
crc_t10dif 9984 1 sd_mod
sg 39732 0 
pata_acpi 12160 0 
ata_generic 12932 0 
8139cp 27520 0 
ohci1394 37936 0 
pata_atiixp 12800 1 
8139too 31616 0 
mii 13440 2 8139cp,8139too
ieee1394 96324 1 ohci1394
ssb 40580 1 b43
libata 177312 3 pata_acpi,ata_generic,pata_atiixp
scsi_mod 155212 5 usb_storage,sr_mod,sd_mod,sg,libata
dock 16656 1 libata
ehci_hcd 43276 0 
ohci_hcd 31888 0 
usbcore 148848 7 usb_storage,libusual,rt73usb,rt2x00usb,ehci_hcd,ohci_hcd
thermal 23708 0 
processor 42156 3 powernow_k8,thermal
fan 12548 0 
fbcon 47648 0 
tileblit 10880 1 fbcon
font 16512 1 fbcon
bitblit 13824 1 fbcon
softcursor 9984 1 bitblit
fuse 60828 1 
 
**lsmod | grep "led_class"**
led_class 12164 2 b43,rt2x00lib
root@deft:~# lsmod | grep "rt2x00lib"
rt2x00lib 36224 2 rt73usb,rt2x00usb
rfkill 17176 2 b43,rt2x00lib
mac80211 216820 3 rt2x00usb,b43,rt2x00lib
cfg80211 32392 2 rt2x00lib,mac80211
led_class 12164 2 b43,rt2x00lib
 
 
**dmesg**
[ 0.000000] Initializing cgroup subsys cpuset
[ 0.000000] Initializing cgroup subsys cpu
[ 0.000000] Linux version 2.6.27-7-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Wed Oct 22 00:29:18 UTC 2008 (Ubuntu 2.6.27-7.13-generic)
[ 0.000000] BIOS-provided physical RAM map:
[ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[ 0.000000] BIOS-e820: 00000000000d0000 - 0000000000100000 (reserved)
[ 0.000000] BIOS-e820: 0000000000100000 - 000000007fea0000 (usable)
[ 0.000000] BIOS-e820: 000000007fea0000 - 000000007feac000 (ACPI data)
[ 0.000000] BIOS-e820: 000000007feac000 - 000000007ff00000 (ACPI NVS)
[ 0.000000] BIOS-e820: 000000007ff00000 - 0000000080000000 (reserved)
[ 0.000000] BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[ 0.000000] BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[ 0.000000] last_pfn = 0x7fea0 max_arch_pfn = 0x100000
[ 0.000000] kernel direct mapping tables up to 38000000 @ 7000-c000
[ 0.000000] RAMDISK: 7ee5a000 - 7fe6f323
[ 0.000000] Allocated new RAMDISK: 005c4000 - 015d9323
[ 0.000000] Move RAMDISK from 000000007ee5a000 - 000000007fe6f322 to 005c4000 - 015d9322
[ 0.000000] DMI present.
[ 0.000000] ACPI: RSDP 000F7C20, 0014 (r0 PTLTD )
[ 0.000000] ACPI: RSDT 7FEA3E71, 0034 (r1 PTLTD RSDT 6040000 LTP 0)
[ 0.000000] ACPI: FACP 7FEABDD8, 0074 (r1 HP Piranha 6040000 ATI F4240)
[ 0.000000] ACPI: DSDT 7FEA3EA5, 7F33 (r1 HP 309B 6040000 MSFT 100000E)
[ 0.000000] ACPI: FACS 7FEACFC0, 0040
[ 0.000000] ACPI: SSDT 7FEABE4C, 0132 (r1 PTLTD POWERNOW 6040000 LTP 1)
[ 0.000000] ACPI: APIC 7FEABF7E, 0046 (r1 PTLTD APIC 6040000 LTP 0)
[ 0.000000] ACPI: MCFG 7FEABFC4, 003C (r1 HP PORSCHE 6040000 LOHR 0)
[ 0.000000] ACPI: DMI detected: Hewlett-Packard
[ 0.000000] 1150MB HIGHMEM available.
[ 0.000000] 896MB LOWMEM available.
[ 0.000000] mapped low ram: 0 - 38000000
[ 0.000000] low ram: 00000000 - 38000000
[ 0.000000] bootmap 00008000 - 0000f000
[ 0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[ 0.000000] #0 [0000000000 - 0000001000] BIOS data page ==> [0000000000 - 0000001000]
[ 0.000000] #1 [0000001000 - 0000002000] EX TRAMPOLINE ==> [0000001000 - 0000002000]
[ 0.000000] #2 [0000006000 - 0000007000] TRAMPOLINE ==> [0000006000 - 0000007000]
[ 0.000000] #3 [0000100000 - 00005c0a20] TEXT DATA BSS ==> [0000100000 - 00005c0a20]
[ 0.000000] #4 [00005c1000 - 00005c4000] INIT_PG_TABLE ==> [00005c1000 - 00005c4000]
[ 0.000000] #5 [000009f800 - 0000100000] BIOS reserved ==> [000009f800 - 0000100000]
[ 0.000000] #6 [0000007000 - 0000008000] PGTABLE ==> [0000007000 - 0000008000]
[ 0.000000] #7 [00005c4000 - 00015d9323] NEW RAMDISK ==> [00005c4000 - 00015d9323]
[ 0.000000] #8 [0000008000 - 000000f000] BOOTMAP ==> [0000008000 - 000000f000]
[ 0.000000] found SMP MP-table at [c00f7c50] 000f7c50
[ 0.000000] Zone PFN ranges:
[ 0.000000] DMA 0x00000000 -> 0x00001000
[ 0.000000] Normal 0x00001000 -> 0x00038000
[ 0.000000] HighMem 0x00038000 -> 0x0007fea0
[ 0.000000] Movable zone start PFN for each node
[ 0.000000] early_node_map[2] active PFN ranges
[ 0.000000] 0: 0x00000000 -> 0x0000009f
[ 0.000000] 0: 0x00000100 -> 0x0007fea0
[ 0.000000] On node 0 totalpages: 523839
[ 0.000000] free_area_init_node: node 0, pgdat c048a500, node_mem_map c15da000
[ 0.000000] DMA zone: 3963 pages, LIFO batch:0
[ 0.000000] Normal zone: 223300 pages, LIFO batch:31
[ 0.000000] HighMem zone: 291971 pages, LIFO batch:31
[ 0.000000] SB4X0 revision 0x11
[ 0.000000] Ignoring ACPI timer override.
[ 0.000000] If you got timer trouble try acpi_use_timer_override
[ 0.000000] ACPI: PM-Timer IO Port: 0x8008
[ 0.000000] ACPI: Local APIC address 0xfee00000
[ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[ 0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[ 0.000000] IOAPIC[0]: apic_id 1, version 33, address 0xfec00000, GSI 0-23
[ 0.000000] ACPI: IRQ9 used by override.
[ 0.000000] Enabling APIC mode: Flat. Using 1 I/O APICs
[ 0.000000] Using ACPI (MADT) for SMP configuration information
[ 0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[ 0.000000] mapped APIC to ffffb000 (fee00000)
[ 0.000000] mapped IOAPIC to ffffa000 (fec00000)
[ 0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[ 0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d0000
[ 0.000000] PM: Registered nosave memory: 00000000000d0000 - 0000000000100000
[ 0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[ 0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[ 0.000000] NR_CPUS: 64, nr_cpu_ids: 1, nr_node_ids 1
[ 0.000000] Built 1 zonelists in Zone order, mobility grouping on. Total pages: 519234
[ 0.000000] Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.gz rundeft=2 --
[ 0.000000] Enabling fast FPU save and restore... done.
[ 0.000000] Enabling unmasked SIMD FPU exception support... done.
[ 0.000000] Initializing CPU#0
[ 0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[ 0.000000] TSC: PIT calibration confirmed by PMTIMER.
[ 0.000000] TSC: using PIT calibration value
[ 0.000000] Detected 2392.997 MHz processor.
[ 0.004000] Console: colour VGA+ 80x25
[ 0.004000] console [tty0] enabled
[ 0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[ 0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[ 0.004000] Memory: 2053752k/2095744k available (2572k kernel code, 40688k reserved, 1160k data, 424k init, 1178240k highmem)
[ 0.004000] virtual kernel memory layout:
[ 0.004000] fixmap : 0xffc77000 - 0xfffff000 (3616 kB)
[ 0.004000] pkmap : 0xff400000 - 0xff800000 (4096 kB)
[ 0.004000] vmalloc : 0xf8800000 - 0xff3fe000 ( 107 MB)
[ 0.004000] lowmem : 0xc0000000 - 0xf8000000 ( 896 MB)
[ 0.004000] .init : 0xc04ab000 - 0xc0515000 ( 424 kB)
[ 0.004000] .data : 0xc038329a - 0xc04a5680 (1160 kB)
[ 0.004000] .text : 0xc0100000 - 0xc038329a (2572 kB)
[ 0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[ 0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[ 0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[ 0.004012] Calibrating delay loop (skipped), value calculated using timer frequency.. 4785.99 BogoMIPS (lpj=9571988)
[ 0.004119] Security Framework initialized
[ 0.004170] SELinux: Disabled at boot.
[ 0.004239] AppArmor: AppArmor initialized
[ 0.004288] Mount-cache hash table entries: 512
[ 0.004493] Initializing cgroup subsys ns
[ 0.004540] Initializing cgroup subsys cpuacct
[ 0.004583] Initializing cgroup subsys memory
[ 0.004639] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[ 0.004685] CPU: L2 Cache: 1024K (64 bytes/line)
[ 0.004741] Checking 'hlt' instruction... OK.
[ 0.020411] SMP alternatives: switching to UP code
[ 0.024019] Freeing SMP alternatives: 11k freed
[ 0.024065] ACPI: Core revision 20080609
[ 0.027028] ACPI: Checking initramfs for custom DSDT
[ 0.424239] ENABLING IO-APIC IRQs
[ 0.424461] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[ 0.464886] CPU0: AMD Turion(tm) 64 Mobile Technology ML-44 stepping 02
[ 0.468029] Brought up 1 CPUs
[ 0.468029] Total of 1 processors activated (4785.99 BogoMIPS).
[ 0.468029] CPU0 attaching sched-domain:
[ 0.468029] domain 0: span 0 level CPU
[ 0.468029] groups: 0
[ 0.468029] net_namespace: 840 bytes
[ 0.468029] Booting paravirtualized kernel on bare hardware
[ 0.468029] Time: 2:25:10 Date: 06/19/09
[ 0.468029] NET: Registered protocol family 16
[ 0.468029] EISA bus registered
[ 0.468029] ACPI: bus type pci registered
[ 0.468029] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 7
[ 0.468029] PCI: MCFG area at e0000000 reserved in E820
[ 0.468029] PCI: Using MMCONFIG for extended config space
[ 0.468029] PCI: Using configuration type 1 for base access
[ 0.468029] ACPI: EC: Look up EC in DSDT
[ 0.468944] ACPI: Interpreter enabled
[ 0.468988] ACPI: (supports S0 S3 S4 S5)
[ 0.469180] ACPI: Using IOAPIC for interrupt routing
[ 0.472053] ACPI: EC: non-query interrupt received, switching to interrupt mode
[ 0.552530] ACPI: EC: GPE = 0x1a, I/O: command/status = 0x66, data = 0x62
[ 0.552576] ACPI: EC: driver started in interrupt mode
[ 0.552654] ACPI: PCI Root Bridge [PCI0] (0000:00)
[ 0.552796] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[ 0.552842] pci 0000:00:04.0: PME# disabled
[ 0.552942] PCI: 0000:00:13.0 reg 10 32bit mmio: [c0000000, c0000fff]
[ 0.553033] PCI: 0000:00:13.1 reg 10 32bit mmio: [c0001000, c0001fff]
[ 0.553133] PCI: 0000:00:13.2 reg 10 32bit mmio: [c0002000, c0002fff]
[ 0.553192] pci 0000:00:13.2: supports D1
[ 0.553194] pci 0000:00:13.2: supports D2
[ 0.553196] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[ 0.553243] pci 0000:00:13.2: PME# disabled
[ 0.553326] PCI: 0000:00:14.0 reg 10 io port: [8400, 840f]
[ 0.553335] PCI: 0000:00:14.0 reg 14 32bit mmio: [c0003000, c00033ff]
[ 0.553377] HPET not enabled in BIOS. You might try hpet=force boot option
[ 0.553463] PCI: 0000:00:14.1 reg 10 io port: [8430, 8437]
[ 0.553471] PCI: 0000:00:14.1 reg 14 io port: [8424, 8427]
[ 0.553479] PCI: 0000:00:14.1 reg 18 io port: [8428, 842f]
[ 0.553487] PCI: 0000:00:14.1 reg 1c io port: [8420, 8423]
[ 0.553495] PCI: 0000:00:14.1 reg 20 io port: [8410, 841f]
[ 0.553661] PCI: 0000:00:14.5 reg 10 32bit mmio: [c0003400, c00034ff]
[ 0.553751] PCI: 0000:00:14.6 reg 10 32bit mmio: [c0003800, c00038ff]
[ 0.553883] PCI: 0000:01:05.0 reg 10 32bit mmio: [c8000000, cfffffff]
[ 0.553887] PCI: 0000:01:05.0 reg 14 io port: [9000, 90ff]
[ 0.553891] PCI: 0000:01:05.0 reg 18 32bit mmio: [c0100000, c010ffff]
[ 0.553900] PCI: 0000:01:05.0 reg 30 32bit mmio: [0, 1ffff]
[ 0.553906] pci 0000:01:05.0: supports D1
[ 0.553908] pci 0000:01:05.0: supports D2
[ 0.553922] PCI: bridge 0000:00:01.0 io port: [9000, 9fff]
[ 0.553924] PCI: bridge 0000:00:01.0 32bit mmio: [c0100000, c01fffff]
[ 0.553928] PCI: bridge 0000:00:01.0 64bit mmio pref: [c8000000, cfffffff]
[ 0.553984] PCI: bridge 0000:00:04.0 io port: [0, fff]
[ 0.553987] PCI: bridge 0000:00:04.0 32bit mmio: [0, fffff]
[ 0.554024] PCI: 0000:06:02.0 reg 10 32bit mmio: [c0204000, c0205fff]
[ 0.554128] PCI: 0000:06:04.0 reg 10 32bit mmio: [c0208000, c0208fff]
[ 0.554151] pci 0000:06:04.0: supports D1
[ 0.554153] pci 0000:06:04.0: supports D2
[ 0.554155] pci 0000:06:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[ 0.554203] pci 0000:06:04.0: PME# disabled
[ 0.554293] PCI: 0000:06:04.2 reg 10 32bit mmio: [c0209000, c02097ff]
[ 0.554303] PCI: 0000:06:04.2 reg 14 32bit mmio: [c0200000, c0203fff]
[ 0.554367] pci 0000:06:04.2: supports D1
[ 0.554368] pci 0000:06:04.2: supports D2
[ 0.554370] pci 0000:06:04.2: PME# supported from D0 D1 D2 D3hot
[ 0.554418] pci 0000:06:04.2: PME# disabled
[ 0.554504] PCI: 0000:06:04.3 reg 10 32bit mmio: [c0206000, c0207fff]
[ 0.554573] pci 0000:06:04.3: supports D1
[ 0.554574] pci 0000:06:04.3: supports D2
[ 0.554576] pci 0000:06:04.3: PME# supported from D0 D1 D2 D3hot
[ 0.554624] pci 0000:06:04.3: PME# disabled
[ 0.554711] PCI: 0000:06:04.4 reg 10 32bit mmio: [c020a000, c020a0ff]
[ 0.554720] PCI: 0000:06:04.4 reg 14 32bit mmio: [c0209c00, c0209cff]
[ 0.554730] PCI: 0000:06:04.4 reg 18 32bit mmio: [c0209800, c02098ff]
[ 0.554783] pci 0000:06:04.4: supports D1
[ 0.554785] pci 0000:06:04.4: supports D2
[ 0.554787] pci 0000:06:04.4: PME# supported from D0 D1 D2 D3hot
[ 0.554835] pci 0000:06:04.4: PME# disabled
[ 0.554929] PCI: 0000:06:06.0 reg 10 io port: [a000, a0ff]
[ 0.554938] PCI: 0000:06:06.0 reg 14 32bit mmio: [c020a400, c020a4ff]
[ 0.554999] pci 0000:06:06.0: supports D1
[ 0.555001] pci 0000:06:06.0: supports D2
[ 0.555002] pci 0000:06:06.0: PME# supported from D1 D2 D3hot D3cold
[ 0.555051] pci 0000:06:06.0: PME# disabled
[ 0.555142] pci 0000:00:14.4: transparent bridge
[ 0.555192] PCI: bridge 0000:00:14.4 io port: [a000, afff]
[ 0.555197] PCI: bridge 0000:00:14.4 32bit mmio: [c0200000, c02fffff]
[ 0.555237] bus 00 -> node 0
[ 0.555242] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[ 0.555394] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[ 0.555527] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[ 0.555674] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[ 0.557654] ACPI: PCI Interrupt Link [LNKA] (IRQs 10 11) *0, disabled.
[ 0.558014] ACPI: PCI Interrupt Link [LNKB] (IRQs 10 11) *0, disabled.
[ 0.558372] ACPI: PCI Interrupt Link [LNKC] (IRQs 10 11) *0, disabled.
[ 0.558730] ACPI: PCI Interrupt Link [LNKD] (IRQs 10 11) *0, disabled.
[ 0.559088] ACPI: PCI Interrupt Link [LNKE] (IRQs 10 11) *0, disabled.
[ 0.559446] ACPI: PCI Interrupt Link [LNKF] (IRQs 10 11) *0, disabled.
[ 0.559805] ACPI: PCI Interrupt Link [LNKG] (IRQs 10 11) *0, disabled.
[ 0.560136] ACPI: PCI Interrupt Link [LNKH] (IRQs 10 11) *0, disabled.
[ 0.560522] Linux Plug and Play Support v0.97 (c) Adam Belay
[ 0.560593] pnp: PnP ACPI init
[ 0.560640] ACPI: bus type pnp registered
[ 0.562649] pnp 00:08: io resource (0x72-0x73) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.562703] pnp 00:08: io resource (0xb0-0xb1) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.562755] pnp 00:08: io resource (0x92-0x92) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.562807] pnp 00:08: io resource (0x40b-0x40b) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.562859] pnp 00:08: io resource (0x4d0-0x4d1) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.562911] pnp 00:08: io resource (0x4d6-0x4d6) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.562963] pnp 00:08: io resource (0x870-0x87f) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.563015] pnp 00:08: io resource (0xc00-0xc01) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.563068] pnp 00:08: io resource (0xc14-0xc14) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.563120] pnp 00:08: io resource (0xc50-0xc52) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.563172] pnp 00:08: io resource (0xc6c-0xc6c) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.563680] pnp 00:08: io resource (0xc6f-0xc6f) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.563732] pnp 00:08: io resource (0xcd4-0xcd5) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.563784] pnp 00:08: io resource (0xcd6-0xcd7) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.563836] pnp 00:08: io resource (0xcd8-0xcdf) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.563888] pnp 00:08: io resource (0xf40-0xf47) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.563940] pnp 00:08: io resource (0x280-0x293) overlaps 0000:00:04.0 BAR 7 (0x0-0xfff), disabling
[ 0.564198] pnp 00:09: mem resource (0xe0000-0xfffff) overlaps 0000:00:04.0 BAR 8 (0x0-0xfffff), disabling
[ 0.564251] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:00:04.0 BAR 8 (0x0-0xfffff), disabling
[ 0.564310] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling
[ 0.588092] pnp: PnP ACPI: found 10 devices
[ 0.588136] ACPI: ACPI bus type pnp unregistered
[ 0.588181] PnPBIOS: Disabled by ACPI PNP
[ 0.588474] PCI: Using ACPI for IRQ routing
[ 0.588521] pci 0000:00:04.0: BAR 7: can't allocate resource
[ 0.588565] pci 0000:00:04.0: BAR 8: can't allocate resource
[ 0.588726] NET: Registered protocol family 8
[ 0.588726] NET: Registered protocol family 20
[ 0.588726] NetLabel: Initializing
[ 0.588726] NetLabel: domain hash size = 128
[ 0.588726] NetLabel: protocols = UNLABELED CIPSOv4
[ 0.588726] NetLabel: unlabeled traffic allowed by default
[ 0.588726] tracer: 772 pages allocated for 65536 entries of 48 bytes
[ 0.588726] actual entries 65620
[ 0.588839] AppArmor: AppArmor Filesystem Enabled
[ 0.588907] ACPI: RTC can wake from S4
[ 0.588954] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[ 0.588954] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[ 0.588954] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved
[ 0.588954] system 00:08: ioport range 0x1080-0x1080 has been reserved
[ 0.588954] system 00:08: ioport range 0x8000-0x805f has been reserved
[ 0.588954] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[ 0.624911] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[ 0.624957] pci 0000:00:01.0: IO window: 0x9000-0x9fff
[ 0.625003] pci 0000:00:01.0: MEM window: 0xc0100000-0xc01fffff
[ 0.625048] pci 0000:00:01.0: PREFETCH window: 0x000000c8000000-0x000000cfffffff
[ 0.625100] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02
[ 0.625144] pci 0000:00:04.0: IO window: disabled
[ 0.625189] pci 0000:00:04.0: MEM window: disabled
[ 0.625233] pci 0000:00:04.0: PREFETCH window: disabled
[ 0.625282] pci 0000:06:04.0: CardBus bridge, secondary bus 0000:07
[ 0.625326] pci 0000:06:04.0: IO window: 0x00a400-0x00a4ff
[ 0.625375] pci 0000:06:04.0: IO window: 0x00a800-0x00a8ff
[ 0.625423] pci 0000:06:04.0: PREFETCH window: 0x88000000-0x8bffffff
[ 0.625471] pci 0000:06:04.0: MEM window: 0x8c000000-0x8fffffff
[ 0.625520] pci 0000:00:14.4: PCI bridge, secondary bus 0000:06
[ 0.625566] pci 0000:00:14.4: IO window: 0xa000-0xafff
[ 0.625615] pci 0000:00:14.4: MEM window: 0xc0200000-0xc02fffff
[ 0.625662] pci 0000:00:14.4: PREFETCH window: 0x00000088000000-0x0000008bffffff
[ 0.625727] pci 0000:00:04.0: setting latency timer to 64
[ 0.625744] pci 0000:06:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 0.625794] bus: 00 index 0 io port: [0, ffff]
[ 0.625837] bus: 00 index 1 mmio: [0, ffffffff]
[ 0.625881] bus: 01 index 0 io port: [9000, 9fff]
[ 0.625925] bus: 01 index 1 mmio: [c0100000, c01fffff]
[ 0.625969] bus: 01 index 2 mmio: [c8000000, cfffffff]
[ 0.626013] bus: 01 index 3 mmio: [0, 0]
[ 0.626056] bus: 02 index 0 mmio: [0, fff]
[ 0.626099] bus: 02 index 1 mmio: [0, fffff]
[ 0.626142] bus: 02 index 2 mmio: [0, 0]
[ 0.626185] bus: 02 index 3 mmio: [0, 0]
[ 0.626229] bus: 06 index 0 io port: [a000, afff]
[ 0.626272] bus: 06 index 1 mmio: [c0200000, c02fffff]
[ 0.626316] bus: 06 index 2 mmio: [88000000, 8bffffff]
[ 0.626360] bus: 06 index 3 io port: [0, ffff]
[ 0.626404] bus: 06 index 4 mmio: [0, ffffffff]
[ 0.626447] bus: 07 index 0 io port: [a400, a4ff]
[ 0.626491] bus: 07 index 1 io port: [a800, a8ff]
[ 0.626535] bus: 07 index 2 mmio: [88000000, 8bffffff]
[ 0.626579] bus: 07 index 3 mmio: [8c000000, 8fffffff]
[ 0.626631] NET: Registered protocol family 2
[ 0.626775] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[ 0.627118] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[ 0.628194] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[ 0.628793] TCP: Hash tables configured (established 131072 bind 65536)
[ 0.628840] TCP reno registered
[ 0.628996] NET: Registered protocol family 1
[ 0.629155] checking if image is initramfs... it is
[ 1.128080] Switched to high resolution mode on CPU 0
[ 1.463448] Freeing initrd memory: 16468k freed
[ 1.464207] audit: initializing netlink socket (disabled)
[ 1.464266] type=2000 audit(1245378309.464:1): initialized
[ 1.469342] highmem bounce pool size: 64 pages
[ 1.469389] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[ 1.471290] VFS: Disk quotas dquot_6.5.1
[ 1.471407] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[ 1.471545] msgmni has been set to 1743
[ 1.471683] io scheduler noop registered
[ 1.471727] io scheduler anticipatory registered
[ 1.471771] io scheduler deadline registered
[ 1.471822] io scheduler cfq registered (default)
[ 1.471873] pci 0000:00:00.0: MSI quirk detected; MSI disabled
[ 1.471962] pci 0000:01:05.0: Boot video device
[ 1.472096] pcieport-driver 0000:00:04.0: found MSI capability
[ 1.472143] pci_express 0000:00:04.0:pcie00: allocate port service
[ 1.472185] pci_express 0000:00:04.0:pcie01: allocate port service
[ 1.492068] aer 0000:00:04.0:pcie01: AER service couldn't init device: no _OSC support
[ 1.492216] isapnp: Scanning for PnP cards...
[ 1.846377] isapnp: No Plug & Play device found
[ 1.875119] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[ 1.875671] serial 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 1.875723] serial 0000:00:14.6: PCI INT B disabled
[ 1.877514] brd: module loaded
[ 1.877616] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[ 1.877761] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[ 1.900879] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 1.900926] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 1.901212] mice: PS/2 mouse device common for all mice
[ 1.902139] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[ 1.902207] rtc0: alarms up to one month
[ 1.902344] EISA: Probing bus 0 at eisa.0
[ 1.902394] Cannot allocate resource for EISA slot 1
[ 1.902462] Cannot allocate resource for EISA slot 8
[ 1.902505] EISA: Detected 0 cards.
[ 1.902550] cpuidle: using governor ladder
[ 1.902593] cpuidle: using governor menu
[ 1.903036] TCP cubic registered
[ 1.903102] Using IPI No-Shortcut mode
[ 1.903287] registered taskstats version 1
[ 1.903438] Magic number: 13:11:410
[ 1.903669] pci 0000:00:18.2: hash matches
[ 1.903762] rtc_cmos 00:04: setting system clock to 2009-06-19 02:25:11 UTC (1245378311)
[ 1.903813] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[ 1.903857] EDD information not available.
[ 1.904364] Freeing unused kernel memory: 424k freed
[ 1.904456] Write protecting the kernel text: 2576k
[ 1.904529] Write protecting the kernel read-only data: 936k
[ 1.919314] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[ 1.991309] fuse init (API version 7.9)
[ 2.010030] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[ 2.010264] processor ACPI0007:00: registered as cooling_device0
[ 2.010311] ACPI: Processor [CPU0] (supports 8 throttling states)
[ 2.015497] Marking TSC unstable due to TSC halts in idle
[ 2.026459] thermal LNXTHERM:01: registered as thermal_zone0
[ 2.036453] ACPI: Thermal Zone [THRM] (0 C)
[ 2.484851] usbcore: registered new interface driver usbfs
[ 2.484927] usbcore: registered new interface driver hub
[ 2.485030] usbcore: registered new device driver usb
[ 2.490796] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[ 2.490826] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2.490886] ohci_hcd 0000:00:13.0: OHCI Host Controller
[ 2.490972] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1
[ 2.491045] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0000000
[ 2.548201] usb usb1: configuration #1 chosen from 1 choice
[ 2.548274] hub 1-0:1.0: USB hub found
[ 2.548329] hub 1-0:1.0: 4 ports detected
[ 2.548558] No dock devices found.
[ 2.594211] SCSI subsystem initialized
[ 2.652344] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2.652408] ohci_hcd 0000:00:13.1: OHCI Host Controller
[ 2.652477] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2
[ 2.652544] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0001000
[ 2.656444] libata version 3.00 loaded.
[ 2.681323] 8139too Fast Ethernet driver 0.9.28
[ 2.712233] usb usb2: configuration #1 chosen from 1 choice
[ 2.712308] hub 2-0:1.0: USB hub found
[ 2.712364] hub 2-0:1.0: 4 ports detected
[ 2.920652] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 2.920718] ehci_hcd 0000:00:13.2: EHCI Host Controller
[ 2.920781] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[ 2.921332] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0002000
[ 2.932041] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[ 2.932243] usb usb3: configuration #1 chosen from 1 choice
[ 2.932310] hub 3-0:1.0: USB hub found
[ 2.932362] hub 3-0:1.0: 8 ports detected
[ 3.140431] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 3.140537] pata_atiixp 0000:00:14.1: setting latency timer to 64
[ 3.140654] scsi0 : pata_atiixp
[ 3.140805] scsi1 : pata_atiixp
[ 3.142031] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14
[ 3.142078] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15
[ 3.252046] usb 3-4: new high speed USB device using ehci_hcd and address 2
[ 3.570637] usb 3-4: configuration #1 chosen from 1 choice
[ 3.600612] ata1.00: ATA-6: ST9100825A, 3.05, max UDMA/100
[ 3.600659] ata1.00: 195371568 sectors, multi 16: LBA 
[ 3.600715] ata1.01: ATA-6: ST9100825A, 3.05, max UDMA/100
[ 3.600761] ata1.01: 195371568 sectors, multi 16: LBA 
[ 3.616567] ata1.00: configured for UDMA/100
[ 3.632538] ata1.01: configured for UDMA/100
[ 3.796571] ata2.00: ATAPI: HL-DT-ST DVDRAM GSA-4084N, KQ09, max MWDMA2
[ 3.812543] ata2.00: configured for MWDMA2
[ 3.812686] scsi 0:0:0:0: Direct-Access ATA ST9100825A 3.05 PQ: 0 ANSI: 5
[ 3.813185] scsi 0:0:1:0: Direct-Access ATA ST9100825A 3.05 PQ: 0 ANSI: 5
[ 3.818019] scsi 1:0:0:0: CD-ROM HL-DT-ST DVDRAM GSA-4084N KQ09 PQ: 0 ANSI: 5
[ 3.818949] b43-pci-bridge 0000:06:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[ 3.876100] ssb: Sonics Silicon Backplane found on PCI device 0000:06:02.0
[ 3.876259] ohci1394 0000:06:04.2: PCI INT C -> GSI 23 (level, low) -> IRQ 23
[ 3.926057] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23] MMIO=[c0209000-c02097ff] Max Packet=[2048] IR/IT contexts=[4/8]
[ 3.926737] 8139too 0000:06:06.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 3.927955] eth0: RealTek RTL8139 at 0xa000, 00:16:d4:3b:1e:ad, IRQ 22
[ 3.928021] eth0: Identified 8139 chip type 'RTL-8100B/8139D'
[ 3.939375] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[ 3.953196] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[ 3.953275] scsi 0:0:1:0: Attached scsi generic sg1 type 0
[ 3.953348] scsi 1:0:0:0: Attached scsi generic sg2 type 5
[ 3.972818] Driver 'sd' needs updating - please use bus_type methods
[ 3.972986] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[ 3.973052] sd 0:0:0:0: [sda] Write Protect is off
[ 3.973097] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3.973132] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3.973252] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[ 3.973314] sd 0:0:0:0: [sda] Write Protect is off
[ 3.973359] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3.973392] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 3.973445] sda:<4>Driver 'sr' needs updating - please use bus_type methods
[ 4.215165] sda1 sda2 sda3
[ 4.215881] sd 0:0:0:0: [sda] Attached SCSI disk
[ 4.216511] sd 0:0:1:0: [sdb] 195371568 512-byte hardware sectors (100030 MB)
[ 4.216580] sd 0:0:1:0: [sdb] Write Protect is off
[ 4.216624] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 4.216668] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.216787] sd 0:0:1:0: [sdb] 195371568 512-byte hardware sectors (100030 MB)
[ 4.216853] sd 0:0:1:0: [sdb] Write Protect is off
[ 4.216898] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 4.216940] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 4.216993] sdb: sdb1 sdb2 < sdb5 sdb6 >
[ 4.278376] sd 0:0:1:0: [sdb] Attached SCSI disk
[ 4.283319] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[ 4.283377] Uniform CD-ROM driver Revision: 3.20
[ 4.283508] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 5.196728] ieee1394: Host added: ID:BUS[0-00:1023] GUID[683f0200f419407a]
[ 5.601860] kjournald starting. Commit interval 5 seconds
[ 5.601919] EXT3-fs: mounted filesystem with ordered data mode.
[ 6.364678] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 6.405358] ISO 9660 Extensions: RRIP_1991A
[ 6.675666] loop: module loaded
[ 6.866159] squashfs: version 3.3 (2007/10/31) Phillip Lougher
[ 7.063842] aufs 20080922
[ 50.123016] udevd version 124 started
[ 51.641978] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[ 52.034875] input: PC Speaker as /devices/platform/pcspkr/input/input2
[ 52.107618] Linux agpgart interface v0.103
[ 52.109806] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[ 52.150521] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0
[ 52.211643] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[ 52.236214] ACPI: Power Button (FF) [PWRF]
[ 52.236361] input: Sleep Button (FF) as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input4
[ 52.260195] ACPI: Sleep Button (FF) [SLPF]
[ 52.260327] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input5
[ 52.276205] ACPI: Lid Switch [LID]
[ 52.276336] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[ 52.304238] ACPI: Power Button (CM) [PWRB]
[ 52.385226] ACPI: WMI: Mapper loaded
[ 52.645975] ACPI: AC Adapter [ACAD] (on-line)
[ 52.685531] Yenta: CardBus bridge found at 0000:06:04.0 [103c:309b]
[ 52.685604] Yenta: Enabling burst memory read transactions
[ 52.685653] Yenta: Using INTVAL to route CSC interrupts to PCI
[ 52.685697] Yenta: Routing CardBus interrupts to ISA
[ 52.685746] Yenta TI: socket 0000:06:04.0, mfunc 0x00a61b22, devctl 0x64
[ 52.694971] sdhci: Secure Digital Host Controller Interface driver
[ 52.695022] sdhci: Copyright(c) Pierre Ossman
[ 52.916794] Yenta: ISA IRQ mask 0x0cf8, PCI irq 20
[ 52.916846] Socket status: 30000006
[ 52.916892] pcmcia: parent PCI bridge I/O window: 0xa000 - 0xafff
[ 52.916937] cs: IO port probe 0xa000-0xafff: clean.
[ 52.917167] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff
[ 52.917213] pcmcia: parent PCI bridge Memory window: 0x88000000 - 0x8bffffff
[ 52.949424] sdhci-pci 0000:06:04.4: SDHCI controller found [104c:8034] (rev 0)
[ 52.949496] sdhci-pci 0000:06:04.4: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 52.949614] mmc0: SDHCI controller on PCI [0000:06:04.4] using PIO
[ 52.951689] mmc1: SDHCI controller on PCI [0000:06:04.4] using PIO
[ 52.951763] mmc2: SDHCI controller on PCI [0000:06:04.4] using PIO
[ 52.951829] tifm_7xx1 0000:06:04.3: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[ 53.155758] ACPI: Battery Slot [BAT1] (battery present)
[ 53.371802] acpi device:12: registered as cooling_device1
[ 53.372119] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0f/device:10/input/input7
[ 53.400187] ACPI: Video Device [VGA] (multi-head: yes rom: no post: no)
[ 53.539974] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[ 53.567958] ATI IXP AC97 controller 0000:00:14.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 53.583478] ATI IXP MC97 controller 0000:00:14.6: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 53.611461] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8
[ 53.692086] MC'97 0 converters and GPIO not ready (0x1)
[ 54.161398] b43-phy0: Broadcom 4318 WLAN found
[ 54.230228] phy0: Selected rate control algorithm 'pid'
[ 54.534900] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[ 54.593578] phy1: Selected rate control algorithm 'pid'
[ 54.593921] Registered led device: rt73usb-phy1:radio
[ 54.594001] Registered led device: rt73usb-phy1:assoc
[ 54.594077] Registered led device: rt73usb-phy1:quality
[ 54.597543] usbcore: registered new interface driver rt73usb
[ 55.647111] cs: IO port probe 0x100-0x3af: clean.
[ 55.649630] cs: IO port probe 0x3e0-0x4ff: excluding 0x408-0x40f 0x4d0-0x4d7
[ 55.653027] cs: IO port probe 0x820-0x8ff: excluding 0x878-0x87f
[ 55.654519] cs: IO port probe 0xc00-0xcf7: excluding 0xc00-0xc07 0xc10-0xc17 0xc50-0xc57 0xc68-0xc6f 0xcd0-0xcdf
[ 55.672480] cs: IO port probe 0xa00-0xaff: clean.
[ 56.988932] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 58.830703] powernow-k8: Found 1 AMD Turion(tm) 64 Mobile Technology ML-44 processors (1 cpu cores) (version 2.20.00)
[ 58.830746] powernow-k8: 0 : fid 0x10 (2400 MHz), vid 0x4
[ 58.830749] powernow-k8: 1 : fid 0xe (2200 MHz), vid 0x6
[ 58.830751] powernow-k8: 2 : fid 0xc (2000 MHz), vid 0x8
[ 58.830753] powernow-k8: 3 : fid 0xa (1800 MHz), vid 0xa
[ 58.830754] powernow-k8: 4 : fid 0x8 (1600 MHz), vid 0xc
[ 58.830756] powernow-k8: 5 : fid 0x0 (800 MHz), vid 0x16
[ 58.830795] powernow-k8: ph2 null fid transition 0x10
[ 59.552855] apm: BIOS not found.
[ 60.624048] Clocksource tsc unstable (delta = -120617742 ns)
[ 61.788060] usb 3-5: new high speed USB device using ehci_hcd and address 3
[ 61.933637] usb 3-5: configuration #1 chosen from 1 choice
[ 62.162272] usbcore: registered new interface driver libusual
[ 62.204164] Initializing USB Mass Storage driver...
[ 62.206949] scsi2 : SCSI emulation for USB Mass Storage devices
[ 62.213909] usbcore: registered new interface driver usb-storage
[ 62.216097] USB Mass Storage support registered.
[ 62.218635] usb-storage: device found at 3
[ 62.218648] usb-storage: waiting for device to settle before scanning
[ 67.216399] usb-storage: device scan complete
[ 67.218121] scsi 2:0:0:0: Direct-Access Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
[ 68.214369] sd 2:0:0:0: [sdc] 15646720 512-byte hardware sectors (8011 MB)
[ 68.217864] sd 2:0:0:0: [sdc] Write Protect is off
[ 68.217877] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 68.217884] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 68.229371] sd 2:0:0:0: [sdc] 15646720 512-byte hardware sectors (8011 MB)
[ 68.232743] sd 2:0:0:0: [sdc] Write Protect is off
[ 68.232756] sd 2:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 68.232762] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[ 68.239841] sdc: sdc1
[ 68.242268] sd 2:0:0:0: [sdc] Attached SCSI removable disk
[ 68.244521] sd 2:0:0:0: Attached scsi generic sg3 type 0
[ 74.960080] pci 0000:01:05.0: power state changed by ACPI to D0
[ 74.960108] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 75.557548] [drm] Initialized drm 1.1.0 20060810
[ 75.582701] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[ 76.217267] [drm] Setting GART location based on new memory map
[ 76.221139] [drm] Loading R300 Microcode
[ 76.221189] [drm] Num pipes: 1
[ 76.221199] [drm] writeback test succeeded in 1 usecs
[ 109.139506] NET: Registered protocol family 10
[ 109.143015] lo: Disabled Privacy Extensions
 
**lshw -C network**
*-network:0 
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 2
bus info: pci@0000:06:02.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:1 DISABLED
description: Ethernet interface
product: RTL-8139/8139C/8139C+
vendor: Realtek Semiconductor Co., Ltd.
physical id: 6
bus info: pci@0000:06:06.0
logical name: eth0
version: 10
serial: 00:16:d4:3b:1e:ad
size: 10MB/s
capacity: 100MB/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=128 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
*-network:0 DISABLED
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:14:a5:bd:ca:a9
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Wireless interface
physical id: 3
logical name: wlan1
serial: 00:18:f8:35:87:a1
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
root@deft:~# iwlist scan
lo Interface doesn't support scanning.
eth0 Interface doesn't support scanning.
wmaster0 Interface doesn't support scanning.
wlan0 Interface doesn't support scanning : Network is down
wmaster1 Interface doesn't support scanning.
wlan1 Interface doesn't support scanning : Network is down
 
**lsb_release -d**
Description: Ubuntu 8.10
 
**uname -mr**
2.6.27-7-generic i686
 
**uname -mrpio**
2.6.27-7-generic i686 unknown unknown GNU/Linux
 
**/etc/init.d/networking restart**
* Reconfiguring network interfaces... [ OK ] 
 
 
If more info is required just ask!! 
 
**Thanks for anyone's help!!!**

---

### Post by kerry_s on 2009-06-20
it looks like the wireless is ready to go.
have you tried:

```
[B]sudo iwconfig wlan0 essid your-network
sudo ifconfig wlan0 up
sudo dhclient wlan0[/B]

```

for the wired:

```
[B]sudo ifconfig eth0 up
sudo dhclient eth0[/B]
```

post your /etc/network/interfaces

funny on there site it says, not for newbies. :)

---

### Post by Webtiger on 2009-06-20
Kerry;
Great instructions!
I have the LAN (eth0) working was able to go out and grab ndiswrapper and the correct Broadcom driver so the onboard WAN is now lit up.
 
Here's the INTERFACES code:
 
# The primary network interface
auto lo
iface lo inet loopback
# The primary wireless network interface
iface wlan0 inet dhcp

 
I'm running a WAP54G Access Point which is a repeater for a WRT54G2 router in another part of the building and the the wireless is running WPA2 - Personal w/AES encryption.
 
A couple of questions regarding WAN activation via my setup.
 
I've managed to set the ESSID and Mode  but does the 'key' for the Access Point or the router have to be entered in hex?
 
Is there any way I can make these Wi-Fi parameters "stick" so I don't have to keep re-entering them after boot time?
 
I still do not have any Network Manager applet if I boot into the GUI. If I do "nm-applet" at the prompt I get back:
(nm-applet:8307): WARNING **: <WARN> applet_dbus_manager_start_service():  Could not acquire the NetworkManagerUserSettings service as it is already taken. Return: 3
 
(nm-applet:8307): GLib-GObject-CRITICAL **: g_object_unerf: assetion 'G_IS_OBJECT (object)' failed
 
I know the DEFT web site says not for Noobies but I have no choice here. I need this for University digital froensics classes. 
It's not like I woke up this past Wednesday and decided to learn Linux the hard way....

---

