---
title: "Realtek RTL8187 Problem on Ubuntu 8.04"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by SliTCX on 2008-12-17
To start off, my issue is that I can view the networks, but when I connect to it, my router suddenly restarts, so I don't know what is happening. Plus, I have no internet on the laptop, I'm using my desktop's internet.

I did everything that was told to do in this thread.[http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681")

```
Model: Gateway MT6459
More information can be found here: [http://support.gateway.com/s/Mobile/2007/Oasis/1014586R/1014586Rnv.shtml]("http://support.gateway.com/s/Mobile/2007/Oasis/1014586R/1014586Rnv.shtml")
```

```
***lspci***
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10) 
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) 
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) 
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) 
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83) 
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) 
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01) 
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80) 
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) 
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration 
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control 
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP] 
02:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
02:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
02:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 
```

```
***lsusb***
Bus 002 Device 001: ID 0000:0000   
Bus 003 Device 003: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive 
Bus 003 Device 002: ID 0bda:8187 Realtek Semiconductor Corp.  
Bus 003 Device 001: ID 0000:0000   
Bus 001 Device 001: ID 0000:0000   

```

```
***ifconfig***
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:732 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:732 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:48952 (47.8 KB)  TX bytes:48952 (47.8 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:f0:ee:d0   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-F0-EE-D0-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

```

```
***iwconfig***
lo        no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11g  ESSID:""   
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:D0:9E:CF:16:61    
          Tx-Power=27 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B    
          Encryption key:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

```

```
***iwconfig wlan0***
wlan0     IEEE 802.11g  ESSID:""   
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:D0:9E:CF:16:61    
          Tx-Power=27 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B    
          Encryption key:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
```

```
***lsmod***
Module                  Size  Used by 
nls_iso8859_1           6656  1  
nls_cp437               8320  1  
vfat                   16256  1  
fat                    60592  1 vfat 
sg                     41880  0  
sd_mod                 33280  2  
usb_storage            82496  1  
libusual               23520  1 usb_storage 
af_packet              27272  0  
ipv6                  311848  10  
rfcomm                 47392  2  
l2cap                  28800  13 rfcomm 
bluetooth              67748  4 rfcomm,l2cap 
ppdev                  11400  0  
powernow_k8            16608  1  
cpufreq_conservative    10632  0  
cpufreq_stats           8416  0  
cpufreq_userspace       6180  0  
cpufreq_powersave       3200  0  
cpufreq_ondemand       11152  1  
freq_table              6464  3 powernow_k8,cpufreq_stats,cpufreq_ondemand 
container               6656  0  
dock                   12960  0  
sbs                    17808  0  
sbshc                   8960  1 sbs 
iptable_filter          4608  0  
ip_tables              24104  1 iptable_filter 
x_tables               23560  1 ip_tables 
sbp2                   27272  0  
parport_pc             41128  0  
lp                     14916  0  
parport                44300  3 ppdev,parport_pc,lp 
joydev                 15488  0  
pcmcia                 45976  0  
arc4                    3456  2  
ecb                     5248  2  
blkcipher               9476  1 ecb 
snd_hda_intel         440408  3  
snd_pcm_oss            47648  0  
snd_mixer_oss          20224  1 snd_pcm_oss 
snd_pcm                92168  2 snd_hda_intel,snd_pcm_oss 
snd_page_alloc         13200  2 snd_hda_intel,snd_pcm 
snd_hwdep              12552  1 snd_hda_intel 
rtl8187                37248  0  
snd_seq_dummy           5764  0  
mac80211              192532  1 rtl8187 
snd_seq_oss            38912  0  
cfg80211               17680  1 mac80211 
snd_seq_midi           10688  0  
snd_rawmidi            29856  1 snd_seq_midi 
eeprom_93cx6            3840  1 rtl8187 
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi 
video                  23444  0  
output                  5632  1 video 
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
snd_timer              27912  2 snd_pcm,snd_seq 
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
snd                    70856  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
serio_raw               9092  0  
battery                16776  0  
ac                      8328  0  
tifm_7xx1               9984  0  
yenta_socket           30092  1  
rsrc_nonstatic         14080  1 yenta_socket 
pcmcia_core            46116  3 pcmcia,yenta_socket,rsrc_nonstatic 
button                 10912  0  
i2c_piix4              11148  0  
psmouse                46236  0  
tifm_core              13064  1 tifm_7xx1 
shpchp                 38172  0  
pci_hotplug            34608  1 shpchp 
k8temp                  7680  0  
i2c_core               28544  1 i2c_piix4 
soundcore              10400  1 snd 
evdev                  14976  7  
pcspkr                  4992  0  
ext3                  149264  1  
jbd                    57000  1 ext3 
mbcache                11392  1 ext3 
ide_cd                 35488  0  
cdrom                  41512  1 ide_cd 
ide_disk               19072  3  
pata_atiixp            10496  0  
pata_acpi               9856  0  
ata_generic             9988  0  
libata                176432  3 pata_atiixp,pata_acpi,ata_generic 
scsi_mod              178488  5 sg,sd_mod,usb_storage,sbp2,libata 
ohci1394               36532  0  
atiixp                  6672  0 [permanent] 
ide_core              136600  3 ide_cd,ide_disk,atiixp 
ieee1394              106968  2 sbp2,ohci1394 
ehci_hcd               41996  0  
ohci_hcd               27524  0  
usbcore               169904  6 usb_storage,libusual,rtl8187,ehci_hcd,ohci_hcd 
thermal                19744  0  
processor              41448  2 powernow_k8,thermal 
fan                     6792  0  
fbcon                  46336  0  
tileblit                4096  1 fbcon 
font                   10112  1 fbcon 
bitblit                 7424  1 fbcon 
softcursor              3712  1 bitblit 
fuse                   56112  3  
```

```
***dmesg***
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23 
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 21 low level) 
[    0.000000] Setting APIC routing to flat 
[    0.000000] Using ACPI (MADT) for SMP configuration information 
[    0.000000] swsusp: Registered nosave memory region: 000000000009d000 - 000000000009e000 
[    0.000000] swsusp: Registered nosave memory region: 000000000009e000 - 00000000000a0000 
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000d0000 
[    0.000000] swsusp: Registered nosave memory region: 00000000000d0000 - 0000000000100000 
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000) 
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs 
[    0.000000] PERCPU: Allocating 34656 bytes of per cpu data 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 483102 
[    0.000000] Policy zone: DMA32 
[    0.000000] Kernel command line: root=UUID=d78a70e9-7f03-4ff3-9bcb-0117992bda84 ro quiet splash 
[    0.000000] Initializing CPU#0 
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes) 
[    0.000000] TSC calibrated against PM_TIMER 
[   14.608052] Marking TSC unstable due to TSCs unsynchronized 
[   14.608054] time.c: Detected 1795.494 MHz processor. 
[   14.608924] Console: colour VGA+ 80x25 
[   14.608928] console [tty0] enabled 
[   14.608945] Checking aperture... 
[   14.608948] CPU 0: aperture @ b3da000000 size 32 MB 
[   14.608950] Aperture too small (32 MB) 
[   14.620724] No AGP bridge found 
[   14.638290] Memory: 1924004k/1964544k available (2489k kernel code, 40144k reserved, 1318k data, 320k init) 
[   14.638328] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1 
[   14.717984] Calibrating delay using timer specific routine.. 3594.89 BogoMIPS (lpj=7189796) 
[   14.718021] Security Framework initialized 
[   14.718027] SELinux:  Disabled at boot. 
[   14.718042] AppArmor: AppArmor initialized 
[   14.718046] Failure registering capabilities with primary security module. 
[   14.718226] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes) 
[   14.719460] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes) 
[   14.720038] Mount-cache hash table entries: 256 
[   14.720174] Initializing cgroup subsys ns 
[   14.720178] Initializing cgroup subsys cpuacct 
[   14.720192] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line) 
[   14.720194] CPU: L2 Cache: 512K (64 bytes/line) 
[   14.720197] CPU 0/0 -> Node 0 
[   14.720199] CPU: Physical Processor ID: 0 
[   14.720200] CPU: Processor Core ID: 0 
[   14.720226] SMP alternatives: switching to UP code 
[   14.720885] Early unpacking initramfs... done 
[   15.085489] ACPI: Core revision 20070126 
[   15.085557] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found. 
[   15.596449] Using local APIC timer interrupts. 
[   15.652118] APIC timer calibration result 12468715 
[   15.652120] Detected 12.468 MHz APIC timer. 
[   15.652225] SMP alternatives: switching to SMP code 
[   15.652751] Booting processor 1/2 APIC 0x1 
[   15.662999] Initializing CPU#1 
[   15.740260] Calibrating delay using timer specific routine.. 3590.99 BogoMIPS (lpj=7181987) 
[   15.740267] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line) 
[   15.740269] CPU: L2 Cache: 512K (64 bytes/line) 
[   15.740271] CPU 1/1 -> Node 0 
[   15.740273] CPU: Physical Processor ID: 0 
[   15.740274] CPU: Processor Core ID: 1 
[   15.740365] AMD Turion(tm) 64 X2 Mobile Technology TL-56 stepping 02 
[   15.740380] AMD C1E detected late. Force timer broadcast. 
[   15.740235] Brought up 2 CPUs 
[   15.740320] CPU0 attaching sched-domain: 
[   15.740323]  domain 0: span 03 
[   15.740325]   groups: 01 02 
[   15.740328]   domain 1: span 03 
[   15.740329]    groups: 03 
[   15.740331] CPU1 attaching sched-domain: 
[   15.740333]  domain 0: span 03 
[   15.740334]   groups: 02 01 
[   15.740337]   domain 1: span 03 
[   15.740338]    groups: 03 
[   15.740587] net_namespace: 120 bytes 
[   15.741026] Time: 16:26:40  Date: 12/17/08 
[   15.741063] NET: Registered protocol family 16 
[   15.741264] ACPI: bus type pci registered 
[   15.741341] PCI: Using configuration type 1 
[   15.742408] ACPI: EC: Look up EC in DSDT 
[   15.744775] ACPI: Interpreter enabled 
[   15.744778] ACPI: (supports S0 S3 S4 S5) 
[   15.744793] ACPI: Using IOAPIC for interrupt routing 
[   15.749321] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62 
[   15.749324] ACPI: EC: driver started in poll mode 
[   15.749368] ACPI: PCI Root Bridge [PCI0] (0000:00) 
[   15.750512] PCI: Transparent bridge - 0000:00:14.4 
[   15.750591] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[   15.750779] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT] 
[   15.750886] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT] 
[   15.753396] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11) *0, disabled. 
[   15.753541] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11) *0, disabled. 
[   15.753683] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11) *0, disabled. 
[   15.753823] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11) *0, disabled. 
[   15.753964] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11) *0, disabled. 
[   15.754107] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11) *0, disabled. 
[   15.754248] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11) *0, disabled. 
[   15.754388] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11) *0, disabled. 
[   15.754529] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7 10 11) *0, disabled. 
[   15.754650] Linux Plug and Play Support v0.97 (c) Adam Belay 
[   15.754682] pnp: PnP ACPI init 
[   15.754690] ACPI: bus type pnp registered 
[   15.757039] pnp: PnP ACPI: found 10 devices 
[   15.757041] ACPI: ACPI bus type pnp unregistered 
[   15.757291] PCI: Using ACPI for IRQ routing 
[   15.757294] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report 
[   15.757588] ACPI: EC: non-query interrupt received, switching to interrupt mode 
[   15.768281] NET: Registered protocol family 8 
[   15.768283] NET: Registered protocol family 20 
[   15.768409] AppArmor: AppArmor Filesystem Enabled 
[   15.780246] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved 
[   15.780250] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved 
[   15.780254] system 00:01: iomem range 0xfee00000-0xfee00fff could not be reserved 
[   15.780265] system 00:08: ioport range 0x1080-0x1080 has been reserved 
[   15.780269] system 00:08: ioport range 0x220-0x22f has been reserved 
[   15.780272] system 00:08: ioport range 0x40b-0x40b has been reserved 
[   15.780275] system 00:08: ioport range 0x4d0-0x4d1 has been reserved 
[   15.780278] system 00:08: ioport range 0x4d6-0x4d6 has been reserved 
[   15.780282] system 00:08: ioport range 0x530-0x537 has been reserved 
[   15.780285] system 00:08: ioport range 0xc00-0xc01 has been reserved 
[   15.780288] system 00:08: ioport range 0xc14-0xc14 has been reserved 
[   15.780291] system 00:08: ioport range 0xc50-0xc52 has been reserved 
[   15.780294] system 00:08: ioport range 0xc6c-0xc6c has been reserved 
[   15.780298] system 00:08: ioport range 0xc6f-0xc6f has been reserved 
[   15.780301] system 00:08: ioport range 0xcd4-0xcd5 has been reserved 
[   15.780304] system 00:08: ioport range 0xcd6-0xcd7 has been reserved 
[   15.780307] system 00:08: ioport range 0xcd8-0xcdf has been reserved 
[   15.780311] system 00:08: ioport range 0x8000-0x805f has been reserved 
[   15.780314] system 00:08: ioport range 0xf40-0xf47 has been reserved 
[   15.780317] system 00:08: ioport range 0x87f-0x87f has been reserved 
[   15.780324] system 00:09: iomem range 0xe0000-0xfffff could not be reserved 
[   15.780328] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved 
[   15.780332] system 00:09: iomem range 0x0-0xfff could not be reserved 
[   15.780733] PCI: Bridge: 0000:00:01.0 
[   15.780736]   IO window: 9000-9fff 
[   15.780739]   MEM window: c0100000-c01fffff 
[   15.780742]   PREFETCH window: c8000000-cfffffff 
[   15.780753] PCI: Bus 3, cardbus bridge: 0000:02:09.0 
[   15.780756]   IO window: 00001400-000014ff 
[   15.780761]   IO window: 00001800-000018ff 
[   15.780766]   PREFETCH window: 88000000-8bffffff 
[   15.780772]   MEM window: 8c000000-8fffffff 
[   15.780778] PCI: Bridge: 0000:00:14.4 
[   15.780779]   IO window: disabled. 
[   15.780785]   MEM window: c0200000-c02fffff 
[   15.780789]   PREFETCH window: disabled. 
[   15.780829] ACPI: PCI Interrupt 0000:02:09.0[A] -> GSI 20 (level, low) -> IRQ 20 
[   15.780884] NET: Registered protocol family 2 
[   15.784209] Time: acpi_pm clocksource has been installed. 
[   15.784213] Clockevents: could not switch to one-shot mode: lapic is not functional. 
[   15.784217] Could not switch to high resolution mode on CPU 0 
[   15.788379] Clockevents: could not switch to one-shot mode: lapic is not functional. 
[   15.788383] Could not switch to high resolution mode on CPU 1 
[   15.816322] IP route cache hash table entries: 65536 (order: 7, 524288 bytes) 
[   15.817172] TCP established hash table entries: 262144 (order: 10, 4194304 bytes) 
[   15.819452] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes) 
[   15.820036] TCP: Hash tables configured (established 262144 bind 65536) 
[   15.820040] TCP reno registered 
[   15.828353] checking if image is initramfs... it is 
[   16.284133] Clockevents: could not switch to one-shot mode: lapic is not functional. 
[   16.284136] Could not switch to high resolution mode on CPU 1 
[   16.283961] Clockevents: could not switch to one-shot mode: lapic is not functional. 
[   16.283968] Could not switch to high resolution mode on CPU 0 
[   16.555214] Freeing initrd memory: 8203k freed 
[   16.561261] audit: initializing netlink socket (disabled) 
[   16.561273] audit(1229531200.444:1): initialized 
[   16.563518] VFS: Disk quotas dquot_6.5.1 
[   16.563600] Dquot-cache hash table entries: 512 (order 0, 4096 bytes) 
[   16.563739] io scheduler noop registered 
[   16.563742] io scheduler anticipatory registered 
[   16.563744] io scheduler deadline registered 
[   16.563871] io scheduler cfq registered (default) 
[   16.563877] PCI: MSI quirk detected. MSI deactivated. 
[   16.564674] Boot video device is 0000:01:05.0 
[   16.594781] Real Time Clock Driver v1.12ac 
[   16.594881] Linux agpgart interface v0.102 
[   16.594884] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[   16.596046] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[   16.596115] input: Macintosh mouse button emulation as /devices/virtual/input/input0 
[   16.596213] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12 
[   16.597981] serio: i8042 KBD port at 0x60,0x64 irq 1 
[   16.597985] serio: i8042 AUX port at 0x60,0x64 irq 12 
[   16.608033] mice: PS/2 mouse device common for all mice 
[   16.608075] cpuidle: using governor ladder 
[   16.608077] cpuidle: using governor menu 
[   16.608237] NET: Registered protocol family 1 
[   16.608342] registered taskstats version 1 
[   16.608454]   Magic number: 4:386:439 
[   16.608592] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0) 
[   16.608595] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[   16.608597] EDD information not available. 
[   16.608605] Freeing unused kernel memory: 320k freed 
[   16.643858] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1 
[   17.833280] fuse init (API version 7.9) 
[   17.855356] ACPI: Processor [CPU0] (supports 8 throttling states) 
[   17.857083] ACPI: Thermal Zone [THRM] (41 C) 
[   18.143378] usbcore: registered new interface driver usbfs 
[   18.143409] usbcore: registered new interface driver hub 
[   18.144244] usbcore: registered new device driver usb 
[   18.146028] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver 
[   18.146094] ACPI: PCI Interrupt 0000:00:13.0[A] -> GSI 19 (level, low) -> IRQ 19 
[   18.146304] ohci_hcd 0000:00:13.0: OHCI Host Controller 
[   18.146549] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 1 
[   18.146574] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0004000 
[   18.199176] usb usb1: configuration #1 chosen from 1 choice 
[   18.199203] hub 1-0:1.0: USB hub found 
[   18.199214] hub 1-0:1.0: 4 ports detected 
[   18.272017] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[   18.272024] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[   18.303108] ACPI: PCI Interrupt 0000:00:13.1[A] -> GSI 19 (level, low) -> IRQ 19 
[   18.303278] ohci_hcd 0000:00:13.1: OHCI Host Controller 
[   18.303348] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 2 
[   18.303368] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0005000 
[   18.359089] usb usb2: configuration #1 chosen from 1 choice 
[   18.359116] hub 2-0:1.0: USB hub found 
[   18.359127] hub 2-0:1.0: 4 ports detected 
[   18.463214] ATIIXP: IDE controller (0x1002:0x4376 rev 0x80) at  PCI slot 0000:00:14.1 
[   18.463237] ACPI: PCI Interrupt 0000:00:14.1[A] -> GSI 16 (level, low) -> IRQ 16 
[   18.463248] ATIIXP: not 100% native mode: will probe irqs later 
[   18.463257]     ide0: BM-DMA at 0x8410-0x8417, BIOS settings: hda:DMA, hdb:DMA 
[   18.463276] ATIIXP: simplex device: DMA disabled 
[   18.463278] ide1: ATIIXP Bus-Master DMA disabled (BIOS) 
[   18.463282] Probing IDE interface ide0... 
[   18.768212] usb 2-3: new full speed USB device using ohci_hcd and address 2 
[   18.986918] usb 2-3: configuration #1 chosen from 1 choice 
[   19.262928] hdb: Optiarc DVD RW AD-7530A, ATAPI CD/DVD-ROM drive 
[   19.598759] hda: ST9160821A, ATA DISK drive 
[   19.598775] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4 
[   19.598960] hda: UDMA/100 mode selected 
[   19.599216] hdb: host max PIO4 wanted PIO255(auto-tune) selected PIO4 
[   19.599485] hdb: UDMA/33 mode selected 
[   19.601691] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14 
[   19.604714] Probing IDE interface ide1... 
[   20.207488] ACPI: PCI Interrupt 0000:00:13.2[A] -> GSI 19 (level, low) -> IRQ 19 
[   20.207676] ehci_hcd 0000:00:13.2: EHCI Host Controller 
[   20.207742] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3 
[   20.207800] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0006000 
[   20.210062] usb 2-3: USB disconnect, address 2 
[   20.213707] SCSI subsystem initialized 
[   20.218043] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[   20.218162] usb usb3: configuration #1 chosen from 1 choice 
[   20.218185] hub 3-0:1.0: USB hub found 
[   20.218192] hub 3-0:1.0: 8 ports detected 
[   20.221079] libata version 3.00 loaded. 
[   20.322763] ACPI: PCI Interrupt 0000:02:09.1[B] -> GSI 21 (level, low) -> IRQ 21 
[   20.372949] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[c0205000-c02057ff]  Max Packet=[2048]  IR/IT contexts=[4/8] 
[   20.397330] hda: max request size: 512KiB 
[   20.397842] hda: 312581808 sectors (160041 MB) w/8192KiB Cache, CHS=19457/255/63 
[   20.398567] hda: cache flushes supported 
[   20.398616]  hda: hda1 hda2 < hda5 > 
[   20.446029] hdb: ATAPI 24X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache 
[   20.446037] Uniform CD-ROM driver Revision: 3.20 
[   20.609840] usb 3-6: new high speed USB device using ehci_hcd and address 2 
[   20.748641] usb 3-6: configuration #1 chosen from 1 choice 
[   20.780850] Attempting manual resume 
[   20.780854] swsusp: Resume From Partition 3:5 
[   20.780856] PM: Checking swsusp image. 
[   20.781035] PM: Resume from disk failed. 
[   20.817380] kjournald starting.  Commit interval 5 seconds 
[   20.817398] EXT3-fs: mounted filesystem with ordered data mode. 
[   21.653655] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b80367045603] 
[   28.566251] input: PC Speaker as /devices/platform/pcspkr/input/input2 
[   29.145735] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   29.181739] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   29.297957] piix4_smbus 0000:00:14.0: Found 0000:00:14.0 device 
[   29.344878] input: Power Button (FF) as /devices/virtual/input/input3 
[   29.397767] ACPI: Power Button (FF) [PWRF] 
[   29.397866] input: Lid Switch as /devices/virtual/input/input4 
[   29.430161] ACPI: Lid Switch [LID] 
[   29.430229] input: Sleep Button (CM) as /devices/virtual/input/input5 
[   29.464008] Yenta: CardBus bridge found at 0000:02:09.0 [107b:0367] 
[   29.464037] Yenta: Using CSCINT to route CSC interrupts to PCI 
[   29.464040] Yenta: Routing CardBus interrupts to PCI 
[   29.464046] Yenta TI: socket 0000:02:09.0, mfunc 0x01ac1b22, devctl 0x64 
[   29.477700] ACPI: Sleep Button (CM) [SLPB] 
[   29.477769] input: Power Button (CM) as /devices/virtual/input/input6 
[   29.541681] ACPI: Power Button (CM) [PWRB] 
[   29.541934] ACPI: AC Adapter [ACAD] (off-line) 
[   29.586585] ACPI: Battery Slot [BAT1] (battery present) 
[   29.698277] Yenta: ISA IRQ mask 0x0ef8, PCI irq 20 
[   29.698283] Socket status: 30000006 
[   29.698287] pcmcia: parent PCI bridge Memory window: 0xc0200000 - 0xc02fffff 
[   29.741641] ACPI: PCI Interrupt 0000:02:09.2[A] -> GSI 20 (level, low) -> IRQ 20 
[   29.860301] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008 
[   29.894764] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7 
[   29.953991] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/LNXVIDEO:00/input/input8 
[   30.021272] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no) 
[   30.317144] ACPI: PCI Interrupt 0000:00:14.2[A] -> GSI 16 (level, low) -> IRQ 16 
[   30.465710] phy0: Selected rate control algorithm 'simple' 
[   30.577712] phy0: hwaddr 00:c0:a8:f0:ee:d0, rtl8187 V1 + rtl8225z2 
[   30.577732] usbcore: registered new interface driver rtl8187 
[   32.051375] lp: driver loaded but no devices found 
[   32.222254] Adding 5654840k swap on /dev/hda5.  Priority:-1 extents:1 across:5654840k 
[   32.252563] EXT3 FS on hda1, internal journal 
[   32.984359] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   33.476299] No dock devices found. 
[   33.830474] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-56 processors (2 cpu cores) (version 2.20.00) 
[   33.830371] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x13 
[   33.830376] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0x15 
[   33.830379] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x1e 
[   34.783905] ppdev: user-space parallel port driver 
[   34.992473] audit(1229531220.120:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4902 profile="/usr/sbin/cupsd" namespace="default" 
[   35.954508] Bluetooth: Core ver 2.11 
[   35.954600] NET: Registered protocol family 31 
[   35.954602] Bluetooth: HCI device and connection manager initialized 
[   35.954607] Bluetooth: HCI socket layer initialized 
[   35.975807] Bluetooth: L2CAP ver 2.9 
[   35.975812] Bluetooth: L2CAP socket layer initialized 
[   36.049738] Bluetooth: RFCOMM socket layer initialized 
[   36.049761] Bluetooth: RFCOMM TTY layer initialized 
[   36.049764] Bluetooth: RFCOMM ver 1.8 
[   36.462103] Clocksource tsc unstable (delta = -251363558 ns) 
[   41.480895] hda-intel: Invalid position buffer, using LPIB read method instead. 
[   48.890889] NET: Registered protocol family 10 
[   48.891351] lo: Disabled Privacy Extensions 
[   48.892156] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[   52.800574] CPU0 attaching NULL sched-domain. 
[   52.800580] CPU1 attaching NULL sched-domain. 
[   52.808638] CPU0 attaching sched-domain: 
[   52.808645]  domain 0: span 03 
[   52.808647]   groups: 01 02 
[   52.808651]   domain 1: span 03 
[   52.808652]    groups: 03 
[   52.808654]    domain 2: span 03 
[   52.808656]     groups: 03 
[   52.808658] CPU1 attaching sched-domain: 
[   52.808660]  domain 0: span 03 
[   52.808661]   groups: 02 01 
[   52.808664]   domain 1: span 03 
[   52.808665]    groups: 03 
[   52.808667]    domain 2: span 03 
[   52.808669]     groups: 03 
[  271.065993] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[  271.979077] NET: Registered protocol family 17 
[  273.063915] wlan0: Initial auth_alg=0 
[  273.063923] wlan0: authenticate with AP 00:d0:9e:cf:16:61 
[  273.065039] wlan0: RX authentication from 00:d0:9e:cf:16:61 (alg=0 transaction=2 status=0) 
[  273.065042] wlan0: authenticated 
[  273.065044] wlan0: associate with AP 00:d0:9e:cf:16:61 
[  273.154608] wlan0: associate with AP 00:d0:9e:cf:16:61 
[  273.245243] wlan0: associate with AP 00:d0:9e:cf:16:61 
[  273.335872] wlan0: association with AP 00:d0:9e:cf:16:61 timed out 
[  612.550009] usb 3-2: new high speed USB device using ehci_hcd and address 3 
[  612.616260] usb 3-2: configuration #1 chosen from 1 choice 
[  612.693248] usbcore: registered new interface driver libusual 
[  612.716017] Initializing USB Mass Storage driver... 
[  612.718488] scsi0 : SCSI emulation for USB Mass Storage devices 
[  612.719979] usbcore: registered new interface driver usb-storage 
[  612.719987] USB Mass Storage support registered. 
[  612.720322] usb-storage: device found at 3 
[  612.720325] usb-storage: waiting for device to settle before scanning 
[  614.942090] usb-storage: device scan complete 
[  614.942416] scsi 0:0:0:0: Direct-Access     SanDisk  Cruzer           8.01 PQ: 0 ANSI: 0 CCS 
[  614.970115] Driver 'sd' needs updating - please use bus_type methods 
[  614.970778] sd 0:0:0:0: [sda] 15682559 512-byte hardware sectors (8029 MB) 
[  614.971181] sd 0:0:0:0: [sda] Write Protect is off 
[  614.971185] sd 0:0:0:0: [sda] Mode Sense: 45 00 00 08 
[  614.971187] sd 0:0:0:0: [sda] Assuming drive cache: write through 
[  614.972335] sd 0:0:0:0: [sda] 15682559 512-byte hardware sectors (8029 MB) 
[  614.972837] sd 0:0:0:0: [sda] Write Protect is off 
[  614.972841] sd 0:0:0:0: [sda] Mode Sense: 45 00 00 08 
[  614.972843] sd 0:0:0:0: [sda] Assuming drive cache: write through 
[  614.972849]  sda: sda1 
[  614.973662] sd 0:0:0:0: [sda] Attached SCSI removable disk 
[  614.988176] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[  792.677942] CPU0 attaching NULL sched-domain. 
[  792.677952] CPU1 attaching NULL sched-domain. 
[  792.689280] CPU0 attaching sched-domain: 
[  792.689290]  domain 0: span 03 
[  792.689292]   groups: 01 02 
[  792.689298]   domain 1: span 03 
[  792.689300]    groups: 03 
[  792.689302] CPU1 attaching sched-domain: 
[  792.689303]  domain 0: span 03 
[  792.689305]   groups: 02 01 
[  792.689307]   domain 1: span 03 
[  792.689309]    groups: 03 
[  792.764078] CPU0 attaching NULL sched-domain. 
[  792.764088] CPU1 attaching NULL sched-domain. 
[  792.771816] CPU0 attaching sched-domain: 
[  792.771824]  domain 0: span 03 
[  792.771826]   groups: 01 02 
[  792.771829]   domain 1: span 03 
[  792.771831]    groups: 03 
[  792.771833]    domain 2: span 03 
[  792.771834]     groups: 03 
[  792.771836] CPU1 attaching sched-domain: 
[  792.771838]  domain 0: span 03 
[  792.771839]   groups: 02 01 
[  792.771842]   domain 1: span 03 
[  792.771843]    groups: 03 
[  792.771845]    domain 2: span 03 
[  792.771847]     groups: 03 
[  793.237839] CPU0 attaching NULL sched-domain. 
[  793.237848] CPU1 attaching NULL sched-domain. 
[  793.249019] CPU0 attaching sched-domain: 
[  793.249025]  domain 0: span 03 
[  793.249028]   groups: 01 02 
[  793.249033]   domain 1: span 03 
[  793.249035]    groups: 03 
[  793.249037] CPU1 attaching sched-domain: 
[  793.249039]  domain 0: span 03 
[  793.249041]   groups: 02 01 
[  793.249043]   domain 1: span 03 
[  793.249046]    groups: 03 
[ 1250.379171] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw. 
[ 1250.379177] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools. 
[ 1250.379180] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details. 
[ 1444.201014] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1449.879787] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
[ 1508.857118] wlan0: Initial auth_alg=0 
[ 1508.857125] wlan0: authenticate with AP 00:d0:9e:cf:16:61 
[ 1508.857952] wlan0: RX authentication from 00:d0:9e:cf:16:61 (alg=0 transaction=2 status=0) 
[ 1508.857955] wlan0: authenticated 
[ 1508.857958] wlan0: associate with AP 00:d0:9e:cf:16:61 
[ 1508.948533] wlan0: associate with AP 00:d0:9e:cf:16:61 
[ 1509.039164] wlan0: associate with AP 00:d0:9e:cf:16:61 
[ 1509.129795] wlan0: association with AP 00:d0:9e:cf:16:61 timed out 
[ 1530.418939] wlan0: Initial auth_alg=0 
[ 1530.418945] wlan0: authenticate with AP 00:d0:9e:cf:16:61 
[ 1530.508091] wlan0: authenticate with AP 00:d0:9e:cf:16:61 
[ 1530.524672] wlan0: RX authentication from 00:d0:9e:cf:16:61 (alg=0 transaction=2 status=0) 
[ 1530.524676] wlan0: authenticated 
[ 1530.524679] wlan0: associate with AP 00:d0:9e:cf:16:61 
[ 1530.525440] wlan0: authentication frame received from 00:d0:9e:cf:16:61, but not in authenticate state - ignored 
[ 1530.547463] wlan0: Initial auth_alg=0 
[ 1530.547470] wlan0: authenticate with AP 00:d0:9e:cf:16:61 
[ 1530.636315] wlan0: authenticate with AP 00:d0:9e:cf:16:61 
[ 1530.703583] wlan0: authenticate with AP 00:d0:9e:cf:16:61 
[ 1530.794200] wlan0: authentication with AP 00:d0:9e:cf:16:61 timed out 
```

```
***sudo lshw -C network***
PCI (sysfs)   
  *-network                
       description: Wireless interface 
       physical id: 2 
       logical name: wlan0 
       serial: 00:c0:a8:f0:ee:d0 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g 
```

```
***iwlist scan***
lo        Interface doesn't support scanning. 
 
wmaster0  Interface doesn't support scanning. 
 
wlan0     Scan completed : 
          Cell 01 - Address: 00:1B:5B:54:38:51 
                    ESSID:"2WIRE943" 
                    Mode:Master 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=32/64  Signal level=13/65   
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=00000000bcc861d3 
          Cell 02 - Address: 00:22:A4:E0:0B:39 
                    ESSID:"2WIRE564" 
                    Mode:Master 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=57/64  Signal level=15/65   
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=00000004443f6fd1 
          Cell 03 - Address: 00:1A:C4:C0:9F:D1 
                    ESSID:"2WIRE992" 
                    Mode:Master 
                    Channel:3 
                    Frequency:2.422 GHz (Channel 3) 
                    Quality=48/64  Signal level=12/65   
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s 
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=00000028e2f576f1 
          Cell 04 - Address: 00:14:95:7B:54:A1 
                    ESSID:"2WIRE920" 
                    Mode:Master 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=51/64  Signal level=21/65   
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=000000055a7565cc 
          Cell 05 - Address: 00:90:4C:7E:00:64 
                    ESSID:"NETGEAR" 
                    Mode:Master 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=34/64  Signal level=7/65   
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s 
                              12 Mb/s; 48 Mb/s 
                    Extra:tsf=000000090c8418b9 
          Cell 06 - Address: 00:D0:9E:CF:16:61 
                    ESSID:"SliTCX-PN" 
                    Mode:Master 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=52/64  Signal level=65/65   
                    Encryption key:on 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s 
                    Extra:tsf=0000000035d086d2 
```

```
***lsb_release -d***
Description:	Ubuntu 8.04.1 

```

```
***uname -mr***
2.6.24-19-generic x86_64 

```

```
***sudo /etc/init.d/networking restart***
 * Reconfiguring network interfaces...                                   [ OK ]  

```

---

### Post by phantom3113 on 2009-01-07
If I'm correct in assuming that the internet you're losing connection on is on an entirely different computer, it sounds like you may have a driver issue with the laptop. I actually had a similar problem with mine, and my laptop model isn't too far off from yours (Gateway T-1621). If you recently installed Hardy and haven't done anything with your wireless yet, I highly recommend following this site: [https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b) (option #1) STEP-BY-STEP. It's a little complex if you're new to Linux, but as long as you follow everything word for word, it should work beautifully for you. The only downside is that Network Manager won't show the correct signal strength (ex: 80% when you're a foot from the router) Hope this helps!

---

