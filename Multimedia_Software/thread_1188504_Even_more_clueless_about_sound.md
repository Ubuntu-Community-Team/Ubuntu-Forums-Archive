---
title: "Even more clueless about sound"
date: 2009-06-15
forum: Multimedia Software
---

### Post by zoe-scutterbug on 2009-06-15
Hiya 

My Problem: No Sound/Sound card no longer recognised.

After a recent reinstall and upgrade from gutsy - hardy to intrepid
I have ...With my special talent i made a small sound problem into big one and 
I totally messed up my sound once again!  My system cant even see my 
on board sound card. I have tried following various  guides but I have
missed someting and made it worse.. I am lost and going round in circles
and getting no where.

Any advise would be appreciated. whole bunch of info below, being clueless
I am not sure which will help.

Many thanks
zoe

zoe@OpenGEUbox:~$ aplay -l
aplay: device_list:215: no soundcards found...

........................

zoe@OpenGEUbox:~$ lspci -v | less

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Device 81cb
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at fe028000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel
.................................

<Sound prefs...testing sound>

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect: Connection refused


zoe@OpenGEUbox:~$ sudo gedit /etc/modprobe.d/alsa-base
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel probe_mask=1

.....................................

zoe@OpenGEUbox:~$ pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.                                                                      
I: core-util.c: Successfully gained nice level -11.                             
W: ltdl-bind-now.c: Failed to find original dlopen loader.                      
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted     
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
I: module-hal-detect.c: Loaded 0 modules.
I: module.c: Loaded "module-hal-detect" (index: #0; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #1; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #3; argument: "").
I: module-volume-restore.c: starting with empty ruleset.
I: module.c: Loaded "module-volume-restore" (index: #4; argument: "").
D: module-default-device-restore.c: No previous default sink setting, ignoring.
D: module-default-device-restore.c: No previous default source setting, ignoring.
I: module.c: Loaded "module-default-device-restore" (index: #5; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #6; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #8; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired

...........................


!!################################
!!ALSA Information Script v 0.4.56
!!################################

!!Script ran on: Mon Jun 15 23:21:01 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 8.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 8.10"


!!DMI Information
!!---------------

Manufacturer:      
Product Name:      


!!Kernel Information
!!------------------

Kernel release:    2.6.27-14-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.20
Library version:    1.0.17a
Utilities version:  1.0.17


!!Loaded ALSA modules
!!-------------------



!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

aRts:
      Installed - Yes (/usr/bin/artsd)
      Running - No

Jack:
      Installed - Yes (/usr/bin/jackd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

--- no soundcards ---


!!PCI Soundcards installed in the system
!!--------------------------------------

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:10.1 0403: 10de:026c (rev a2)
    Subsystem: 1043:81cb


!!Modprobe options (Sound related)
!!--------------------------------

snd-hda-intel: model=5stack
snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-hda-intel: probe_mask=1


!!Loaded sound module options
!!--------------------------


!!ALSA Device nodes
!!-----------------

crw-rw----  1 root audio 116,  1 Jun 16 00:06 /dev/snd/seq
crw-rw----  1 root audio 116, 33 Jun 16 00:06 /dev/snd/timer


!!ALSA configuration files
!!------------------------

!!System wide config file (/etc/asound.conf)




!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:215: no soundcards found...

ARECORD

arecord: device_list:215: no soundcards found...

!!Amixer output
!!-------------


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
snd_pcm_oss
snd_pcm
snd_page_alloc
snd_mixer_oss
snd_seq_oss
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
snd
soundcore
binfmt_misc
sco
bridge
stp
bnep
rfcomm
l2cap
bluetooth
af_packet
kvm_amd
kvm
ppdev
ipv6
powernow_k8
cpufreq_powersave
cpufreq_stats
cpufreq_userspace
cpufreq_ondemand
cpufreq_conservative
freq_table
video
output
container
wmi
sbs
sbshc
pci_slot
battery
iptable_filter
ip_tables
x_tables
ac
ac97_bus
sbp2
lp
joydev
dm_multipath
scsi_dh
evdev
wlan_scan_sta
ath_rate_sample
parport_pc
parport
ath_pci
wlan
ath_hal
psmouse
button
i2c_nforce2
serio_raw
nvidia
agpgart
pcspkr
i2c_core
k8temp
ext3
jbd
mbcache
sd_mod
crc_t10dif
usb_storage
sr_mod
cdrom
usbhid
hid
sg
sata_nv
pata_acpi
libusual
pata_amd
ata_generic
ohci1394
ohci_hcd
forcedeth
ehci_hcd
ieee1394
libata
scsi_mod
dock
usbcore
dm_mirror
dm_log
dm_snapshot
dm_mod
thermal
processor
fan
fbcon
tileblit
font
bitblit
softcursor
fuse
compcache
lzo_decompress
lzo_compress
tlsf




thanks
zoe

---

### Post by zoe-scutterbug on 2009-06-16
more info

zoe@OpenGEUbox:~$ lsmod | grep snd_hda_intel


zoe@OpenGEUbox:~$ sudo modprobe snd_hda_intel
[sudo] password for zoe:                     
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)                                                                         
zoe@OpenGEUbox:~$ dmesg                                                         
[    0.000000] Initializing cgroup subsys cpuset                                
[    0.000000] Initializing cgroup subsys cpu                                   
[    0.000000] Linux version 2.6.27-14-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Fri Jun 5 10:14:59 UTC 2009 (Ubuntu 2.6.27-14.34-generic)                                                                
[    0.000000] BIOS-provided physical RAM map:                                  
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)         
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)       
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)       
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077ef0000 (usable)         
[    0.000000]  BIOS-e820: 0000000077ef0000 - 0000000077ef3000 (ACPI NVS)       
[    0.000000]  BIOS-e820: 0000000077ef3000 - 0000000077f00000 (ACPI data)      
[    0.000000]  BIOS-e820: 0000000078000000 - 0000000080000000 (reserved)       
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)       
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)       
[    0.000000] DMI 2.3 present.                                                 
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.                                                                              
[    0.000000] last_pfn = 0x77ef0 max_arch_pfn = 0x100000                       
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000        
[    0.000000] RAMDISK: 3770d000 - 37fef32c                                     
[    0.000000] ACPI: RSDP 000F6D00, 0014 (r0 Nvidia)                            
[    0.000000] ACPI: RSDT 77EF3040, 0034 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)                                                                            
[    0.000000] ACPI: FACP 77EF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)                                                                            
[    0.000000] ACPI: DSDT 77EF3180, 6E72 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)                                                                            
[    0.000000] ACPI: FACS 77EF0000, 0040                                        
[    0.000000] ACPI: SSDT 77EFA100, 030E (r1 PTLTD  POWERNOW        1  LTP        1)                                                                            
[    0.000000] ACPI: MCFG 77EFA480, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)                                                                            
[    0.000000] ACPI: APIC 77EFA040, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)                                                                            
[    0.000000] 1022MB HIGHMEM available.                                        
[    0.000000] 896MB LOWMEM available.                                          
[    0.000000]   mapped low ram: 0 - 38000000                                   
[    0.000000]   low ram: 00000000 - 38000000                                   
[    0.000000]   bootmap 00011000 - 00018000                                    
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]     
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                                    
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                                                    
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                                                    
[    0.000000]   #3 [0000100000 - 00005c59e0]    TEXT DATA BSS ==> [0000100000 - 00005c59e0]                                                                    
[    0.000000]   #4 [003770d000 - 0037fef32c]          RAMDISK ==> [003770d000 - 0037fef32c]                                                                    
[    0.000000]   #5 [00005c6000 - 00005c9000]    INIT_PG_TABLE ==> [00005c6000 - 00005c9000]                                                                    
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]                                                                    
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]                                                                    
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]                                                                    
[    0.000000] found SMP MP-table at [c00f5270] 000f5270                        
[    0.000000] Zone PFN ranges:                                                 
[    0.000000]   DMA      0x00000010 -> 0x00001000                              
[    0.000000]   Normal   0x00001000 -> 0x00038000                              
[    0.000000]   HighMem  0x00038000 -> 0x00077ef0                              
[    0.000000] Movable zone start PFN for each node                             
[    0.000000] early_node_map[2] active PFN ranges                              
[    0.000000]     0: 0x00000010 -> 0x0000009f                                  
[    0.000000]     0: 0x00000100 -> 0x00077ef0                                  
[    0.000000] On node 0 totalpages: 491135                                     
[    0.000000] free_area_init_node: node 0, pgdat c048d700, node_mem_map c1000240                                                                               
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0                             
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31                       
[    0.000000]   HighMem zone: 259570 pages, LIFO batch:31                      
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.             
[    0.000000] If you got timer trouble try acpi_use_timer_override             
[    0.000000] ACPI: PM-Timer IO Port: 0x4008                                   
[    0.000000] ACPI: Local APIC address 0xfee00000                              
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)               
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)               
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])              
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])              
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])          
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23   
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)         
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.                           
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)      
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)     
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)     
[    0.000000] ACPI: IRQ9 used by override.                                     
[    0.000000] ACPI: IRQ14 used by override.                                    
[    0.000000] ACPI: IRQ15 used by override.                                    
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                    
[    0.000000] Using ACPI (MADT) for SMP configuration information              
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs                             
[    0.000000] mapped APIC to ffffb000 (fee00000)                               
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)                             
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)                                                                           
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data                   
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1                        
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 486817                                                                      
[    0.000000] Kernel command line: root=UUID=e2491bd4-3091-40b5-8e3b-0201950859ea ro quiet splash                                                              
[    0.000000] Enabling fast FPU save and restore... done.                      
[    0.000000] Enabling unmasked SIMD FPU exception support... done.            
[    0.000000] Initializing CPU#0                                               
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)            
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.                       
[    0.000000] TSC: using PIT calibration value                                 
[    0.000000] Detected 3013.823 MHz processor.                                 
[    0.004000] spurious 8259A interrupt: IRQ7.                                  
[    0.004000] Console: colour VGA+ 80x25                                       
[    0.004000] console [tty0] enabled                                           
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes) 
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)   
[    0.004000] Memory: 1931416k/1964992k available (2581k kernel code, 32208k reserved, 1163k data, 428k init, 1047488k highmem)                                
[    0.004000] virtual kernel memory layout:                                    
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)                
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)                
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)                
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)                
[    0.004000]       .init : 0xc04af000 - 0xc051a000   ( 428 kB)                
[    0.004000]       .data : 0xc038571a - 0xc04a8680   (1163 kB)                
[    0.004000]       .text : 0xc0100000 - 0xc038571a   (2581 kB)                
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                                                      
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated             
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1                                                                          
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6027.64 BogoMIPS (lpj=12055292)                                       
[    0.004021] Security Framework initialized                                   
[    0.004026] SELinux:  Disabled at boot.                                      
[    0.004042] AppArmor: AppArmor initialized                                   
[    0.004048] Mount-cache hash table entries: 512                              
[    0.004168] Initializing cgroup subsys ns                                    
[    0.004171] Initializing cgroup subsys cpuacct                               
[    0.004173] Initializing cgroup subsys memory                                
[    0.004182] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004184] CPU: L2 Cache: 1024K (64 bytes/line)                             
[    0.004186] CPU 0(2) -> Core 0                                               
[    0.004189] using C1E aware idle routine                                     
[    0.004197] Checking 'hlt' instruction... OK.                                
[    0.021132] ACPI: Core revision 20080609                                     
[    0.022895] ACPI: Checking initramfs for custom DSDT                         
[    0.276348] ENABLING IO-APIC IRQs                                            
[    0.276567] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1             
[    0.284017] ..MP-BIOS bug: 8254 timer not connected to IO-APIC               
[    0.284017] ...trying to set up timer (IRQ0) through the 8259A ...           
[    0.284017] ..... (found apic 0 pin 0) ...                                   
[    0.292018] ....... failed.                                                  
[    0.292018] ...trying to set up timer as Virtual Wire IRQ...                 
[    0.292018] ..... failed.                                                    
[    0.292018] ...trying to set up timer as ExtINT IRQ...                       
[    0.335314] ..... works.                                                     
[    0.335315] CPU0: AMD Processor model unknown stepping 03                    
[    0.336021] Booting processor 1/1 ip 6000                                    
[    0.004000] Initializing CPU#1                                               
[    0.388024] Calibrating delay using timer specific routine.. 6028.18 BogoMIPS (lpj=12056368)                                                                 
[    0.388024] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.388024] CPU: L2 Cache: 1024K (64 bytes/line)                             
[    0.388024] CPU 1(2) -> Core 1                                               
[    0.420216] CPU1: AMD Processor model unknown stepping 03                    
[    0.420236] Brought up 2 CPUs                                                
[    0.420238] Total of 2 processors activated (12055.83 BogoMIPS).             
[    0.420278] CPU0 attaching sched-domain:                                     
[    0.420280]  domain 0: span 0-1 level CPU                                    
[    0.420282]   groups: 0 1                                                    
[    0.420286] CPU1 attaching sched-domain:                                     
[    0.420288]  domain 0: span 0-1 level CPU                                    
[    0.420289]   groups: 1 0                                                    
[    0.420333] net_namespace: 840 bytes                                         
[    0.420333] Booting paravirtualized kernel on bare hardware                  
[    0.420333] Time: 16:36:36  Date: 06/16/09                                   
[    0.420333] NET: Registered protocol family 16                               
[    0.420333] EISA bus registered                                              
[    0.420333] ACPI: bus type pci registered                                    
[    0.420333] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 255 
[    0.420333] PCI: MCFG area at f0000000 reserved in E820                      
[    0.420333] PCI: updated MCFG configuration 0: base f0000000 segment 0 buses 0 - 63                                                                          
[    0.420333] PCI: Using MMCONFIG for extended config space                    
[    0.420333] PCI: Using configuration type 1 for base access                  
[    0.420910] ACPI: EC: Look up EC in DSDT                                     
[    0.430298] ACPI: Interpreter enabled                                        
[    0.430301] ACPI: (supports S0 S1 S3 S4 S5)                                  
[    0.430312] ACPI: Using IOAPIC for interrupt routing                         
[    0.436524] ACPI: PCI Root Bridge [PCI0] (0000:00)                           
[    0.436524] PCI: 0000:00:05.0 reg 10 32bit mmio: [fb000000, fbffffff]        
[    0.436524] PCI: 0000:00:05.0 reg 14 64bit mmio: [e0000000, efffffff]        
[    0.436524] PCI: 0000:00:05.0 reg 1c 64bit mmio: [fc000000, fcffffff]        
[    0.436524] PCI: 0000:00:05.0 reg 30 32bit mmio: [0, 1ffff]                  
[    0.436524] HPET not enabled in BIOS. You might try hpet=force boot option   
[    0.436524] PCI: 0000:00:0a.1 reg 20 io port: [4c00, 4c3f]                   
[    0.436524] PCI: 0000:00:0a.1 reg 24 io port: [4c40, 4c7f]                   
[    0.436524] pci 0000:00:0a.1: PME# supported from D3hot D3cold               
[    0.436524] pci 0000:00:0a.1: PME# disabled                                  
[    0.436524] PCI: 0000:00:0b.0 reg 10 32bit mmio: [fe02f000, fe02ffff]        
[    0.436533] pci 0000:00:0b.0: supports D1                                    
[    0.436534] pci 0000:00:0b.0: supports D2                                    
[    0.436536] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold      
[    0.436539] pci 0000:00:0b.0: PME# disabled                                  
[    0.436556] PCI: 0000:00:0b.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]        
[    0.436586] pci 0000:00:0b.1: supports D1                                    
[    0.436587] pci 0000:00:0b.1: supports D2                                    
[    0.436589] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold      
[    0.436592] pci 0000:00:0b.1: PME# disabled                                  
[    0.436618] PCI: 0000:00:0d.0 reg 20 io port: [f400, f40f]                   
[    0.436652] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]                     
[    0.436656] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]                     
[    0.436659] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]                     
[    0.436663] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]                     
[    0.436666] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]                   
[    0.436670] PCI: 0000:00:0e.0 reg 24 32bit mmio: [fe02d000, fe02dfff]        
[    0.440037] PCI: 0000:00:10.1 reg 10 32bit mmio: [fe028000, fe02bfff]        
[    0.440072] pci 0000:00:10.1: PME# supported from D3hot D3cold               
[    0.440075] pci 0000:00:10.1: PME# disabled                                  
[    0.440097] PCI: 0000:00:14.0 reg 10 32bit mmio: [fe02c000, fe02cfff]        
[    0.440101] PCI: 0000:00:14.0 reg 14 io port: [dc00, dc07]                   
[    0.440122] pci 0000:00:14.0: supports D1                                    
[    0.440123] pci 0000:00:14.0: supports D2                                    
[    0.440125] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold      
[    0.440128] pci 0000:00:14.0: PME# disabled                                  
[    0.440199] PCI: 0000:01:03.0 reg 10 32bit mmio: [fddff000, fddff7ff]        
[    0.440204] PCI: 0000:01:03.0 reg 14 io port: [cc00, cc7f]                   
[    0.440238] pci 0000:01:03.0: supports D2                                    
[    0.440240] pci 0000:01:03.0: PME# supported from D2 D3hot D3cold            
[    0.440243] pci 0000:01:03.0: PME# disabled                                  
[    0.440271] PCI: 0000:01:0e.0 reg 10 32bit mmio: [fdde0000, fddeffff]        
[    0.440323] pci 0000:00:10.0: transparent bridge                             
[    0.440326] PCI: bridge 0000:00:10.0 io port: [c000, cfff]                   
[    0.440329] PCI: bridge 0000:00:10.0 32bit mmio: [fdd00000, fddfffff]        
[    0.440331] PCI: bridge 0000:00:10.0 32bit mmio pref: [fde00000, fdefffff]   
[    0.440336] bus 00 -> node 0                                                 
[    0.440341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]              
[    0.440580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]         
[    0.517935] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.517935] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)        
[    0.517935] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.517935] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.517935] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.517935] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.517935] ACPI: PCI Interrupt Link [LNK7] (IRQs *5 7 9 10 11 14 15)        
[    0.517935] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.517935] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.517935] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.517964] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)        
[    0.520202] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.520382] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)        
[    0.520560] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.520738] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.520916] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.521095] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.521273] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.521453] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)        
[    0.521630] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                           
[    0.521846] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.          
[    0.522056] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0                     
[    0.522265] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.          
[    0.522475] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.          
[    0.522684] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.          
[    0.522894] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.          
[    0.523103] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0                     
[    0.523312] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.          
[    0.523522] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled. 
[    0.523733] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled. 
[    0.523946] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0            
[    0.524168] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled. 
[    0.524379] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled. 
[    0.524591] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0            
[    0.524802] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled. 
[    0.525013] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled. 
[    0.525225] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled. 
[    0.525436] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled. 
[    0.525647] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled. 
[    0.525859] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0            
[    0.526070] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled. 
[    0.526130] Linux Plug and Play Support v0.97 (c) Adam Belay                 
[    0.526130] pnp: PnP ACPI init                                               
[    0.526130] ACPI: bus type pnp registered                                    
[    0.529445] pnp: PnP ACPI: found 11 devices                                  
[    0.529445] ACPI: ACPI bus type pnp unregistered                             
[    0.529445] PnPBIOS: Disabled by ACPI PNP                                    
[    0.529445] PCI: Using ACPI for IRQ routing                                  
[    0.536038] NET: Registered protocol family 8                                
[    0.536039] NET: Registered protocol family 20                               
[    0.536059] NetLabel: Initializing                                           
[    0.536060] NetLabel:  domain hash size = 128                                
[    0.536062] NetLabel:  protocols = UNLABELED CIPSOv4                         
[    0.536072] NetLabel:  unlabeled traffic allowed by default                  
[    0.536451] tracer: 772 pages allocated for 65536 entries of 48 bytes        
[    0.536452]    actual entries 65620                                          
[    0.536552] AppArmor: AppArmor Filesystem Enabled                            
[    0.536578] ACPI: RTC can wake from S4                                       
[    0.544045] system 00:01: ioport range 0x4000-0x407f has been reserved       
[    0.544047] system 00:01: ioport range 0x4080-0x40ff has been reserved       
[    0.544049] system 00:01: ioport range 0x4400-0x447f has been reserved       
[    0.544051] system 00:01: ioport range 0x4480-0x44ff has been reserved       
[    0.544053] system 00:01: ioport range 0x4800-0x487f has been reserved       
[    0.544055] system 00:01: ioport range 0x4880-0x48ff has been reserved       
[    0.544057] system 00:01: ioport range 0x2000-0x207f has been reserved       
[    0.544059] system 00:01: ioport range 0x2080-0x20ff has been reserved       
[    0.544061] system 00:01: iomem range 0x78000000-0x7fffffff could not be reserved                                                                            
[    0.544065] system 00:02: ioport range 0x4d0-0x4d1 has been reserved         
[    0.544067] system 00:02: ioport range 0x800-0x87f has been reserved         
[    0.544073] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved                                                                            
[    0.544077] system 00:0a: iomem range 0xd5800-0xd7fff has been reserved      
[    0.544079] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved  
[    0.544081] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved  
[    0.544083] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved  
[    0.544086] system 00:0a: iomem range 0x77ef0000-0x77efffff could not be reserved                                                                            
[    0.544088] system 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved                                                                            
[    0.544090] system 00:0a: iomem range 0x0-0x9ffff could not be reserved      
[    0.544092] system 00:0a: iomem range 0x100000-0x77eeffff could not be reserved                                                                              
[    0.544094] system 00:0a: iomem range 0x77f00000-0x7fefffff could not be reserved                                                                            
[    0.544096] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved                                                                            
[    0.544099] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved                                                                            
[    0.544101] system 00:0a: iomem range 0xfefff000-0xfeffffff could not be reserved                                                                            
[    0.544103] system 00:0a: iomem range 0xfff80000-0xfff80fff could not be reserved                                                                            
[    0.544105] system 00:0a: iomem range 0xfff90000-0xfffbffff could not be reserved                                                                            
[    0.544108] system 00:0a: iomem range 0xfffed000-0xfffeffff could not be reserved                                                                            
[    0.579028] pci 0000:00:10.0: PCI bridge, secondary bus 0000:01              
[    0.579031] pci 0000:00:10.0:   IO window: 0xc000-0xcfff                     
[    0.579034] pci 0000:00:10.0:   MEM window: 0xfdd00000-0xfddfffff            
[    0.579037] pci 0000:00:10.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff                                                                           
[    0.579046] pci 0000:00:10.0: setting latency timer to 64                    
[    0.579048] bus: 00 index 0 io port: [0, ffff]                               
[    0.579050] bus: 00 index 1 mmio: [0, ffffffff]                              
[    0.579051] bus: 01 index 0 io port: [c000, cfff]                            
[    0.579053] bus: 01 index 1 mmio: [fdd00000, fddfffff]                       
[    0.579054] bus: 01 index 2 mmio: [fde00000, fdefffff]                       
[    0.579056] bus: 01 index 3 io port: [0, ffff]                               
[    0.579057] bus: 01 index 4 mmio: [0, ffffffff]                              
[    0.579065] NET: Registered protocol family 2                                
[    0.580047] Switched to high resolution mode on CPU 0                        
[    0.580256] Switched to high resolution mode on CPU 1                        
[    0.592049] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.592251] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)                                                                             
[    0.592780] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)      
[    0.593021] TCP: Hash tables configured (established 131072 bind 65536)      
[    0.593023] TCP reno registered                                              
[    0.600075] NET: Registered protocol family 1                                
[    0.600164] checking if image is initramfs... it is                          
[    1.116668] Freeing initrd memory: 9096k freed                               
[    1.117684] audit: initializing netlink socket (disabled)                    
[    1.117699] type=2000 audit(1245170196.116:1): initialized                   
[    1.121699] highmem bounce pool size: 64 pages                               
[    1.121703] HugeTLB registered 4 MB page size, pre-allocated 0 pages         
[    1.123987] VFS: Disk quotas dquot_6.5.1                                     
[    1.124083] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)       
[    1.124165] msgmni has been set to 1745                                      
[    1.124270] io scheduler noop registered                                     
[    1.124271] io scheduler anticipatory registered                             
[    1.124273] io scheduler deadline registered                                 
[    1.124281] io scheduler cfq registered (default)                            
[    1.124293] pci 0000:00:00.0: Enabling HT MSI Mapping                        
[    1.124320] pci 0000:00:05.0: Boot video device                              
[    1.124339] pci 0000:00:09.0: Enabling HT MSI Mapping                        
[    1.141052] pci 0000:00:0e.0: Enabling HT MSI Mapping                        
[    1.141060] pci 0000:00:10.0: Enabling HT MSI Mapping                        
[    1.141071] pci 0000:00:10.1: Enabling HT MSI Mapping                        
[    1.141390] isapnp: Scanning for PnP cards...                                
[    1.494231] isapnp: No Plug & Play device found                              
[    1.523318] Serial: 8250/16550 driver4 ports, IRQ sharing enabled            
[    1.523457] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A             
[    1.524054] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A                  
[    1.525673] brd: module loaded                                               
[    1.525734] input: Macintosh mouse button emulation as /devices/virtual/input/input0                                                                         
[    1.525890] PNP: No PS/2 controller found. Probing ports directly.           
[    1.528763] serio: i8042 KBD port at 0x60,0x64 irq 1                         
[    1.528767] serio: i8042 AUX port at 0x60,0x64 irq 12                        
[    1.529018] mice: PS/2 mouse device common for all mice                      
[    1.529124] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0            
[    1.529150] rtc0: alarms up to one year, y3k                                 
[    1.529263] EISA: Probing bus 0 at eisa.0                                    
[    1.529270] Cannot allocate resource for EISA slot 2                         
[    1.529274] Cannot allocate resource for EISA slot 4                         
[    1.529284] EISA: Detected 0 cards.                                          
[    1.529286] cpuidle: using governor ladder                                   
[    1.529288] cpuidle: using governor menu                                     
[    1.529715] TCP cubic registered                                             
[    1.529735] Using IPI No-Shortcut mode                                       
[    1.529911] registered taskstats version 1                                   
[    1.530009]   Magic number: 13:479:641                                       
[    1.530152] rtc_cmos 00:04: setting system clock to 2009-06-16 16:36:37 UTC (1245170197)                                                                     
[    1.530154] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found             
[    1.530156] EDD information not available.                                   
[    1.530410] Freeing unused kernel memory: 428k freed                         
[    1.530455] Write protecting the kernel text: 2584k                          
[    1.530485] Write protecting the kernel read-only data: 940k                 
[    1.575654] compcache: Compressed swap size set to: 485468 KB                
[    1.576243] TLSF: pool: f881e000, init_size=16384, max_size=0, grow_size=16384                                                                               
[    1.701136] fuse init (API version 7.9)                                      
[    1.752143] fan PNP0C0B:00: registered as cooling_device0                    
[    1.752148] ACPI: Fan [FAN] (on)                                             
[    1.760197] processor ACPI0007:00: registered as cooling_device1             
[    1.760243] processor ACPI0007:01: registered as cooling_device2             
[    1.762997] thermal LNXTHERM:01: registered as thermal_zone0                 
[    1.764905] ACPI: Thermal Zone [THRM] (40 C)                                 
[    1.816162] device-mapper: uevent: version 1.0.3                             
[    1.816345] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]                                                                 
[    2.229181] usbcore: registered new interface driver usbfs                   
[    2.229201] usbcore: registered new interface driver hub                     
[    2.229237] usbcore: registered new device driver usb                        
[    2.229317] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.                                                                              
[    2.231263] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23                
[    2.231273] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23                                                                 
[    2.231277] forcedeth 0000:00:14.0: setting latency timer to 64              
[    2.231303] nv_probe: set workaround bit for reversed mac addr               
[    2.253869] No dock devices found.                                           
[    2.263273] SCSI subsystem initialized                                       
[    2.287989] libata version 3.00 loaded.                                      
[    2.288139] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver                                                                            
[    2.307563] Adding 485464k swap on /dev/ramzswap0.  Priority:100 extents:1 across:485464k                                                                    
[    2.748437] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 11, addr 00:1a:92:55:29:b1                                                                 
[    2.748440] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[    2.749515] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22                
[    2.749526] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22                                                                  
[    2.749538] ohci_hcd 0000:00:0b.0: setting latency timer to 64               
[    2.749541] ohci_hcd 0000:00:0b.0: OHCI Host Controller                      
[    2.749591] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1                                                                             
[    2.749614] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xfe02f000                 
[    2.806256] usb usb1: configuration #1 chosen from 1 choice                  
[    2.806344] hub 1-0:1.0: USB hub found                                       
[    2.806352] hub 1-0:1.0: 8 ports detected                                    
[    3.012504] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21                
[    3.012514] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21                                                                  
[    3.012524] ehci_hcd 0000:00:0b.1: setting latency timer to 64               
[    3.012526] ehci_hcd 0000:00:0b.1: EHCI Host Controller                      
[    3.012556] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2                                                                             
[    3.012579] ehci_hcd 0000:00:0b.1: debug port 1                              
[    3.012582] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported    
[    3.012597] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000                 
[    3.188026] usb 1-3: new full speed USB device using ohci_hcd and address 2  
[    3.201019] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004                                                                            
[    3.201134] usb usb2: configuration #1 chosen from 1 choice                  
[    3.201156] hub 2-0:1.0: USB hub found                                       
[    3.201163] hub 2-0:1.0: 8 ports detected                                    
[    3.256030] hub 1-0:1.0: unable to enumerate USB device on port 3            
[    3.408302] pata_amd 0000:00:0d.0: version 0.3.10                            
[    3.408336] pata_amd 0000:00:0d.0: setting latency timer to 64               
[    3.408402] scsi0 : pata_amd                                                 
[    3.408475] scsi1 : pata_amd                                                 
[    3.409023] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14  
[    3.409025] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15  
[    3.572334] ata1.00: ATAPI: Optiarc DVD RW AD-5170A, 1.13, max UDMA/66       
[    3.572345] ata1: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)                                             
[    3.588280] ata1.00: configured for UDMA/66                                  
[    3.588316] ata2: port disabled. ignoring.                                   
[    3.589213] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-5170A  1.13 PQ: 0 ANSI: 5                                                                     
[    3.591918] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19                
[    3.591928] ohci1394 0000:01:03.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19                                                                  
[    3.644644] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]                             
[    3.650063] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20                
[    3.650080] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20                                                                 
[    3.650114] pata_acpi 0000:00:0e.0: setting latency timer to 64              
[    3.650124] pata_acpi 0000:00:0e.0: PCI INT A disabled                       
[    3.656293] sata_nv 0000:00:0e.0: version 3.5                                
[    3.656304] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20                                                                   
[    3.656307] sata_nv 0000:00:0e.0: Using SWNCQ mode                           
[    3.656339] sata_nv 0000:00:0e.0: setting latency timer to 64                
[    3.656453] scsi2 : sata_nv                                                  
[    3.656518] scsi3 : sata_nv                                                  
[    3.656673] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 20  
[    3.656676] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 20  
[    3.669232] scsi 0:0:0:0: Attached scsi generic sg0 type 5                   
[    3.678236] Driver 'sr' needs updating - please use bus_type methods         
[    3.681212] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray    
[    3.681215] Uniform CD-ROM driver Revision: 3.20                             
[    3.681276] sr 0:0:0:0: Attached scsi CD-ROM sr0                             
[    3.928023] usb 2-7: new high speed USB device using ehci_hcd and address 4  
[    4.131107] usb 2-7: configuration #1 chosen from 1 choice                   
[    4.436026] usb 1-3: new full speed USB device using ohci_hcd and address 3  
[    4.536050] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)           
[    4.544301] ata3.00: ATA-7: ST3250310AS, 3.AAC, max UDMA/133                 
[    4.544304] ata3.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32)     
[    4.561296] ata3.00: configured for UDMA/133                                 
[    4.658281] usb 1-3: configuration #1 chosen from 1 choice                   
[    4.920264] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001234dde]  
[    4.964044] usb 1-4: new low speed USB device using ohci_hcd and address 4   
[    5.173129] usb 1-4: configuration #1 chosen from 1 choice                   
[    5.176292] usbcore: registered new interface driver hiddev                  
[    5.176318] usbcore: registered new interface driver libusual                
[    5.184532] Initializing USB Mass Storage driver...                          
[    5.185250] scsi4 : SCSI emulation for USB Mass Storage devices              
[    5.185666] usb-storage: device found at 4                                   
[    5.185668] usb-storage: waiting for device to settle before scanning        
[    5.188825] input: Microsoft SideWinder? Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3:1.0/input/input1                                             
[    5.200130] input,hidraw0: USB HID v1.11 Mouse [Microsoft SideWinder? Mouse] on usb-0000:00:0b.0-3                                                           
[    5.209277] input: HID 7350:099a as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input2                                                           
[    5.210125] input,hidraw1: USB HID v1.10 Keyboard [HID 7350:099a] on usb-0000:00:0b.0-4                                                                      
[    5.225162] input: HID 7350:099a as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.1/input/input3                                                           
[    5.225340] input,hiddev96,hidraw2: USB HID v1.10 Device [HID 7350:099a] on usb-0000:00:0b.0-4                                                               
[    5.225374] usbcore: registered new interface driver usbhid                  
[    5.225378] usbhid: v2.6:USB HID core driver                                 
[    5.225388] usbcore: registered new interface driver usb-storage             
[    5.225392] USB Mass Storage support registered.                             
[    5.294429] ata4: SATA link down (SStatus 0 SControl 300)                    
[    5.294519] scsi 2:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5                                                                     
[    5.294667] scsi 2:0:0:0: Attached scsi generic sg1 type 0                   
[    5.306955] Driver 'sd' needs updating - please use bus_type methods         
[    5.307036] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.307048] sd 2:0:0:0: [sda] Write Protect is off                           
[    5.307050] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                        
[    5.307067] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                          
[    5.307118] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.307127] sd 2:0:0:0: [sda] Write Protect is off                           
[    5.307128] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00                        
[    5.307143] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA                                                          
[    5.307146]  sda: sda1 sda2 < sda5 >                                         
[    5.348761] sd 2:0:0:0: [sda] Attached SCSI disk                             
[    5.517987] PM: Starting manual resume from disk                             
[    5.517990] PM: Resume from partition 8:5                                    
[    5.517991] PM: Checking hibernation image.                                  
[    5.518153] PM: Resume from disk failed.                                     
[    5.561188] kjournald starting.  Commit interval 5 seconds                   
[    5.561204] EXT3-fs: mounted filesystem with ordered data mode.              
[   10.189572] usb-storage: device scan complete                                
[   10.194034] scsi 4:0:0:0: Direct-Access     ASUS     Flash HS-CF      3.95 PQ: 0 ANSI: 0                                                                     
[   10.197529] scsi 4:0:0:1: Direct-Access     ASUS     Flash HS-COMBO   3.95 PQ: 0 ANSI: 0                                                                     
[   10.201823] sd 4:0:0:0: [sdb] Attached SCSI removable disk                   
[   10.201904] sd 4:0:0:0: Attached scsi generic sg2 type 0                     
[   10.250941] sd 4:0:0:1: [sdc] Attached SCSI removable disk                   
[   10.250975] sd 4:0:0:1: Attached scsi generic sg3 type 0                     
[   11.507601] udevd version 124 started                                        
[   12.114115] input: PC Speaker as /devices/platform/pcspkr/input/input4       
[   12.186887] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5                                                                        
[   12.212035] ACPI: Power Button (FF) [PWRF]                                   
[   12.212099] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6                                                               
[   12.237270] ACPI: I/O resource nForce2_smbus [0x4c00-0x4c3f] conflicts with ACPI region SM00 [0x4c00-0x4c05]                                                 
[   12.237273] ACPI: Device needs an ACPI driver                                
[   12.237302] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00               
[   12.237315] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40               
[   12.240983] device-mapper: multipath: version 1.0.5 loaded                   
[   12.244036] ACPI: Power Button (CM) [PWRB]                                   
[   12.245265] ath_hal: module license 'Proprietary' taints kernel.             
[   12.246289] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)                                                                       
[   12.256624] wlan: 0.9.4                                                      
[   12.282624] Linux agpgart interface v0.103                                   
[   12.312744] ath_pci: 0.9.4                                                   
[   12.313156] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17                
[   12.313165] ath_pci 0000:01:0e.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17                                                                   
[   13.363253] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16                
[   13.363264] nvidia 0000:00:05.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16                                                                    
[   13.363269] nvidia 0000:00:05.0: setting latency timer to 64                 
[   13.369320] ath_rate_sample: 1.2 (0.9.4)                                     
[   13.369743] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps                     
[   13.369747] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps                                               
[   13.369754] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps                                                                             
[   13.369759] wifi0: H/W encryption support: WEP AES AES_CCM TKIP              
[   13.369762] wifi0: mac 7.9 phy 4.5 radio 5.6                                 
[   13.369765] wifi0: Use hw queue 1 for WME_AC_BE traffic                      
[   13.369766] wifi0: Use hw queue 0 for WME_AC_BK traffic                      
[   13.369768] wifi0: Use hw queue 2 for WME_AC_VI traffic                      
[   13.369770] wifi0: Use hw queue 3 for WME_AC_VO traffic                      
[   13.369771] wifi0: Use hw queue 8 for CAB traffic                            
[   13.369772] wifi0: Use hw queue 9 for beacons                                
[   13.413592] parport_pc 00:08: reported by Plug and Play ACPI                 
[   13.413619] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]          
[   13.434676] wifi0: Atheros 5212: mem=0xfdde0000, irq=17                      
[   13.434734] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008                                                                
[   13.593171] snd_rawmidi: disagrees about version of symbol snd_info_register 
[   13.593175] snd_rawmidi: Unknown symbol snd_info_register                    
[   13.593239] snd_rawmidi: disagrees about version of symbol snd_seq_device_new
[   13.593241] snd_rawmidi: Unknown symbol snd_seq_device_new                   
[   13.593298] snd_rawmidi: disagrees about version of symbol snd_info_free_entry                                                                               
[   13.593300] snd_rawmidi: Unknown symbol snd_info_free_entry                  
[   13.593360] snd_rawmidi: disagrees about version of symbol snd_unregister_oss_device                                                                         
[   13.593362] snd_rawmidi: Unknown symbol snd_unregister_oss_device            
[   13.593418] snd_rawmidi: disagrees about version of symbol snd_register_oss_device                                                                           
[   13.593419] snd_rawmidi: Unknown symbol snd_register_oss_device              
[   13.593474] snd_rawmidi: disagrees about version of symbol snd_ctl_register_ioctl                                                                            
[   13.593475] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl               
[   13.593523] snd_rawmidi: disagrees about version of symbol snd_card_file_add 
[   13.593525] snd_rawmidi: Unknown symbol snd_card_file_add                    
[   13.593776] snd_rawmidi: disagrees about version of symbol snd_unregister_device                                                                             
[   13.593778] snd_rawmidi: Unknown symbol snd_unregister_device                
[   13.593838] snd_rawmidi: disagrees about version of symbol snd_device_new    
[   13.593840] snd_rawmidi: Unknown symbol snd_device_new                       
[   13.593890] snd_rawmidi: disagrees about version of symbol snd_ctl_unregister_ioctl                                                                          
[   13.593892] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl             
[   13.594071] snd_rawmidi: disagrees about version of symbol snd_info_create_card_entry                                                                        
[   13.594073] snd_rawmidi: Unknown symbol snd_info_create_card_entry           
[   13.594127] snd_rawmidi: disagrees about version of symbol snd_card_file_remove                                                                              
[   13.594128] snd_rawmidi: Unknown symbol snd_card_file_remove                 
[   13.594179] snd_rawmidi: disagrees about version of symbol snd_register_device_for_dev                                                                       
[   13.594181] snd_rawmidi: Unknown symbol snd_register_device_for_dev          
[   13.594240] snd_rawmidi: disagrees about version of symbol snd_device_register                                                                               
[   13.594242] snd_rawmidi: Unknown symbol snd_device_register                  
[   13.613282] snd_seq_midi: Unknown symbol snd_rawmidi_info_select             
[   13.613552] snd_seq_midi: Unknown symbol snd_rawmidi_output_params           
[   13.613704] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_read             
[   13.613752] snd_seq_midi: disagrees about version of symbol snd_seq_device_register_driver                                                                   
[   13.613754] snd_seq_midi: Unknown symbol snd_seq_device_register_driver      
[   13.613815] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_write            
[   13.613934] snd_seq_midi: Unknown symbol snd_rawmidi_drain_output            
[   13.614130] snd_seq_midi: Unknown symbol snd_rawmidi_input_params            
[   13.614251] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_open             
[   13.614297] snd_seq_midi: disagrees about version of symbol snd_seq_create_kernel_client                                                                     
[   13.614299] snd_seq_midi: Unknown symbol snd_seq_create_kernel_client        
[   13.614365] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_release          
[   13.922106] snd_hda_intel: Unknown symbol snd_ctl_add_slave                  
[   13.922202] snd_hda_intel: disagrees about version of symbol snd_ctl_add     
[   13.922203] snd_hda_intel: Unknown symbol snd_ctl_add                        
[   13.922286] snd_hda_intel: disagrees about version of symbol snd_pcm_new     
[   13.922288] snd_hda_intel: Unknown symbol snd_pcm_new                        
[   13.922352] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates                                                                          
[   13.922354] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates             
[   13.922409] snd_hda_intel: disagrees about version of symbol snd_card_register                                                                               
[   13.922410] snd_hda_intel: Unknown symbol snd_card_register                  
[   13.922460] snd_hda_intel: disagrees about version of symbol snd_card_free   
[   13.922462] snd_hda_intel: Unknown symbol snd_card_free                      
[   13.922511] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all                                                           
[   13.922513] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all                                                                              
[   13.922563] snd_hda_intel: disagrees about version of symbol snd_card_proc_new                                                                               
[   13.922565] snd_hda_intel: Unknown symbol snd_card_proc_new                  
[   13.922735] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id 
[   13.922737] snd_hda_intel: Unknown symbol snd_ctl_find_id                    
[   13.922785] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync
[   13.922786] snd_hda_intel: Unknown symbol snd_pcm_set_sync                   
[   13.922948] snd_hda_intel: disagrees about version of symbol snd_ctl_new1    
[   13.922950] snd_hda_intel: Unknown symbol snd_ctl_new1                       
[   13.923075] snd_hda_intel: disagrees about version of symbol snd_component_add                                                                               
[   13.923077] snd_hda_intel: Unknown symbol snd_component_add                  
[   13.923144] snd_hda_intel: Unknown symbol snd_ctl_make_virtual_master        
[   13.923223] snd_hda_intel: Unknown symbol snd_card_new                       
[   13.923329] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages                                                                        
[   13.923330] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages           
[   13.923380] snd_hda_intel: disagrees about version of symbol snd_ctl_boolean_mono_info                                                                       
[   13.923382] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info          
[   13.923449] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl                                                                               
[   13.923451] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl                  
[   13.923504] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages                                                                          
[   13.923505] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages             
[   13.923582] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops 
[   13.923584] snd_hda_intel: Unknown symbol snd_pcm_set_ops                    
[   13.923644] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list                                                                      
[   13.923646] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list         
[   13.923732] snd_hda_intel: disagrees about version of symbol snd_device_new  
[   13.923734] snd_hda_intel: Unknown symbol snd_device_new                     
[   13.923782] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page                                                                          
[   13.923783] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page             
[   13.923858] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all                                                                             
[   13.923860] snd_hda_intel: Unknown symbol snd_pcm_suspend_all                
[   13.923934] snd_hda_intel: disagrees about version of symbol snd_card_disconnect                                                                             
[   13.923936] snd_hda_intel: Unknown symbol snd_card_disconnect                
[   13.923983] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer                                                                   
[   13.923985] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer      
[   13.924121] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup                                                                            
[   13.924122] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup               
[   13.924252] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed                                                                          
[   13.924254] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed             
[   13.924300] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step                                                                      
[   13.924302] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step         
[   65.137220] lp0: using parport0 (interrupt-driven).                          
[   65.156198] snd_hda_intel: Unknown symbol snd_ctl_add_slave                  
[   65.156291] snd_hda_intel: disagrees about version of symbol snd_ctl_add     
[   65.156292] snd_hda_intel: Unknown symbol snd_ctl_add                        
[   65.156376] snd_hda_intel: disagrees about version of symbol snd_pcm_new     
[   65.156377] snd_hda_intel: Unknown symbol snd_pcm_new                        
[   65.156442] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates                                                                          
[   65.156444] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates             
[   65.156499] snd_hda_intel: disagrees about version of symbol snd_card_register                                                                               
[   65.156501] snd_hda_intel: Unknown symbol snd_card_register                  
[   65.156551] snd_hda_intel: disagrees about version of symbol snd_card_free   
[   65.156553] snd_hda_intel: Unknown symbol snd_card_free                      
[   65.156602] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all                                                           
[   65.156604] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all                                                                              
[   65.156654] snd_hda_intel: disagrees about version of symbol snd_card_proc_new                                                                               
[   65.156656] snd_hda_intel: Unknown symbol snd_card_proc_new                  
[   65.156828] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id 
[   65.156830] snd_hda_intel: Unknown symbol snd_ctl_find_id                    
[   65.156878] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync
[   65.156879] snd_hda_intel: Unknown symbol snd_pcm_set_sync                   
[   65.157005] snd_hda_intel: disagrees about version of symbol snd_ctl_new1    
[   65.157006] snd_hda_intel: Unknown symbol snd_ctl_new1                       
[   65.157132] snd_hda_intel: disagrees about version of symbol snd_component_add                                                                               
[   65.157133] snd_hda_intel: Unknown symbol snd_component_add                  
[   65.157200] snd_hda_intel: Unknown symbol snd_ctl_make_virtual_master        
[   65.157280] snd_hda_intel: Unknown symbol snd_card_new                       
[   65.157385] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages                                                                        
[   65.157387] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages           
[   65.157437] snd_hda_intel: disagrees about version of symbol snd_ctl_boolean_mono_info                                                                       
[   65.157439] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info          
[   65.157506] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl                                                                               
[   65.157508] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl                  
[   65.157561] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages                                                                          
[   65.157563] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages             
[   65.157641] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops 
[   65.157642] snd_hda_intel: Unknown symbol snd_pcm_set_ops                    
[   65.157703] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list                                                                      
[   65.157705] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list         
[   65.157792] snd_hda_intel: disagrees about version of symbol snd_device_new  
[   65.157793] snd_hda_intel: Unknown symbol snd_device_new                     
[   65.157842] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page                                                                          
[   65.157843] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page             
[   65.157918] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all                                                                             
[   65.157920] snd_hda_intel: Unknown symbol snd_pcm_suspend_all                
[   65.157995] snd_hda_intel: disagrees about version of symbol snd_card_disconnect                                                                             
[   65.157997] snd_hda_intel: Unknown symbol snd_card_disconnect                
[   65.158044] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer                                                                   
[   65.158046] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer      
[   65.158183] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup                                                                            
[   65.158184] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup               
[   65.158314] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed                                                                          
[   65.158316] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed             
[   65.158363] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step                                                                      
[   65.158365] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step         
[   65.192714] snd_ac97_codec: Unknown symbol snd_ctl_add_slave                 
[   65.192766] snd_ac97_codec: disagrees about version of symbol snd_info_register                                                                              
[   65.192768] snd_ac97_codec: Unknown symbol snd_info_register                 
[   65.192819] snd_ac97_codec: disagrees about version of symbol snd_ctl_add    
[   65.192820] snd_ac97_codec: Unknown symbol snd_ctl_add                       
[   65.192930] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry                                                                            
[   65.192931] snd_ac97_codec: Unknown symbol snd_info_free_entry               
[   65.193057] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[   65.193059] snd_ac97_codec: Unknown symbol snd_ctl_find_id                   
[   65.193109] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1   
[   65.193110] snd_ac97_codec: Unknown symbol snd_ctl_new1                      
[   65.193168] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id                                                                              
[   65.193169] snd_ac97_codec: Unknown symbol snd_ctl_remove_id                 
[   65.193236] snd_ac97_codec: disagrees about version of symbol snd_component_add                                                                              
[   65.193238] snd_ac97_codec: Unknown symbol snd_component_add                 
[   65.193302] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master       
[   65.193349] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add                                                                            
[   65.193351] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add               
[   65.193477] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info                                                                      
[   65.193479] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info         
[   65.193633] snd_ac97_codec: disagrees about version of symbol snd_device_new 
[   65.193635] snd_ac97_codec: Unknown symbol snd_device_new                    
[   65.193762] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry                                                                     
[   65.193764] snd_ac97_codec: Unknown symbol snd_info_create_card_entry        
[   65.326060] Adding 5695000k swap on /dev/sda5.  Priority:-1 extents:1 across:5695000k                                                                        
[   65.879415] EXT3 FS on sda1, internal journal                                
[   66.794504] type=1505 audit(1245170262.750:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4552                
[   66.927057] type=1505 audit(1245170262.882:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4557                       
[   66.927230] type=1505 audit(1245170262.882:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4557                                      
[   66.956992] type=1505 audit(1245170262.910:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4561                                     
[   66.984116] type=1505 audit(1245170262.941:6): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=4565                             
[   67.093408] ip_tables: (C) 2000-2006 Netfilter Core Team                     
[   67.785040] ACPI: WMI: Mapper loaded                                         
[   68.026807] powernow-k8: Found 1 AMD Processor model unknown processors (2 cpu cores) (version 2.20.00)                                                      
[   68.027282] powernow-k8:    0 : fid 0x16 (3000 MHz), vid 0x6                 
[   68.027286] powernow-k8:    1 : fid 0x14 (2800 MHz), vid 0x8                 
[   68.027287] powernow-k8:    2 : fid 0x12 (2600 MHz), vid 0xa                 
[   68.027289] powernow-k8:    3 : fid 0x10 (2400 MHz), vid 0xc                 
[   68.027291] powernow-k8:    4 : fid 0xe (2200 MHz), vid 0xe                  
[   68.027292] powernow-k8:    5 : fid 0xc (2000 MHz), vid 0x10                 
[   68.027294] powernow-k8:    6 : fid 0xa (1800 MHz), vid 0x10                 
[   68.027295] powernow-k8:    7 : fid 0x2 (1000 MHz), vid 0x12                 
[   68.879119] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)                                                                         
[   69.124862] NET: Registered protocol family 10                               
[   69.125497] lo: Disabled Privacy Extensions                                  
[   71.331155] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)         
[   71.331161] apm: disabled - APM is not SMP safe.                             
[   71.657315] ppdev: user-space parallel port driver                           
[   75.508881] NET: Registered protocol family 17                               
[   77.439248] eth0: no link during initialization.                             
[   77.439695] ADDRCONF(NETDEV_UP): eth0: link is not ready                     
[   77.576035] Clocksource tsc unstable (delta = -68776119 ns)                  
[   82.441875] Bluetooth: Core ver 2.13                                         
[   82.442090] NET: Registered protocol family 31                               
[   82.442098] Bluetooth: HCI device and connection manager initialized         
[   82.442130] Bluetooth: HCI socket layer initialized                          
[   82.475141] Bluetooth: L2CAP ver 2.11                                        
[   82.475153] Bluetooth: L2CAP socket layer initialized                        
[   82.543803] Bluetooth: RFCOMM socket layer initialized                       
[   82.543833] Bluetooth: RFCOMM TTY layer initialized                          
[   82.543838] Bluetooth: RFCOMM ver 1.10                                       
[   82.548808] Bluetooth: BNEP (Ethernet Emulation) ver 1.3                     
[   82.548819] Bluetooth: BNEP filters: protocol multicast                      
[   82.689560] Bridge firewalling registered                                    
[   82.737958] Bluetooth: SCO (Voice Link) ver 0.6                              
[   82.737970] Bluetooth: SCO socket layer initialized                          
[   98.016026] ath0: no IPv6 routers present                                    
[  196.556274] ppdev0: registered pardevice                                     
[  196.612269] ppdev0: unregistered pardevice                                   
[  197.811742] ppdev0: registered pardevice                                     
[  197.861062] ppdev0: unregistered pardevice                                   
[  198.655697] ppdev0: registered pardevice                                     
[  198.704345] ppdev0: unregistered pardevice                                   
[ 7324.605798] snd_hda_intel: Unknown symbol snd_ctl_add_slave                  
[ 7324.606108] snd_hda_intel: disagrees about version of symbol snd_ctl_add     
[ 7324.606114] snd_hda_intel: Unknown symbol snd_ctl_add                        
[ 7324.606378] snd_hda_intel: disagrees about version of symbol snd_pcm_new     
[ 7324.606382] snd_hda_intel: Unknown symbol snd_pcm_new                        
[ 7324.606591] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates                                                                          
[ 7324.606596] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates             
[ 7324.606776] snd_hda_intel: disagrees about version of symbol snd_card_register                                                                               
[ 7324.606781] snd_hda_intel: Unknown symbol snd_card_register                  
[ 7324.606946] snd_
















[IMG]http://mail.google.com/mail/images/cleardot.gif[/IMG] _New window_
[IMG]http://mail.google.com/mail/images/cleardot.gif[/IMG] _Print all_
[IMG]http://mail.google.com/mail/images/cleardot.gif[/IMG] _Expand all_
[IMG]http://mail.google.com/mail/images/cleardot.gif[/IMG] _Collapse all_
[IMG]http://mail.google.com/mail/images/cleardot.gif[/IMG] _Forward all_


Sponsored Links
[B][PCI Compliance Solution]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=B4FXrzuk3SsDTEc6Jsga1s-W3DtGLzXO19b6XCcCNtwHAh7YCEAEYASCGj4ACKAk4AFD-7YHo_v____8BYLvGmoPQCqABq8Dk_QOyAQ9tYWlsLmdvb2dsZS5jb226AQhnbWFpbC1jdsgBAdoBNmh0dHA6Ly9tYWlsLmdvb2dsZS5jb20vYnZzY3dwczM5c3BpdXJzcm1sYzZxaDY4M3lubWpjOIACAagDAegD4AXoA-AB6AOvAugDBegDHvUDAAAABA&num=1&sig=AGiWqtwKt_HICRKMreJlfpJkSrMdzQ3xFw&adurl=http://web.solidcore.com/pci-dss-compliance") 
[/B]QSA recommended PCI Auditing and compliance solution
[www.solidcore.com]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=B4FXrzuk3SsDTEc6Jsga1s-W3DtGLzXO19b6XCcCNtwHAh7YCEAEYASCGj4ACKAk4AFD-7YHo_v____8BYLvGmoPQCqABq8Dk_QOyAQ9tYWlsLmdvb2dsZS5jb226AQhnbWFpbC1jdsgBAdoBNmh0dHA6Ly9tYWlsLmdvb2dsZS5jb20vYnZzY3dwczM5c3BpdXJzcm1sYzZxaDY4M3lubWpjOIACAagDAegD4AXoA-AB6AOvAugDBegDHvUDAAAABA&num=1&sig=AGiWqtwKt_HICRKMreJlfpJkSrMdzQ3xFw&adurl=http://web.solidcore.com/pci-dss-compliance") 


[B][Accelerate C in FPGAs]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BInZVzuk3SsDTEc6Jsga1s-W3DqLv-JgBptLcsgTAjbcB0PhaEAIYAiCGj4ACKAk4AFCinKDU_v____8BYLvGmoPQCrIBD21haWwuZ29vZ2xlLmNvbboBCGdtYWlsLWN2yAEB2gE2aHR0cDovL21haWwuZ29vZ2xlLmNvbS9idnNjd3BzMzlzcGl1cnNybWxjNnFoNjgzeW5tamM4gAIBqAMB6APgBegD4AHoA68C6AMF6AMe9QMAAAAE&num=2&sig=AGiWqtyWhzYwNUPYc7a6quIakgNnJyJM0A&adurl=http://www.ImpulseC.com/xilinx%3F_kk%3Dxilinx%2520ml507%2520linux%26_kt%3D04f95cbf-e817-4e3d-9b8f-b16fdacf376a") 
[/B]Generate hardware from C code Ask about ready-to-run examples
[www.ImpulseC.com]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BInZVzuk3SsDTEc6Jsga1s-W3DqLv-JgBptLcsgTAjbcB0PhaEAIYAiCGj4ACKAk4AFCinKDU_v____8BYLvGmoPQCrIBD21haWwuZ29vZ2xlLmNvbboBCGdtYWlsLWN2yAEB2gE2aHR0cDovL21haWwuZ29vZ2xlLmNvbS9idnNjd3BzMzlzcGl1cnNybWxjNnFoNjgzeW5tamM4gAIBqAMB6APgBegD4AHoA68C6AMF6AMe9QMAAAAE&num=2&sig=AGiWqtyWhzYwNUPYc7a6quIakgNnJyJM0A&adurl=http://www.ImpulseC.com/xilinx%3F_kk%3Dxilinx%2520ml507%2520linux%26_kt%3D04f95cbf-e817-4e3d-9b8f-b16fdacf376a") 


[B][Voice Recording]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BnVaxzuk3SsDTEc6Jsga1s-W3DoHXjKYBjYrK0g7AjbcB4M0vEAMYAyCGj4ACKAk4AFCMq4b5_v____8BYLvGmoPQCrIBD21haWwuZ29vZ2xlLmNvbboBCGdtYWlsLWN2yAEB2gE2aHR0cDovL21haWwuZ29vZ2xlLmNvbS9idnNjd3BzMzlzcGl1cnNybWxjNnFoNjgzeW5tamM4gAIBqQJsqkhvOjW3PqgDAegD4AXoA-AB6AOvAugDBegDHvUDAAAABA&num=3&sig=AGiWqtzPFz3s3YBswNvENVz_qxzUGS9sfw&adurl=http://www.optilogix.co.uk/home_.htm") 
[/B]OEM hardware technology for the voice recording industry.
[www.optilogix.co.uk]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BnVaxzuk3SsDTEc6Jsga1s-W3DoHXjKYBjYrK0g7AjbcB4M0vEAMYAyCGj4ACKAk4AFCMq4b5_v____8BYLvGmoPQCrIBD21haWwuZ29vZ2xlLmNvbboBCGdtYWlsLWN2yAEB2gE2aHR0cDovL21haWwuZ29vZ2xlLmNvbS9idnNjd3BzMzlzcGl1cnNybWxjNnFoNjgzeW5tamM4gAIBqQJsqkhvOjW3PqgDAegD4AXoA-AB6AOvAugDBegDHvUDAAAABA&num=3&sig=AGiWqtzPFz3s3YBswNvENVz_qxzUGS9sfw&adurl=http://www.optilogix.co.uk/home_.htm") 


[B][PCI Compliance made easy]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BlPQGzuk3SsDTEc6Jsga1s-W3DtXLiXCP7K7_DsCNtwGg6Y4BEAQYBCCGj4ACKAk4AFDL2_jK-v____8BYLvGmoPQCqABvZ6Q-QOyAQ9tYWlsLmdvb2dsZS5jb226AQhnbWFpbC1jdsgBAdoBNmh0dHA6Ly9tYWlsLmdvb2dsZS5jb20vYnZzY3dwczM5c3BpdXJzcm1sYzZxaDY4M3lubWpjOIACAcgC7-PhB6gDAegD4AXoA-AB6AOvAugDBegDHvUDAAAABA&num=4&sig=AGiWqtx9Z4EvJusBjAPLcZOaD-G5seUt-Q&adurl=http://www.splunk.com/view/pci/SP-CAAACPS%3Fac%3Dga0108_pci_pcicompliance") 
[/B]40 reports, 85 saved searches Satisfy your PCI requirements today
[www.splunk.com/PCICompliance]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BlPQGzuk3SsDTEc6Jsga1s-W3DtXLiXCP7K7_DsCNtwGg6Y4BEAQYBCCGj4ACKAk4AFDL2_jK-v____8BYLvGmoPQCqABvZ6Q-QOyAQ9tYWlsLmdvb2dsZS5jb226AQhnbWFpbC1jdsgBAdoBNmh0dHA6Ly9tYWlsLmdvb2dsZS5jb20vYnZzY3dwczM5c3BpdXJzcm1sYzZxaDY4M3lubWpjOIACAcgC7-PhB6gDAegD4AXoA-AB6AOvAugDBegDHvUDAAAABA&num=4&sig=AGiWqtx9Z4EvJusBjAPLcZOaD-G5seUt-Q&adurl=http://www.splunk.com/view/pci/SP-CAAACPS%3Fac%3Dga0108_pci_pcicompliance") 


[B][Full Linux Laptop Support]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BZCQtzuk3SsDTEc6Jsga1s-W3DsSxgSGcwrf8AcCNtwGg7w8QBRgFIIaPgAIoCTgAUL_C3acBYLvGmoPQCrIBD21haWwuZ29vZ2xlLmNvbboBCGdtYWlsLWN2yAEB2gE2aHR0cDovL21haWwuZ29vZ2xlLmNvbS9idnNjd3BzMzlzcGl1cnNybWxjNnFoNjgzeW5tamM4qAMB6APgBegD4AHoA68C6AMF6AMe9QMAAAAE&num=5&sig=AGiWqtxNEPfxpdb-BUz54xLpXGXlixwgNg&adurl=http://www.EmperorLinux.com/") 
[/B]We support: Wireless, EVDO, USB, Firewire, ACPI hibernate, BlueTooth
[www.EmperorLinux.com]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BZCQtzuk3SsDTEc6Jsga1s-W3DsSxgSGcwrf8AcCNtwGg7w8QBRgFIIaPgAIoCTgAUL_C3acBYLvGmoPQCrIBD21haWwuZ29vZ2xlLmNvbboBCGdtYWlsLWN2yAEB2gE2aHR0cDovL21haWwuZ29vZ2xlLmNvbS9idnNjd3BzMzlzcGl1cnNybWxjNnFoNjgzeW5tamM4qAMB6APgBegD4AHoA68C6AMF6AMe9QMAAAAE&num=5&sig=AGiWqtxNEPfxpdb-BUz54xLpXGXlixwgNg&adurl=http://www.EmperorLinux.com/") 


[B][Programmable FPGA boards]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BZGtKzuk3SsDTEc6Jsga1s-W3Dqy-2FKe3MOgA8CNtwHA3h8QBhgGIIaPgAIoCTgAUJbjmtwCYLvGmoPQCqABtICN_wOyAQ9tYWlsLmdvb2dsZS5jb226AQhnbWFpbC1jdsgBAdoBNmh0dHA6Ly9tYWlsLmdvb2dsZS5jb20vYnZzY3dwczM5c3BpdXJzcm1sYzZxaDY4M3lubWpjOIACAakCjfR0PtRnuz6oAwHoA-AF6APgAegDrwLoAwXoAx71AwAAAAQ&num=6&sig=AGiWqtwP-0EQ2cRYIPYSjRbwjKx3LtOOZQ&adurl=http://www.hunt-rtg.com/readytogo.htm%3Fcrtag%3Dcr") 
[/B]Low cost USB connected/standalone. Cables, IP, tools, PSU included.
[www.Hunt-Rtg.com]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BZGtKzuk3SsDTEc6Jsga1s-W3Dqy-2FKe3MOgA8CNtwHA3h8QBhgGIIaPgAIoCTgAUJbjmtwCYLvGmoPQCqABtICN_wOyAQ9tYWlsLmdvb2dsZS5jb226AQhnbWFpbC1jdsgBAdoBNmh0dHA6Ly9tYWlsLmdvb2dsZS5jb20vYnZzY3dwczM5c3BpdXJzcm1sYzZxaDY4M3lubWpjOIACAakCjfR0PtRnuz6oAwHoA-AF6APgAegDrwLoAwXoAx71AwAAAAQ&num=6&sig=AGiWqtwP-0EQ2cRYIPYSjRbwjKx3LtOOZQ&adurl=http://www.hunt-rtg.com/readytogo.htm%3Fcrtag%3Dcr") 


[B][UK - IT Salary Report]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BoUQGzuk3SsDTEc6Jsga1s-W3Dtqn62Lk-Ye5C8CNtwGg4BQQBxgHIIaPgAIoCTgAUNDh3oADYLvGmoPQCqAB4oi7_AOyAQ9tYWlsLmdvb2dsZS5jb226AQhnbWFpbC1jdsgBAdoBNmh0dHA6Ly9tYWlsLmdvb2dsZS5jb20vYnZzY3dwczM5c3BpdXJzcm1sYzZxaDY4M3lubWpjOIACAakC0cYT-ykBpz7IAsqT8geoAwHoA-AF6APgAegDrwLoAwXoAx71AwAAAAQ&num=7&sig=AGiWqtwkMg2T0Mhm7YOJW7Bs2vyI1uvP1Q&adurl=http://www.activetechpros.com/landing.htm%3Fsrc%3Dgoogle_sem_uk_devprogtoolC") 
[/B]IT pros earn an annual average of £45,275. Benchmark your pay here.
[www.activeTechPros.com]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BoUQGzuk3SsDTEc6Jsga1s-W3Dtqn62Lk-Ye5C8CNtwGg4BQQBxgHIIaPgAIoCTgAUNDh3oADYLvGmoPQCqAB4oi7_AOyAQ9tYWlsLmdvb2dsZS5jb226AQhnbWFpbC1jdsgBAdoBNmh0dHA6Ly9tYWlsLmdvb2dsZS5jb20vYnZzY3dwczM5c3BpdXJzcm1sYzZxaDY4M3lubWpjOIACAakC0cYT-ykBpz7IAsqT8geoAwHoA-AF6APgAegDrwLoAwXoAx71AwAAAAQ&num=7&sig=AGiWqtwkMg2T0Mhm7YOJW7Bs2vyI1uvP1Q&adurl=http://www.activetechpros.com/landing.htm%3Fsrc%3Dgoogle_sem_uk_devprogtoolC") 


[B][Free PCI Compliance Guide]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BNXwyzuk3SsDTEc6Jsga1s-W3Dv74pnHO3MnbC8CNtwHA_WgQCBgIIIaPgAIoCTgAUMGipKf4_____wFgu8aag9AKoAGG2Y76A7IBD21haWwuZ29vZ2xlLmNvbboBCGdtYWlsLWN2yAEB2gE2aHR0cDovL21haWwuZ29vZ2xlLmNvbS9idnNjd3BzMzlzcGl1cnNybWxjNnFoNjgzeW5tamM4gAIByALO1sQDqAMB6APgBegD4AHoA68C6AMF6AMe9QMAAAAE&num=8&sig=AGiWqtyRW-WRtcb00bFkmFw5G0yOjRmdew&adurl=http://www.qualys.com/forms/google/pci_wp/%3Flsid%3D6877%26leadsource%3D80884%26kw%3Dpci") 
[/B]Winning the PCI Compliance Battle. Free Guide for Online Merchants.
[PCI.qualys.com]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BNXwyzuk3SsDTEc6Jsga1s-W3Dv74pnHO3MnbC8CNtwHA_WgQCBgIIIaPgAIoCTgAUMGipKf4_____wFgu8aag9AKoAGG2Y76A7IBD21haWwuZ29vZ2xlLmNvbboBCGdtYWlsLWN2yAEB2gE2aHR0cDovL21haWwuZ29vZ2xlLmNvbS9idnNjd3BzMzlzcGl1cnNybWxjNnFoNjgzeW5tamM4gAIByALO1sQDqAMB6APgBegD4AHoA68C6AMF6AMe9QMAAAAE&num=8&sig=AGiWqtyRW-WRtcb00bFkmFw5G0yOjRmdew&adurl=http://www.qualys.com/forms/google/pci_wp/%3Flsid%3D6877%26leadsource%3D80884%26kw%3Dpci") 


[B][Vulnerability Scanner]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BPq07zuk3SsDTEc6Jsga1s-W3DtDWuGm4keiTAcCNtwHwjtsBEAkYCSCGj4ACKAk4AFDXvrbUB2C7xpqD0AqyAQ9tYWlsLmdvb2dsZS5jb226AQhnbWFpbC1jdsgBAdoBNmh0dHA6Ly9tYWlsLmdvb2dsZS5jb20vYnZzY3dwczM5c3BpdXJzcm1sYzZxaDY4M3lubWpjOIACAagDAegD4AXoA-AB6AOvAugDBegDHvUDAAAABA&num=9&sig=AGiWqtwSBSr3c4zaNBaIH5GxAtGRp02sfA&adurl=http://www.saintcorporation.com/resources/compliance/pci.html") 
[/B]How vulnerable are your networks? Find out with the SAINT Scanner.
[www.saintcorporation.com]("http://pagead2.googlesyndication.com/aclk?sa=l&ai=BPq07zuk3SsDTEc6Jsga1s-W3DtDWuGm4keiTAcCNtwHwjtsBEAkYCSCGj4ACKAk4AFDXvrbUB2C7xpqD0AqyAQ9tYWlsLmdvb2dsZS5jb226AQhnbWFpbC1jdsgBAdoBNmh0dHA6Ly9tYWlsLmdvb2dsZS5jb20vYnZzY3dwczM5c3BpdXJzcm1sYzZxaDY4M3lubWpjOIACAagDAegD4AXoA-AB6AOvAugDBegDHvUDAAAABA&num=9&sig=AGiWqtwSBSr3c4zaNBaIH5GxAtGRp02sfA&adurl=http://www.saintcorporation.com/resources/compliance/pci.html") 



More about...
[ACPI Bios »]("http://mail.google.com/mail/?ui=2&ik=efd27748af&view=ap&t=r&rlk=ACPI%20Bios&rll=en")

[Bios Updates »]("http://mail.google.com/mail/?ui=2&ik=efd27748af&view=ap&t=r&rlk=Bios%20Updates&rll=en")

[Linux Kernel Howto »]("http://mail.google.com/mail/?ui=2&ik=efd27748af&view=ap&t=r&rlk=Linux%20Kernel%20Howto&rll=en")

[Free Driver Update »]("http://mail.google.com/mail/?ui=2&ik=efd27748af&view=ap&t=r&rlk=Free%20Driver%20Update&rll=en")






About these links

---

### Post by markbuntu on 2009-06-16
Since you did an upgrade-upgrade I would suggest that you remove and reinstall alsa so that it can autoconfig itself cleanly. There is probably some old stuff lying about causing your problems with the snd-hda-intel version mismatches.


(1) Remove the ALSA packages. From a terminal:
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

```
(2) Reinstall the same packages
```

sudo apt-get install linux-sound-base alsa-base alsa-utils

```
Packages gdm and ubuntu-desktop are also removed in this process if you are using Gnome. They need to be reinstalled:
```

sudo apt-get install gdm ubuntu-desktop

```
If you are using xubuntu this will also happen to you
```

sudo apt-get install gdm xubuntu-desktop

```
(3) Reboot.

After you reboot, go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If you still have problems go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by zoe-scutterbug on 2009-06-17
Much appreciation and Thanks Mark I tried to following the guide in ....[ubuntu] Interpid Sound Solutions & and [SOLVED] Multiple Sound Solution (ALSA w Pulseaudio) ..and other places too but sadly i am still failing


..................................................


Testing sound in sound prefs>>>>

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

........................

pressing the volume icon in the uper bar>>>>>>

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

........................

open volume control gives me >>>>>>>>>>

No volume control GStreamer plugins and/or devices found.

.............................

alsamixer/gnome mixer >>>>> blank

..............................

Adding a new user did not help :(

............................
zoe@OpenGEUbox:~$ cat /proc/asound/cards
--- no soundcards ---

....................
zoe@OpenGEUbox:~$ cat /proc/asound/modules
zoe@OpenGEUbox:~$

................
zoe@OpenGEUbox:~$ aplay -l
aplay: device_list:215: no soundcards found...
zoe@OpenGEUbox:~$

....................
zoe@OpenGEUbox:~$ arecord -l
arecord: device_list:215: no soundcards found...
zoe@OpenGEUbox:~$

..................
sudo killall pulseaudio

sudo alsa force-reload

pulseaudio -D

gives

zoe@OpenGEUbox:~$ sudo killall pulseaudio
zoe@OpenGEUbox:~$
zoe@OpenGEUbox:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zoebuggy/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zoe/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zoebuggy/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zoe/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-pcm-oss snd-pcm snd-page-alloc snd-mixer-oss snd-seq-oss snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-pcm-oss snd-pcm snd-page-alloc snd-mixer-oss snd-seq-oss snd-seq-midi-event snd-seq snd-timer snd-seq-device.
zoe@OpenGEUbox:~$
zoe@OpenGEUbox:~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
zoe@OpenGEUbox:~$

..............................

I am using a hda-intel onboard sound card via nvidia on an asus barebones pundit 1 but dont know how to find my sound chip

.....................

zoe@OpenGEUbox:~$ pulseaudio -vvv
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.                                                                
I: core-util.c: Successfully gained nice level -11.                          
W: ltdl-bind-now.c: Failed to find original dlopen loader.                   
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted  
I: main.c: This is PulseAudio 0.9.10                                         
I: main.c: Page size is 4096 bytes                                           
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
I: module-hal-detect.c: Loaded 0 modules.
I: module.c: Loaded "module-hal-detect" (index: #0; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #1; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #3; argument: "").
I: module-volume-restore.c: starting with empty ruleset.
I: module.c: Loaded "module-volume-restore" (index: #4; argument: "").
D: module-default-device-restore.c: No previous default sink setting, ignoring.
D: module-default-device-restore.c: No previous default source setting, ignoring.
I: module.c: Loaded "module-default-device-restore" (index: #5; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #6; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #8; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired


xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

zoe@OpenGEUbox:~$ sudo depmod
[sudo] password for zoe:
zoe@OpenGEUbox:~$ sudo modprobe snd-hda-intel
- Show quoted text -
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)
zoe@OpenGEUbox:~$
 

zoe@OpenGEUbox:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-14-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Fri Jun 5 10:14:59 UTC 2009 (Ubuntu 2.6.27-14.34-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000077ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000077ef0000 - 0000000077ef3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000077ef3000 - 0000000077f00000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000078000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x77ef0 max_arch_pfn = 0x100000
[    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000
[    0.000000] RAMDISK: 3770d000 - 37fef32c
[    0.000000] ACPI: RSDP 000F6D00, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 77EF3040, 0034 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 77EF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 77EF3180, 6E72 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 77EF0000, 0040
[    0.000000] ACPI: SSDT 77EFA100, 030E (r1 PTLTD  POWERNOW        1  LTP        1)
[    0.000000] ACPI: MCFG 77EFA480, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 77EFA040, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] 1022MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 38000000
[    0.000000]   low ram: 00000000 - 38000000
[    0.000000]   bootmap 00011000 - 00018000
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00005c59e0]    TEXT DATA BSS ==> [0000100000 - 00005c59e0]
[    0.000000]   #4 [003770d000 - 0037fef32c]          RAMDISK ==> [003770d000 - 0037fef32c]
[    0.000000]   #5 [00005c6000 - 00005c9000]    INIT_PG_TABLE ==> [00005c6000 - 00005c9000]
[    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]
[    0.000000] found SMP MP-table at [c00f5270] 000f5270
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00038000
[    0.000000]   HighMem  0x00038000 -> 0x00077ef0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00077ef0
[    0.000000] On node 0 totalpages: 491135
[    0.000000] free_area_init_node: node 0, pgdat c048d700, node_mem_map c1000240
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 223300 pages, LIFO batch:31
[    0.000000]   HighMem zone: 259570 pages, LIFO batch:31
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] If you got timer trouble try acpi_use_timer_override
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)
[    0.000000] PERCPU: Allocating 41628 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 486817
[    0.000000] Kernel command line: root=UUID=e2491bd4-3091-40b5-8e3b-0201950859ea ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 3013.822 MHz processor.

[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] Memory: 1931416k/1964992k available (2581k kernel code, 32208k reserved, 1163k data, 428k init, 1047488k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    0.004000]       .init : 0xc04af000 - 0xc051a000   ( 428 kB)
[    0.004000]       .data : 0xc038571a - 0xc04a8680   (1163 kB)
[    0.004000]       .text : 0xc0100000 - 0xc038571a   (2581 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6027.64 BogoMIPS (lpj=12055288)

[    0.004021] Security Framework initialized
[    0.004026] SELinux:  Disabled at boot.
[    0.004043] AppArmor: AppArmor initialized

[    0.004048] Mount-cache hash table entries: 512
[    0.004167] Initializing cgroup subsys ns
[    0.004170] Initializing cgroup subsys cpuacct
[    0.004172] Initializing cgroup subsys memory

[    0.004182] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004183] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.004185] CPU 0(2) -> Core 0
[    0.004188] using C1E aware idle routine
[    0.004196] Checking 'hlt' instruction... OK.

[    0.021132] ACPI: Core revision 20080609
[    0.022895] ACPI: Checking initramfs for custom DSDT
[    0.276348] ENABLING IO-APIC IRQs
[    0.276568] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1

[    0.284017] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    0.284017] ...trying to set up timer (IRQ0) through the 8259A ...
[    0.284017] ..... (found apic 0 pin 0) ...
[    0.292018] ....... failed.
[    0.292018] ...trying to set up timer as Virtual Wire IRQ...
[    0.292018] ..... failed.
[    0.292018] ...trying to set up timer as ExtINT IRQ...
[    0.335324] ..... works.
[    0.335325] CPU0: AMD Processor model unknown stepping 03

[    0.336021] Booting processor 1/1 ip 6000
[    0.004000] Initializing CPU#1
[    0.388024] Calibrating delay using timer specific routine.. 6028.18 BogoMIPS (lpj=12056368)
[    0.388024] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.388024] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.388024] CPU 1(2) -> Core 1
[    0.420216] CPU1: AMD Processor model unknown stepping 03
[    0.420236] Brought up 2 CPUs
[    0.420238] Total of 2 processors activated (12055.82 BogoMIPS).

[    0.420278] CPU0 attaching sched-domain:
[    0.420280]  domain 0: span 0-1 level CPU
[    0.420282]   groups: 0 1
[    0.420286] CPU1 attaching sched-domain:
[    0.420288]  domain 0: span 0-1 level CPU
[    0.420289]   groups: 1 0
[    0.420333] net_namespace: 840 bytes
[    0.420333] Booting paravirtualized kernel on bare hardware
[    0.420333] Time: 16:02:50  Date: 06/17/09

[    0.420333] NET: Registered protocol family 16
[    0.420333] EISA bus registered
[    0.420333] ACPI: bus type pci registered
[    0.420333] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 255
[    0.420333] PCI: MCFG area at f0000000 reserved in E820
[    0.420333] PCI: updated MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.420333] PCI: Using MMCONFIG for extended config space
[    0.420333] PCI: Using configuration type 1 for base access
[    0.420911] ACPI: EC: Look up EC in DSDT
[    0.430299] ACPI: Interpreter enabled
[    0.430302] ACPI: (supports S0 S1 S3 S4 S5)
[    0.430313] ACPI: Using IOAPIC for interrupt routing

[    0.436524] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.436524] PCI: 0000:00:05.0 reg 10 32bit mmio: [fb000000, fbffffff]
[    0.436524] PCI: 0000:00:05.0 reg 14 64bit mmio: [e0000000, efffffff]
[    0.436524] PCI: 0000:00:05.0 reg 1c 64bit mmio: [fc000000, fcffffff]
[    0.436524] PCI: 0000:00:05.0 reg 30 32bit mmio: [0, 1ffff]
[    0.436524] HPET not enabled in BIOS. You might try hpet=force boot option
[    0.436524] PCI: 0000:00:0a.1 reg 20 io port: [4c00, 4c3f]
[    0.436524] PCI: 0000:00:0a.1 reg 24 io port: [4c40, 4c7f]
[    0.436524] pci 0000:00:0a.1: PME# supported from D3hot D3cold
[    0.436524] pci 0000:00:0a.1: PME# disabled
[    0.436524] PCI: 0000:00:0b.0 reg 10 32bit mmio: [fe02f000, fe02ffff]
[    0.436534] pci 0000:00:0b.0: supports D1
[    0.436536] pci 0000:00:0b.0: supports D2
[    0.436537] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.436540] pci 0000:00:0b.0: PME# disabled
[    0.436558] PCI: 0000:00:0b.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]
[    0.436588] pci 0000:00:0b.1: supports D1
[    0.436589] pci 0000:00:0b.1: supports D2
[    0.436591] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.436593] pci 0000:00:0b.1: PME# disabled
[    0.436620] PCI: 0000:00:0d.0 reg 20 io port: [f400, f40f]
[    0.436654] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]
[    0.436658] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]
[    0.436661] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]
[    0.436665] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]
[    0.436668] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]
[    0.436672] PCI: 0000:00:0e.0 reg 24 32bit mmio: [fe02d000, fe02dfff]
[    0.440038] PCI: 0000:00:10.1 reg 10 32bit mmio: [fe028000, fe02bfff]

[    0.440072] pci 0000:00:10.1: PME# supported from D3hot D3cold
[    0.440076] pci 0000:00:10.1: PME# disabled
[    0.440098] PCI: 0000:00:14.0 reg 10 32bit mmio: [fe02c000, fe02cfff]
[    0.440102] PCI: 0000:00:14.0 reg 14 io port: [dc00, dc07]
[    0.440123] pci 0000:00:14.0: supports D1
[    0.440124] pci 0000:00:14.0: supports D2
[    0.440126] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.440129] pci 0000:00:14.0: PME# disabled
[    0.440200] PCI: 0000:01:03.0 reg 10 32bit mmio: [fddff000, fddff7ff]
[    0.440205] PCI: 0000:01:03.0 reg 14 io port: [cc00, cc7f]
[    0.440239] pci 0000:01:03.0: supports D2

[    0.440240] pci 0000:01:03.0: PME# supported from D2 D3hot D3cold
[    0.440243] pci 0000:01:03.0: PME# disabled
[    0.440272] PCI: 0000:01:0e.0 reg 10 32bit mmio: [fdde0000, fddeffff]
[    0.440324] pci 0000:00:10.0: transparent bridge
[    0.440327] PCI: bridge 0000:00:10.0 io port: [c000, cfff]

[    0.440329] PCI: bridge 0000:00:10.0 32bit mmio: [fdd00000, fddfffff]
[    0.440332] PCI: bridge 0000:00:10.0 32bit mmio pref: [fde00000, fdefffff]

[    0.440336] bus 00 -> node 0
[    0.440342] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]

[    0.440580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.517942] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.517942] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)
[    0.517942] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.517942] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.517942] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.517942] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.517942] ACPI: PCI Interrupt Link [LNK7] (IRQs *5 7 9 10 11 14 15)
[    0.517942] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.517942] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.517942] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.520034] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)
[    0.520212] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.520392] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)
[    0.520570] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.520748] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.520927] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.521106] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.521284] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.521464] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)
[    0.521642] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.
[    0.521858] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[    0.522069] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.522279] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[    0.522488] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[    0.522698] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.
[    0.522908] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.
[    0.523118] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0
[    0.523328] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.
[    0.523538] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
[    0.523749] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.523962] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.524184] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
[    0.524396] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
[    0.524607] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0
[    0.524818] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.525030] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
[    0.525242] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
[    0.525453] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
[    0.525664] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.525876] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.526087] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
[    0.526147] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.526147] pnp: PnP ACPI init
[    0.526147] ACPI: bus type pnp registered
[    0.529462] pnp: PnP ACPI: found 11 devices
[    0.529462] ACPI: ACPI bus type pnp unregistered
[    0.529462] PnPBIOS: Disabled by ACPI PNP
[    0.529462] PCI: Using ACPI for IRQ routing

[    0.536038] NET: Registered protocol family 8
[    0.536039] NET: Registered protocol family 20
[    0.536059] NetLabel: Initializing
[    0.536061] NetLabel:  domain hash size = 128

[    0.536062] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.536071] NetLabel:  unlabeled traffic allowed by default
[    0.536449] tracer: 772 pages allocated for 65536 entries of 48 bytes
[    0.536451]    actual entries 65620
[    0.536549] AppArmor: AppArmor Filesystem Enabled
[    0.536574] ACPI: RTC can wake from S4
[    0.544044] system 00:01: ioport range 0x4000-0x407f has been reserved

[    0.544047] system 00:01: ioport range 0x4080-0x40ff has been reserved
[    0.544049] system 00:01: ioport range 0x4400-0x447f has been reserved
[    0.544051] system 00:01: ioport range 0x4480-0x44ff has been reserved
[    0.544053] system 00:01: ioport range 0x4800-0x487f has been reserved
[    0.544055] system 00:01: ioport range 0x4880-0x48ff has been reserved
[    0.544057] system 00:01: ioport range 0x2000-0x207f has been reserved
[    0.544059] system 00:01: ioport range 0x2080-0x20ff has been reserved
[    0.544061] system 00:01: iomem range 0x78000000-0x7fffffff could not be reserved
[    0.544065] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[    0.544067] system 00:02: ioport range 0x800-0x87f has been reserved
[    0.544073] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved
[    0.544077] system 00:0a: iomem range 0xd5800-0xd7fff has been reserved
[    0.544079] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved
[    0.544081] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved
[    0.544083] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved
[    0.544085] system 00:0a: iomem range 0x77ef0000-0x77efffff could not be reserved
[    0.544087] system 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved

[    0.544090] system 00:0a: iomem range 0x0-0x9ffff could not be reserved
[    0.544092] system 00:0a: iomem range 0x100000-0x77eeffff could not be reserved
[    0.544094] system 00:0a: iomem range 0x77f00000-0x7fefffff could not be reserved
[    0.544096] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.544098] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved
[    0.544100] system 00:0a: iomem range 0xfefff000-0xfeffffff could not be reserved

[    0.544103] system 00:0a: iomem range 0xfff80000-0xfff80fff could not be reserved
[    0.544105] system 00:0a: iomem range 0xfff90000-0xfffbffff could not be reserved
[    0.544107] system 00:0a: iomem range 0xfffed000-0xfffeffff could not be reserved
[    0.579025] pci 0000:00:10.0: PCI bridge, secondary bus 0000:01
[    0.579028] pci 0000:00:10.0:   IO window: 0xc000-0xcfff
[    0.579031] pci 0000:00:10.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.579034] pci 0000:00:10.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.579042] pci 0000:00:10.0: setting latency timer to 64
[    0.579045] bus: 00 index 0 io port: [0, ffff]
[    0.579047] bus: 00 index 1 mmio: [0, ffffffff]
[    0.579048] bus: 01 index 0 io port: [c000, cfff]
[    0.579050] bus: 01 index 1 mmio: [fdd00000, fddfffff]
[    0.579051] bus: 01 index 2 mmio: [fde00000, fdefffff]
[    0.579053] bus: 01 index 3 io port: [0, ffff]
[    0.579054] bus: 01 index 4 mmio: [0, ffffffff]
[    0.579062] NET: Registered protocol family 2

[    0.580047] Switched to high resolution mode on CPU 0
[    0.580257] Switched to high resolution mode on CPU 1
[    0.592050] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)

[    0.592251] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.592784] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.593030] TCP: Hash tables configured (established 131072 bind 65536)
[    0.593032] TCP reno registered

[    0.600075] NET: Registered protocol family 1
[    0.600165] checking if image is initramfs... it is
[    1.115885] Freeing initrd memory: 9096k freed
[    1.116786] audit: initializing netlink socket (disabled)
[    1.116801] type=2000 audit(1245254570.116:1): initialized
[    1.120834] highmem bounce pool size: 64 pages
[    1.120838] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.123183] VFS: Disk quotas dquot_6.5.1
[    1.123276] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.123360] msgmni has been set to 1745
[    1.123465] io scheduler noop registered
[    1.123467] io scheduler anticipatory registered
[    1.123468] io scheduler deadline registered
[    1.123476] io scheduler cfq registered (default)
[    1.123488] pci 0000:00:00.0: Enabling HT MSI Mapping
[    1.123515] pci 0000:00:05.0: Boot video device
[    1.123534] pci 0000:00:09.0: Enabling HT MSI Mapping
[    1.136220] pci 0000:00:0e.0: Enabling HT MSI Mapping
[    1.136228] pci 0000:00:10.0: Enabling HT MSI Mapping
[    1.136238] pci 0000:00:10.1: Enabling HT MSI Mapping
[    1.136561] isapnp: Scanning for PnP cards...
[    1.489362] isapnp: No Plug & Play device found
[    1.519322] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.519441] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.519919] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.521587] brd: module loaded
[    1.521646] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.521801] PNP: No PS/2 controller found. Probing ports directly.
[    1.524609] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.524613] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.529117] mice: PS/2 mouse device common for all mice
[    1.529224] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.529250] rtc0: alarms up to one year, y3k
[    1.529364] EISA: Probing bus 0 at eisa.0
[    1.529371] Cannot allocate resource for EISA slot 2
[    1.529374] Cannot allocate resource for EISA slot 4
[    1.529385] EISA: Detected 0 cards.
[    1.529387] cpuidle: using governor ladder
[    1.529389] cpuidle: using governor menu
[    1.529817] TCP cubic registered
[    1.529837] Using IPI No-Shortcut mode
[    1.530008] registered taskstats version 1
[    1.530103]   Magic number: 13:933:34
[    1.530258] rtc_cmos 00:04: setting system clock to 2009-06-17 16:02:51 UTC (1245254571)
[    1.530260] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.530262] EDD information not available.
[    1.530516] Freeing unused kernel memory: 428k freed
[    1.530561] Write protecting the kernel text: 2584k
[    1.530590] Write protecting the kernel read-only data: 940k
[    1.576051] compcache: Compressed swap size set to: 485468 KB
[    1.576629] TLSF: pool: f881e000, init_size=16384, max_size=0, grow_size=16384
[    1.721151] fuse init (API version 7.9)
[    1.737163] fan PNP0C0B:00: registered as cooling_device0
[    1.737168] ACPI: Fan [FAN] (on)
[    1.745197] processor ACPI0007:00: registered as cooling_device1
[    1.745244] processor ACPI0007:01: registered as cooling_device2
[    1.747926] thermal LNXTHERM:01: registered as thermal_zone0
[    1.749835] ACPI: Thermal Zone [THRM] (40 C)
[    1.825807] device-mapper: uevent: version 1.0.3
[    1.826007] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    2.266808] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    2.267193] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[    2.267203] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 23 (level, low) -> IRQ 23
[    2.267207] forcedeth 0000:00:14.0: setting latency timer to 64
[    2.267232] nv_probe: set workaround bit for reversed mac addr
[    2.268270] usbcore: registered new interface driver usbfs
[    2.268288] usbcore: registered new interface driver hub
[    2.272350] usbcore: registered new device driver usb
[    2.273640] No dock devices found.
[    2.283632] SCSI subsystem initialized
[    2.311135] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.312713] libata version 3.00 loaded.
[    2.312772] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    2.314665] Adding 485464k swap on /dev/ramzswap0.  Priority:100 extents:1 across:485464k
[    2.784478] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x5043 @ 11, addr 00:1a:92:55:29:b1
[    2.784482] forcedeth 0000:00:14.0: highdma pwrctl timirq gbit lnktim desc-v3
[    2.785040] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[    2.785053] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 22 (level, low) -> IRQ 22
[    2.785066] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    2.785069] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    2.785118] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 1
[    2.785141] ohci_hcd 0000:00:0b.0: irq 22, io mem 0xfe02f000
[    2.842130] usb usb1: configuration #1 chosen from 1 choice
[    2.842154] hub 1-0:1.0: USB hub found
[    2.842163] hub 1-0:1.0: 8 ports detected
[    3.048439] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 21
[    3.048446] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 21 (level, low) -> IRQ 21
[    3.048452] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    3.048454] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    3.048470] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 2
[    3.048491] ehci_hcd 0000:00:0b.1: debug port 1
[    3.048495] ehci_hcd 0000:00:0b.1: cache line size of 64 is not supported
[    3.048505] ehci_hcd 0000:00:0b.1: irq 21, io mem 0xfe02e000
[    3.060024] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.060095] usb usb2: configuration #1 chosen from 1 choice
[    3.060114] hub 2-0:1.0: USB hub found
[    3.060119] hub 2-0:1.0: 8 ports detected
[    3.268113] pata_amd 0000:00:0d.0: version 0.3.10
[    3.268145] pata_amd 0000:00:0d.0: setting latency timer to 64
[    3.268334] scsi0 : pata_amd
[    3.268528] scsi1 : pata_amd
[    3.269107] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    3.269109] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    3.432359] ata1.00: ATAPI: Optiarc DVD RW AD-5170A, 1.13, max UDMA/66
[    3.432371] ata1: nv_mode_filter: 0x1f39f&0x1f01f->0x1f01f, BIOS=0x1f000 (0xc5000000) ACPI=0x1f01f (30:600:0x13)
[    3.448269] ata1.00: configured for UDMA/66
[    3.448316] ata2: port disabled. ignoring.
[    3.449260] scsi 0:0:0:0: CD-ROM            Optiarc  DVD RW AD-5170A  1.13 PQ: 0 ANSI: 5
[    3.449676] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    3.449684] ohci1394 0000:01:03.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    3.502387] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fddff000-fddff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    3.512813] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 20
[    3.512824] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    3.512852] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    3.512862] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    3.516103] sata_nv 0000:00:0e.0: version 3.5
[    3.516108] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 20 (level, low) -> IRQ 20
[    3.516111] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    3.516134] sata_nv 0000:00:0e.0: setting latency timer to 64
[    3.526628] scsi2 : sata_nv
[    3.526757] scsi3 : sata_nv
[    3.526920] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 20
[    3.526923] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 20
[    3.527148] scsi 0:0:0:0: Attached scsi generic sg0 type 5
[    3.536516] Driver 'sr' needs updating - please use bus_type methods
[    3.539089] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    3.539092] Uniform CD-ROM driver Revision: 3.20
[    3.539156] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.712023] usb 2-7: new high speed USB device using ehci_hcd and address 4
[    3.914997] usb 2-7: configuration #1 chosen from 1 choice
[    4.221019] usb 1-3: new full speed USB device using ohci_hcd and address 2
[    4.404051] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.412299] ata3.00: ATA-7: ST3250310AS, 3.AAC, max UDMA/133
[    4.412302] ata3.00: 488397168 sectors, multi 1: LBA48 NCQ (depth 31/32)
[    4.429297] ata3.00: configured for UDMA/133
[    4.442126] usb 1-3: configuration #1 chosen from 1 choice
[    4.748027] usb 1-4: new low speed USB device using ohci_hcd and address 3
[    4.776098] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001234dde]
[    4.957125] usb 1-4: configuration #1 chosen from 1 choice
[    4.967394] usbcore: registered new interface driver libusual
[    4.967603] usbcore: registered new interface driver hiddev
[    4.973031] Initializing USB Mass Storage driver...
[    4.973099] scsi4 : SCSI emulation for USB Mass Storage devices
[    4.973158] usb-storage: device found at 4
[    4.973159] usb-storage: waiting for device to settle before scanning
[    4.979818] input: Microsoft SideWinder? Mouse as /devices/pci0000:00/0000:00:0b.0/usb1/1-3/1-3:1.0/input/input1
[    4.985106] input,hidraw0: USB HID v1.11 Mouse [Microsoft SideWinder? Mouse] on usb-0000:00:0b.0-3
[    4.994237] input: HID 7350:099a as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input2
[    4.994375] input,hidraw1: USB HID v1.10 Keyboard [HID 7350:099a] on usb-0000:00:0b.0-4
[    5.010160] input: HID 7350:099a as /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.1/input/input3
[    5.010333] input,hiddev96,hidraw2: USB HID v1.10 Device [HID 7350:099a] on usb-0000:00:0b.0-4
[    5.010363] usbcore: registered new interface driver usbhid
[    5.010366] usbhid: v2.6:USB HID core driver
[    5.010373] usbcore: registered new interface driver usb-storage
[    5.010376] USB Mass Storage support registered.
[    5.162434] ata4: SATA link down (SStatus 0 SControl 300)
[    5.162525] scsi 2:0:0:0: Direct-Access     ATA      ST3250310AS      3.AA PQ: 0 ANSI: 5
[    5.162662] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[    5.177197] Driver 'sd' needs updating - please use bus_type methods
[    5.177276] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.177287] sd 2:0:0:0: [sda] Write Protect is off
[    5.177289] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.177305] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.177350] sd 2:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    5.177358] sd 2:0:0:0: [sda] Write Protect is off
[    5.177360] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.177374] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.177377]  sda: sda1 sda2 < sda5 >
[    5.215769] sd 2:0:0:0: [sda] Attached SCSI disk
[    5.348641] PM: Starting manual resume from disk
[    5.348644] PM: Resume from partition 8:5
[    5.348646] PM: Checking hibernation image.
[    5.348782] PM: Resume from disk failed.
[    5.394882] kjournald starting.  Commit interval 5 seconds
[    5.394900] EXT3-fs: mounted filesystem with ordered data mode.
[    9.977569] usb-storage: device scan complete
[    9.982194] scsi 4:0:0:0: Direct-Access     ASUS     Flash HS-CF      3.95 PQ: 0 ANSI: 0
[    9.985432] scsi 4:0:0:1: Direct-Access     ASUS     Flash HS-COMBO   3.95 PQ: 0 ANSI: 0
[    9.989979] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[    9.990063] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   10.041094] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   10.041127] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   11.499569] udevd version 124 started
[   12.236211] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   12.289445] device-mapper: multipath: version 1.0.5 loaded
[   12.331282] ACPI: I/O resource nForce2_smbus [0x4c00-0x4c3f] conflicts with ACPI region SM00 [0x4c00-0x4c05]
[   12.331285] ACPI: Device needs an ACPI driver
[   12.331310] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   12.331323] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   12.417986] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input5
[   12.445040] ACPI: Power Button (FF) [PWRF]
[   12.445113] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input6
[   12.457106] Linux agpgart interface v0.103
[   12.477025] ACPI: Power Button (CM) [PWRB]
[   12.627713] nvidia: module license 'NVIDIA' taints kernel.
[   12.998200] ACPI: PCI Interrupt Link [APC7] enabled at IRQ 16
[   12.998211] nvidia 0000:00:05.0: PCI INT A -> Link[APC7] -> GSI 16 (level, low) -> IRQ 16
[   12.998216] nvidia 0000:00:05.0: setting latency timer to 64
[   12.998408] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.11  Wed Nov 26 10:53:26 PST 2008
[   13.004987] parport_pc 00:08: reported by Plug and Play ACPI
[   13.005032] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   13.010896] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   13.059251] wlan: 0.9.4
[   13.063323] ath_pci: 0.9.4
[   13.063705] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   13.063714] ath_pci 0000:01:0e.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   13.652430] ath_rate_sample: 1.2 (0.9.4)
[   13.652849] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   13.652853] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   13.652860] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   13.652865] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   13.652868] wifi0: mac 7.9 phy 4.5 radio 5.6
[   13.652871] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   13.652873] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   13.652874] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   13.652876] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   13.652877] wifi0: Use hw queue 8 for CAB traffic
[   13.652878] wifi0: Use hw queue 9 for beacons
[   13.683123] wifi0: Atheros 5212: mem=0xfdde0000, irq=17
[   13.718418] snd_rawmidi: disagrees about version of symbol snd_info_register
[   13.718423] snd_rawmidi: Unknown symbol snd_info_register
[   13.718487] snd_rawmidi: disagrees about version of symbol snd_seq_device_new
[   13.718488] snd_rawmidi: Unknown symbol snd_seq_device_new
[   13.718547] snd_rawmidi: disagrees about version of symbol snd_info_free_entry
[   13.718549] snd_rawmidi: Unknown symbol snd_info_free_entry
[   13.718611] snd_rawmidi: disagrees about version of symbol snd_unregister_oss_device
[   13.718612] snd_rawmidi: Unknown symbol snd_unregister_oss_device
[   13.718669] snd_rawmidi: disagrees about version of symbol snd_register_oss_device
[   13.718671] snd_rawmidi: Unknown symbol snd_register_oss_device
[   13.718726] snd_rawmidi: disagrees about version of symbol snd_ctl_register_ioctl
[   13.718728] snd_rawmidi: Unknown symbol snd_ctl_register_ioctl
[   13.718777] snd_rawmidi: disagrees about version of symbol snd_card_file_add
[   13.718779] snd_rawmidi: Unknown symbol snd_card_file_add
[   13.719036] snd_rawmidi: disagrees about version of symbol snd_unregister_device
[   13.719037] snd_rawmidi: Unknown symbol snd_unregister_device
[   13.719099] snd_rawmidi: disagrees about version of symbol snd_device_new
[   13.719101] snd_rawmidi: Unknown symbol snd_device_new
[   13.719152] snd_rawmidi: disagrees about version of symbol snd_ctl_unregister_ioctl
[   13.719154] snd_rawmidi: Unknown symbol snd_ctl_unregister_ioctl
[   13.719337] snd_rawmidi: disagrees about version of symbol snd_info_create_card_entry
[   13.719339] snd_rawmidi: Unknown symbol snd_info_create_card_entry
[   13.719394] snd_rawmidi: disagrees about version of symbol snd_card_file_remove
[   13.719396] snd_rawmidi: Unknown symbol snd_card_file_remove
[   13.719448] snd_rawmidi: disagrees about version of symbol snd_register_device_for_dev
[   13.719450] snd_rawmidi: Unknown symbol snd_register_device_for_dev
[   13.719510] snd_rawmidi: disagrees about version of symbol snd_device_register
[   13.719512] snd_rawmidi: Unknown symbol snd_device_register
[   13.730184] snd_seq_midi: Unknown symbol snd_rawmidi_info_select
[   13.730454] snd_seq_midi: Unknown symbol snd_rawmidi_output_params
[   13.730606] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_read
[   13.730653] snd_seq_midi: disagrees about version of symbol snd_seq_device_register_driver
[   13.730655] snd_seq_midi: Unknown symbol snd_seq_device_register_driver
[   13.730716] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_write
[   13.730835] snd_seq_midi: Unknown symbol snd_rawmidi_drain_output
[   13.731031] snd_seq_midi: Unknown symbol snd_rawmidi_input_params
[   13.731152] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_open
[   13.731198] snd_seq_midi: disagrees about version of symbol snd_seq_create_kernel_client
[   13.731200] snd_seq_midi: Unknown symbol snd_seq_create_kernel_client
[   13.731266] snd_seq_midi: Unknown symbol snd_rawmidi_kernel_release
[   14.263782] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[   14.263877] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   14.263879] snd_hda_intel: Unknown symbol snd_ctl_add
[   14.263962] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   14.263964] snd_hda_intel: Unknown symbol snd_pcm_new
[   14.264028] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   14.264030] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   14.264086] snd_hda_intel: disagrees about version of symbol snd_card_register
[   14.264088] snd_hda_intel: Unknown symbol snd_card_register
[   14.264139] snd_hda_intel: disagrees about version of symbol snd_card_free
[   14.264141] snd_hda_intel: Unknown symbol snd_card_free
[   14.264190] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   14.264192] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   14.264243] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   14.264245] snd_hda_intel: Unknown symbol snd_card_proc_new
[   14.264418] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   14.264419] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   14.264467] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync
[   14.264468] snd_hda_intel: Unknown symbol snd_pcm_set_sync
[   14.264594] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   14.264596] snd_hda_intel: Unknown symbol snd_ctl_new1
[   14.264722] snd_hda_intel: disagrees about version of symbol snd_component_add
[   14.264724] snd_hda_intel: Unknown symbol snd_component_add
[   14.264790] snd_hda_intel: Unknown symbol snd_ctl_make_virtual_master
[   14.264870] snd_hda_intel: Unknown symbol snd_card_new
[   14.264976] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   14.264978] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   14.265053] snd_hda_intel: disagrees about version of symbol snd_ctl_boolean_mono_info
[   14.265055] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[   14.265122] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   14.265123] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   14.265177] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   14.265178] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   14.265255] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   14.265257] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   14.265317] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   14.265319] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   14.265407] snd_hda_intel: disagrees about version of symbol snd_device_new
[   14.265409] snd_hda_intel: Unknown symbol snd_device_new
[   14.265457] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page
[   14.265458] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[   14.265533] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   14.265535] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   14.265610] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   14.265612] snd_hda_intel: Unknown symbol snd_card_disconnect
[   14.265659] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   14.265661] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   14.265798] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup
[   14.265800] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[   14.265929] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   14.265931] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   14.265977] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   14.265979] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   35.133608] lp0: using parport0 (interrupt-driven).
[   35.152924] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[   35.153019] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[   35.153021] snd_hda_intel: Unknown symbol snd_ctl_add
[   35.153104] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[   35.153106] snd_hda_intel: Unknown symbol snd_pcm_new
[   35.153171] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[   35.153172] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[   35.153229] snd_hda_intel: disagrees about version of symbol snd_card_register
[   35.153231] snd_hda_intel: Unknown symbol snd_card_register
[   35.153282] snd_hda_intel: disagrees about version of symbol snd_card_free
[   35.153284] snd_hda_intel: Unknown symbol snd_card_free
[   35.153333] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[   35.153335] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[   35.153387] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[   35.153388] snd_hda_intel: Unknown symbol snd_card_proc_new
[   35.153562] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[   35.153564] snd_hda_intel: Unknown symbol snd_ctl_find_id
[   35.153612] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync
[   35.153613] snd_hda_intel: Unknown symbol snd_pcm_set_sync
[   35.153740] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[   35.153741] snd_hda_intel: Unknown symbol snd_ctl_new1
[   35.153868] snd_hda_intel: disagrees about version of symbol snd_component_add
[   35.153870] snd_hda_intel: Unknown symbol snd_component_add
[   35.153937] snd_hda_intel: Unknown symbol snd_ctl_make_virtual_master
[   35.154016] snd_hda_intel: Unknown symbol snd_card_new
[   35.154123] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[   35.154125] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[   35.154176] snd_hda_intel: disagrees about version of symbol snd_ctl_boolean_mono_info
[   35.154178] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[   35.154245] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[   35.154246] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[   35.154300] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[   35.154302] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[   35.154379] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[   35.154381] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[   35.154442] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[   35.154444] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[   35.154532] snd_hda_intel: disagrees about version of symbol snd_device_new
[   35.154533] snd_hda_intel: Unknown symbol snd_device_new
[   35.154582] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page
[   35.154583] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[   35.154658] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[   35.154660] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[   35.154736] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[   35.154738] snd_hda_intel: Unknown symbol snd_card_disconnect
[   35.154785] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[   35.154787] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[   35.154925] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup
[   35.154927] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[   35.155057] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[   35.155058] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[   35.155105] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[   35.155107] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
[   35.189264] snd_ac97_codec: Unknown symbol snd_ctl_add_slave
[   35.189317] snd_ac97_codec: disagrees about version of symbol snd_info_register
[   35.189319] snd_ac97_codec: Unknown symbol snd_info_register
[   35.189371] snd_ac97_codec: disagrees about version of symbol snd_ctl_add
[   35.189372] snd_ac97_codec: Unknown symbol snd_ctl_add
[   35.189483] snd_ac97_codec: disagrees about version of symbol snd_info_free_entry
[   35.189485] snd_ac97_codec: Unknown symbol snd_info_free_entry
[   35.189598] snd_ac97_codec: disagrees about version of symbol snd_ctl_find_id
[   35.189600] snd_ac97_codec: Unknown symbol snd_ctl_find_id
[   35.189651] snd_ac97_codec: disagrees about version of symbol snd_ctl_new1
[   35.189652] snd_ac97_codec: Unknown symbol snd_ctl_new1
[   35.189711] snd_ac97_codec: disagrees about version of symbol snd_ctl_remove_id
[   35.189712] snd_ac97_codec: Unknown symbol snd_ctl_remove_id
[   35.189781] snd_ac97_codec: disagrees about version of symbol snd_component_add
[   35.189782] snd_ac97_codec: Unknown symbol snd_component_add
[   35.189846] snd_ac97_codec: Unknown symbol snd_ctl_make_virtual_master
[   35.189894] snd_ac97_codec: disagrees about version of symbol snd_pcm_hw_rule_add
[   35.189895] snd_ac97_codec: Unknown symbol snd_pcm_hw_rule_add
[   35.190023] snd_ac97_codec: disagrees about version of symbol snd_ctl_boolean_mono_info
[   35.190025] snd_ac97_codec: Unknown symbol snd_ctl_boolean_mono_info
[   35.190180] snd_ac97_codec: disagrees about version of symbol snd_device_new
[   35.190182] snd_ac97_codec: Unknown symbol snd_device_new
[   35.190311] snd_ac97_codec: disagrees about version of symbol snd_info_create_card_entry
[   35.190313] snd_ac97_codec: Unknown symbol snd_info_create_card_entry
[   35.339349] Adding 5695000k swap on /dev/sda5.  Priority:-1 extents:1 across:5695000k
[   35.893035] EXT3 FS on sda1, internal journal
[   36.833620] type=1505 audit(1245254606.790:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=4485
[   36.970440] type=1505 audit(1245254606.927:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4490
[   36.970611] type=1505 audit(1245254606.927:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4490
[   37.004658] type=1505 audit(1245254606.962:5): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=4494
[   37.040251] type=1505 audit(1245254606.995:6): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=4498
[   37.156590] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.881552] ACPI: WMI: Mapper loaded
[   38.123305] powernow-k8: Found 1 AMD Processor model unknown processors (2 cpu cores) (version 2.20.00)
[   38.123773] powernow-k8:    0 : fid 0x16 (3000 MHz), vid 0x6
[   38.123776] powernow-k8:    1 : fid 0x14 (2800 MHz), vid 0x8
[   38.123778] powernow-k8:    2 : fid 0x12 (2600 MHz), vid 0xa
[   38.123780] powernow-k8:    3 : fid 0x10 (2400 MHz), vid 0xc
[   38.123782] powernow-k8:    4 : fid 0xe (2200 MHz), vid 0xe
[   38.123783] powernow-k8:    5 : fid 0xc (2000 MHz), vid 0x10
[   38.123785] powernow-k8:    6 : fid 0xa (1800 MHz), vid 0x10
[   38.123786] powernow-k8:    7 : fid 0x2 (1000 MHz), vid 0x12
[   38.925699] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   39.171436] NET: Registered protocol family 10
[   39.171887] lo: Disabled Privacy Extensions
[   41.380462] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   41.380469] apm: disabled - APM is not SMP safe.
[   41.696496] ppdev: user-space parallel port driver
[   45.863416] NET: Registered protocol family 17
[   47.577033] Clocksource tsc unstable (delta = -173417909 ns)
[   47.945436] eth0: no link during initialization.
[   47.946155] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.812415] Bluetooth: Core ver 2.13
[   52.812521] NET: Registered protocol family 31
[   52.812529] Bluetooth: HCI device and connection manager initialized
[   52.812542] Bluetooth: HCI socket layer initialized
[   52.846067] Bluetooth: L2CAP ver 2.11
[   52.846079] Bluetooth: L2CAP socket layer initialized
[   52.897776] Bluetooth: RFCOMM socket layer initialized
[   52.897806] Bluetooth: RFCOMM TTY layer initialized
[   52.897811] Bluetooth: RFCOMM ver 1.10
[   52.907520] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   52.907528] Bluetooth: BNEP filters: protocol multicast
[   53.061877] Bridge firewalling registered
[   53.095888] Bluetooth: SCO (Voice Link) ver 0.6
[   53.095902] Bluetooth: SCO socket layer initialized
[   68.360026] ath0: no IPv6 routers present
[  166.168419] ppdev0: registered pardevice
[  166.216361] ppdev0: unregistered pardevice
[  167.404988] ppdev0: registered pardevice
[  167.445156] ppdev0: unregistered pardevice
[  168.270804] ppdev0: registered pardevice
[  168.316286] ppdev0: unregistered pardevice
[ 4632.655577] snd_hda_intel: Unknown symbol snd_ctl_add_slave
[ 4632.655682] snd_hda_intel: disagrees about version of symbol snd_ctl_add
[ 4632.655684] snd_hda_intel: Unknown symbol snd_ctl_add
[ 4632.655772] snd_hda_intel: disagrees about version of symbol snd_pcm_new
[ 4632.655774] snd_hda_intel: Unknown symbol snd_pcm_new
[ 4632.655843] snd_hda_intel: disagrees about version of symbol snd_pcm_limit_hw_rates
[ 4632.655845] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[ 4632.655906] snd_hda_intel: disagrees about version of symbol snd_card_register
[ 4632.655908] snd_hda_intel: Unknown symbol snd_card_register
[ 4632.655964] snd_hda_intel: disagrees about version of symbol snd_card_free
[ 4632.655966] snd_hda_intel: Unknown symbol snd_card_free
[ 4632.656053] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_preallocate_pages_for_all
[ 4632.656055] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[ 4632.656112] snd_hda_intel: disagrees about version of symbol snd_card_proc_new
[ 4632.656113] snd_hda_intel: Unknown symbol snd_card_proc_new
[ 4632.656291] snd_hda_intel: disagrees about version of symbol snd_ctl_find_id
[ 4632.656293] snd_hda_intel: Unknown symbol snd_ctl_find_id
[ 4632.656345] snd_hda_intel: disagrees about version of symbol snd_pcm_set_sync
[ 4632.656347] snd_hda_intel: Unknown symbol snd_pcm_set_sync
[ 4632.661620] snd_hda_intel: disagrees about version of symbol snd_ctl_new1
[ 4632.661625] snd_hda_intel: Unknown symbol snd_ctl_new1
[ 4632.661757] snd_hda_intel: disagrees about version of symbol snd_component_add
[ 4632.661759] snd_hda_intel: Unknown symbol snd_component_add
[ 4632.661840] snd_hda_intel: Unknown symbol snd_ctl_make_virtual_master
[ 4632.661924] snd_hda_intel: Unknown symbol snd_card_new
[ 4632.662577] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_malloc_pages
[ 4632.662580] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[ 4632.662636] snd_hda_intel: disagrees about version of symbol snd_ctl_boolean_mono_info
[ 4632.662638] snd_hda_intel: Unknown symbol snd_ctl_boolean_mono_info
[ 4632.662711] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_ioctl
[ 4632.662712] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[ 4632.662771] snd_hda_intel: disagrees about version of symbol snd_pcm_lib_free_pages
[ 4632.662772] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[ 4632.662855] snd_hda_intel: disagrees about version of symbol snd_pcm_set_ops
[ 4632.662856] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[ 4632.662922] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_list
[ 4632.662924] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_list
[ 4632.663017] snd_hda_intel: disagrees about version of symbol snd_device_new
[ 4632.663019] snd_hda_intel: Unknown symbol snd_device_new
[ 4632.663072] snd_hda_intel: disagrees about version of symbol snd_pcm_sgbuf_ops_page
[ 4632.663074] snd_hda_intel: Unknown symbol snd_pcm_sgbuf_ops_page
[ 4632.663153] snd_hda_intel: disagrees about version of symbol snd_pcm_suspend_all
[ 4632.663155] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[ 4632.663236] snd_hda_intel: disagrees about version of symbol snd_card_disconnect
[ 4632.663237] snd_hda_intel: Unknown symbol snd_card_disconnect
[ 4632.663290] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_integer
[ 4632.663292] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[ 4632.663434] snd_hda_intel: disagrees about version of symbol snd_pci_quirk_lookup
[ 4632.663436] snd_hda_intel: Unknown symbol snd_pci_quirk_lookup
[ 4632.663576] snd_hda_intel: disagrees about version of symbol snd_pcm_period_elapsed
[ 4632.663577] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed
[ 4632.663629] snd_hda_intel: disagrees about version of symbol snd_pcm_hw_constraint_step
[ 4632.663631] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_step
zoe@OpenGEUbox:~$



2009/6/17 Philip J Groves <philip.groves@gmail.com>
- Show quoted text -

    Zoe,

    It sounds as if the requisites for the snd-hda-intel module are not being met. "sudo depmod" should fix that.

    Then retry "sudo modprobe snd-hda-intel"

    Phil



    ----- Original message -----
    Sent: 2009/06/16 19:41:55
    Subject: Re: Re: Re: tomorrow

    hi phil

    thanks for your assistance :)))))

    this is what i got with those commands


    zoe@OpenGEUbox:~$ lsmod | grep snd_hda_intel


    zoe@OpenGEUbox:~$ sudo modprobe snd_hda_intel
    [sudo] password for zoe:                    
    FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.27-14-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)                                                                        
    zoe@OpenGEUbox:~$ dmesg                                                        
    [    0.000000] Initializing cgroup subsys cpuset                               
    [    0.000000] Initializing cgroup subsys cpu                                  
    [    0.000000] Linux version 2.6.27-14-generic (buildd@vernadsky) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) ) #1 SMP Fri Jun 5 10:14:59 UTC 2009 (Ubuntu 2.6.27-14.34-generic)                                                               
    [    0.000000] BIOS-provided physical RAM map:                                 
    [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)        
    [    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)      
    [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)      
    [    0.000000]  BIOS-e820: 0000000000100000 - 0000000077ef0000 (usable)        
    [    0.000000]  BIOS-e820: 0000000077ef0000 - 0000000077ef3000 (ACPI NVS)      
    [    0.000000]  BIOS-e820: 0000000077ef3000 - 0000000077f00000 (ACPI data)     
    [    0.000000]  BIOS-e820: 0000000078000000 - 0000000080000000 (reserved)      
    [    0.000000]  BIOS-e820: 00000000f0000000 - 00000000f4000000 (reserved)      
    [    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)      
    [    0.000000] DMI 2.3 present.                                                
    [    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working it around.                                                                             
    [    0.000000] last_pfn = 0x77ef0 max_arch_pfn = 0x100000                      
    [    0.000000] kernel direct mapping tables up to 38000000 @ 10000-15000       
    [    0.000000] RAMDISK: 3770d000 - 37fef32c                                    
    [    0.000000] ACPI: RSDP 000F6D00, 0014 (r0 Nvidia)                           
    [    0.000000] ACPI: RSDT 77EF3040, 0034 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)                                                                           
    [    0.000000] ACPI: FACP 77EF30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)                                                                           
    [    0.000000] ACPI: DSDT 77EF3180, 6E72 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)                                                                           
    [    0.000000] ACPI: FACS 77EF0000, 0040                                       
    [    0.000000] ACPI: SSDT 77EFA100, 030E (r1 PTLTD  POWERNOW        1  LTP        1)                                                                           
    [    0.000000] ACPI: MCFG 77EFA480, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)                                                                           
    [    0.000000] ACPI: APIC 77EFA040, 007C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)                                                                           
    [    0.000000] 1022MB HIGHMEM available.                                       
    [    0.000000] 896MB LOWMEM available.                                         
    [    0.000000]   mapped low ram: 0 - 38000000                                  
    [    0.000000]   low ram: 00000000 - 38000000                                  
    [    0.000000]   bootmap 00011000 - 00018000                                   
    [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]    
    [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]                                                                   
    [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]                                                                   
    [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]                                                                   
    [    0.000000]   #3 [0000100000 - 00005c59e0]    TEXT DATA BSS ==> [0000100000 - 00005c59e0]                                                                   
    [    0.000000]   #4 [003770d000 - 0037fef32c]          RAMDISK ==> [003770d000 - 0037fef32c]                                                                   
    [    0.000000]   #5 [00005c6000 - 00005c9000]    INIT_PG_TABLE ==> [00005c6000 - 00005c9000]                                                                   
    [    0.000000]   #6 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]                                                                   
    [    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]                                                                   
    [    0.000000]   #8 [0000011000 - 0000018000]          BOOTMAP ==> [0000011000 - 0000018000]                                                                   
    [    0.000000] found SMP MP-table at [c00f5270] 000f5270                       
    [    0.000000] Zone PFN ranges:                                                
    [    0.000000]   DMA      0x00000010 -> 0x00001000                             
    [    0.000000]   Normal   0x00001000 -> 0x00038000                             
    [    0.000000]   HighMem  0x00038000 -> 0x00077ef0                             
    [    0.000000] Movable zone start PFN for each node                            
    [    0.000000] early_node_map[2] active PFN ranges                             
    [    0.000000]     0: 0x00000010 -> 0x0000009f                                 
    [    0.000000]     0: 0x00000100 -> 0x00077ef0                                 
    [    0.000000] On node 0 totalpages: 491135                                    
    [    0.000000] free_area_init_node: node 0, pgdat c048d700, node_mem_map c1000240                                                                              
    [    0.000000]   DMA zone: 3947 pages, LIFO batch:0                            
    [    0.000000]   Normal zone: 223300 pages, LIFO batch:31                      
    [    0.000000]   HighMem zone: 259570 pages, LIFO batch:31                     
    [    0.000000] Nvidia board detected. Ignoring ACPI timer override.            
    [    0.000000] If you got timer trouble try acpi_use_timer_override            
    [    0.000000] ACPI: PM-Timer IO Port: 0x4008                                  
    [    0.000000] ACPI: Local APIC address 0xfee00000                             
    [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)              
    [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)              
    [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])             
    [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])             
    [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])         
    [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23  
    [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)        
    [    0.000000] ACPI: BIOS IRQ0 pin2 override ignored.                          
    [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)     
    [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)    
    [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)    
    [    0.000000] ACPI: IRQ9 used by override.                                    
    [    0.000000] ACPI: IRQ14 used by override.                                   
    [    0.000000] ACPI: IRQ15 used by override.                                   
    [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs                   
    [    0.000000] Using ACPI (MADT) for SMP configuration information             
    [    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs                            
    [    0.000000] mapped APIC to ffffb000 (fee00000)                              
    [    0.000000] mapped IOAPIC to ffffa000 (fec00000)                            
    [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
    [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
    [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
    [    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:70000000)                                                                          
    [    0.000000] PERCPU: Allocating 41628 bytes of per cpu data                  
    [    0.000000] NR_CPUS: 64, nr_cpu_ids: 2, nr_node_ids 1                       
    [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 486817                                                                     
    [    0.000000] Kernel command line: root=UUID=e2491bd4-3091-40b5-8e3b-0201950859ea ro quiet splash                                                             
    [    0.000000] Enabling fast FPU save and restore... done.                     
    [    0.000000] Enabling unmasked SIMD FPU exception support... done.           
    [    0.000000] Initializing CPU#0                                              
    [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)           
    [    0.000000] TSC: PIT calibration confirmed by PMTIMER.                      
    [    0.000000] TSC: using PIT calibration value                                
    [    0.000000] Detected 3013.823 MHz processor.                                
    [    0.004000] spurious 8259A interrupt: IRQ7.                                 
    [    0.004000] Console: colour VGA+ 80x25                                      
    [    0.004000] console [tty0] enabled                                          
    [    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
    [    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)  
    [    0.004000] Memory: 1931416k/1964992k available (2581k kernel code, 32208k reserved, 1163k data, 428k init, 1047488k highmem)                               
    [    0.004000] virtual kernel memory layout:                                   
    [    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)               
    [    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)               
    [    0.004000]     vmalloc : 0xf8800000 - 0xff3fe000   ( 107 MB)               
    [    0.004000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)               
    [    0.004000]       .init : 0xc04af000 - 0xc051a000   ( 428 kB)               
    [    0.004000]       .data : 0xc038571a - 0xc04a8680   (1163 kB)               
    [    0.004000]       .text : 0xc0100000 - 0xc038571a   (2581 kB)               
    [    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.                                                                     
    [    0.004000] CPA: page pool initialized 1 of 1 pages preallocated            
    [    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1                                                                         
    [    0.004007] Calibrating delay loop (skipped), value calculated using timer frequency.. 6027.64 BogoMIPS (lpj=12055292)                                      
    [    0.004021] Security Framework initialized                                  
    [    0.004026] SELinux:  Disabled at boot.                                     
    [    0.004042] AppArmor: AppArmor initialized                                  
    [    0.004048] Mount-cache hash table entries: 512                             
    [    0.004168] Initializing cgroup subsys ns                                   
    [    0.004171] Initializing cgroup subsys cpuacct                              
    [    0.004173] Initializing cgroup subsys memory                               
    [    0.004182] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
    [    0.004184] CPU: L2 Cache: 1024K (64 bytes/line)                            
    [    0.004186] CPU 0(2) -> Core 0                                              
    [    0.004189] using C1E aware idle routine                                    
    [    0.004197] Checking 'hlt' instruction... OK.                               
    [    0.021132] ACPI: Core revision 20080609                                    
    [    0.022895] ACPI: Checking initramfs for custom DSDT                        
    [    0.276348] ENABLING IO-APIC IRQs                                           
    [    0.276567] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1            
    [    0.284017] ..MP-BIOS bug: 8254 timer not connected to IO-APIC              
    [    0.284017] ...trying to set up timer (IRQ0) through the 8259A ...          
    [    0.284017] ..... (found apic 0 pin 0) ...                                  
    [    0.292018] ....... failed.                                                 
    [    0.292018] ...trying to set up timer as Virtual Wire IRQ...                
    [    0.292018] ..... failed.                                                   
    [    0.292018] ...trying to set up timer as ExtINT IRQ...                      
    [    0.335314] ..... works.                                                    
    [    0.335315] CPU0: AMD Processor model unknown stepping 03                   
    [    0.336021] Booting processor 1/1 ip 6000                                   
    [    0.004000] Initializing CPU#1                                              
    [    0.388024] Calibrating delay using timer specific routine.. 6028.18 BogoMIPS (lpj=12056368)                                                                
    [    0.388024] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
    [    0.388024] CPU: L2 Cache: 1024K (64 bytes/line)                            
    [    0.388024] CPU 1(2) -> Core 1                                              
    [    0.420216] CPU1: AMD Processor model unknown stepping 03                   
    [    0.420236] Brought up 2 CPUs                                               
    [    0.420238] Total of 2 processors activated (12055.83 BogoMIPS).            
    [    0.420278] CPU0 attaching sched-domain:                                    
    [    0.420280]  domain 0: span 0-1 level CPU                                   
    [    0.420282]   groups: 0 1                                                   
    [    0.420286] CPU1 attaching sched-domain:                                    
    [    0.420288]  domain 0: span 0-1 level CPU                                   
    [    0.420289]   groups: 1 0                                                   
    [    0.420333] net_namespace: 840 bytes                                        
    [    0.420333] Booting paravirtualized kernel on bare hardware                 
    [    0.420333] Time: 16:36:36  Date: 06/16/09                                  
    [    0.420333] NET: Registered protocol family 16                              
    [    0.420333] EISA bus registered                                             
    [    0.420333] ACPI: bus type pci registered                                   
    [    0.420333] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 255
    [    0.420333] PCI: MCFG area at f0000000 reserved in E820                     
    [    0.420333] PCI: updated MCFG configuration 0: base f0000000 segment 0 buses 0 - 63                                                                         
    [    0.420333] PCI: Using MMCONFIG for extended config space                   
    [    0.420333] PCI: Using configuration type 1 for base access                 
    [    0.420910] ACPI: EC: Look up EC in DSDT                                    
    [    0.430298] ACPI: Interpreter enabled                                       
    [    0.430301] ACPI: (supports S0 S1 S3 S4 S5)                                 
    [    0.430312] ACPI: Using IOAPIC for interrupt routing                        
    [    0.436524] ACPI: PCI Root Bridge [PCI0] (0000:00)                          
    [    0.436524] PCI: 0000:00:05.0 reg 10 32bit mmio: [fb000000, fbffffff]       
    [    0.436524] PCI: 0000:00:05.0 reg 14 64bit mmio: [e0000000, efffffff]       
    [    0.436524] PCI: 0000:00:05.0 reg 1c 64bit mmio: [fc000000, fcffffff]       
    [    0.436524] PCI: 0000:00:05.0 reg 30 32bit mmio: [0, 1ffff]                 
    [    0.436524] HPET not enabled in BIOS. You might try hpet=force boot option  
    [    0.436524] PCI: 0000:00:0a.1 reg 20 io port: [4c00, 4c3f]                  
    [    0.436524] PCI: 0000:00:0a.1 reg 24 io port: [4c40, 4c7f]                  
    [    0.436524] pci 0000:00:0a.1: PME# supported from D3hot D3cold              
    [    0.436524] pci 0000:00:0a.1: PME# disabled                                 
    [    0.436524] PCI: 0000:00:0b.0 reg 10 32bit mmio: [fe02f000, fe02ffff]       
    [    0.436533] pci 0000:00:0b.0: supports D1                                   
    [    0.436534] pci 0000:00:0b.0: supports D2                                   
    [    0.436536] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold     
    [    0.436539] pci 0000:00:0b.0: PME# disabled                                 
    [    0.436556] PCI: 0000:00:0b.1 reg 10 32bit mmio: [fe02e000, fe02e0ff]       
    [    0.436586] pci 0000:00:0b.1: supports D1                                   
    [    0.436587] pci 0000:00:0b.1: supports D2                                   
    [    0.436589] pci 0000:00:0b.1: PME# supported from D0 D1 D2 D3hot D3cold     
    [    0.436592] pci 0000:00:0b.1: PME# disabled                                 
    [    0.436618] PCI: 0000:00:0d.0 reg 20 io port: [f400, f40f]                  
    [    0.436652] PCI: 0000:00:0e.0 reg 10 io port: [9f0, 9f7]                    
    [    0.436656] PCI: 0000:00:0e.0 reg 14 io port: [bf0, bf3]                    
    [    0.436659] PCI: 0000:00:0e.0 reg 18 io port: [970, 977]                    
    [    0.436663] PCI: 0000:00:0e.0 reg 1c io port: [b70, b73]                    
    [    0.436666] PCI: 0000:00:0e.0 reg 20 io port: [e000, e00f]                  
    [    0.436670] PCI: 0000:00:0e.0 reg 24 32bit mmio: [fe02d000, fe02dfff]       
    [    0.440037] PCI: 0000:00:10.1 reg 10 32bit mmio: [fe028000, fe02bfff]       
    [    0.440072] pci 0000:00:10.1: PME# supported from D3hot D3cold              
    [    0.440075] pci 0000:00:10.1: PME# disabled                                 
    [    0.440097] PCI: 0000:00:14.0 reg 10 32bit mmio: [fe02c000, fe02cfff]       
    [    0.440101] PCI: 0000:00:14.0 reg 14 io port: [dc00, dc07]                  
    [    0.440122] pci 0000:00:14.0: supports D1                                   
    [    0.440123] pci 0000:00:14.0: supports D2                                   
    [    0.440125] pci 0000:00:14.0: PME# supported from D0 D1 D2 D3hot D3cold     
    [    0.440128] pci 0000:00:14.0: PME# disabled                                 
    [    0.440199] PCI: 0000:01:03.0 reg 10 32bit mmio: [fddff000, fddff7ff]       
    [    0.440204] PCI: 0000:01:03.0 reg 14 io port: [cc00, cc7f]                  
    [    0.440238] pci 0000:01:03.0: supports D2                                   
    [    0.440240] pci 0000:01:03.0: PME# supported from D2 D3hot D3cold           
    [    0.440243] pci 0000:01:03.0: PME# disabled                                 
    [    0.440271] PCI: 0000:01:0e.0 reg 10 32bit mmio: [fdde0000, fddeffff]       
    [    0.440323] pci 0000:00:10.0: transparent bridge                            
    [    0.440326] PCI: bridge 0000:00:10.0 io port: [c000, cfff]                  
    [    0.440329] PCI: bridge 0000:00:10.0 32bit mmio: [fdd00000, fddfffff]       
    [    0.440331] PCI: bridge 0000:00:10.0 32bit mmio pref: [fde00000, fdefffff]  
    [    0.440336] bus 00 -> node 0                                                
    [    0.440341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]             
    [    0.440580] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]        
    [    0.517935] ACPI: PCI Interrupt Link [LNK1] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.517935] ACPI: PCI Interrupt Link [LNK2] (IRQs 5 7 9 *10 11 14 15)       
    [    0.517935] ACPI: PCI Interrupt Link [LNK3] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.517935] ACPI: PCI Interrupt Link [LNK4] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.517935] ACPI: PCI Interrupt Link [LNK5] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.517935] ACPI: PCI Interrupt Link [LNK6] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.517935] ACPI: PCI Interrupt Link [LNK7] (IRQs *5 7 9 10 11 14 15)       
    [    0.517935] ACPI: PCI Interrupt Link [LNK8] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.517935] ACPI: PCI Interrupt Link [LUBA] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.517935] ACPI: PCI Interrupt Link [LUBB] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.517964] ACPI: PCI Interrupt Link [LMAC] (IRQs 5 7 9 10 *11 14 15)       
    [    0.520202] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.520382] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 9 10 *11 14 15)       
    [    0.520560] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.520738] ACPI: PCI Interrupt Link [LMCI] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.520916] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.521095] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.521273] ACPI: PCI Interrupt Link [LIDE] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.521453] ACPI: PCI Interrupt Link [LSID] (IRQs 5 7 9 *10 11 14 15)       
    [    0.521630] ACPI: PCI Interrupt Link [LFID] (IRQs 5 7 9 10 11 14 15) *0, disabled.                                                                          
    [    0.521846] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.         
    [    0.522056] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0                    
    [    0.522265] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.         
    [    0.522475] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.         
    [    0.522684] ACPI: PCI Interrupt Link [APC5] (IRQs 16) *0, disabled.         
    [    0.522894] ACPI: PCI Interrupt Link [APC6] (IRQs 16) *0, disabled.         
    [    0.523103] ACPI: PCI Interrupt Link [APC7] (IRQs 16) *0                    
    [    0.523312] ACPI: PCI Interrupt Link [APC8] (IRQs 16) *0, disabled.         
    [    0.523522] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0, disabled.
    [    0.523733] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
    [    0.523946] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0           
    [    0.524168] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0, disabled.
    [    0.524379] ACPI: PCI Interrupt Link [APMU] (IRQs 20 21 22 23) *0, disabled.
    [    0.524591] ACPI: PCI Interrupt Link [AAZA] (IRQs 20 21 22 23) *0           
    [    0.524802] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
    [    0.525013] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0, disabled.
    [    0.525225] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0, disabled.
    [    0.525436] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22 23) *0, disabled.
    [    0.525647] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
    [    0.525859] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0           
    [    0.526070] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0, disabled.
    [    0.526130] Linux Plug and Play Support v0.97 (c) Adam Belay                
    [    0.526130] pnp: PnP ACPI init                                              
    [    0.526130] ACPI: bus type pnp registered                                   
    [    0.529445] pnp: PnP ACPI: found 11 devices                                 
    [    0.529445] ACPI: ACPI bus type pnp unregistered                            
    [    0.529445] PnPBIOS: Disabled by ACPI PNP                                   
    [    0.529445] PCI: Using ACPI for IRQ routing                                 
    [    0.536038] NET: Registered protocol family 8                               
    [    0.536039] NET: Registered protocol family 20                              
    [    0.536059] NetLabel: Initializing                                          
    [    0.536060] NetLabel:  domain hash size = 128                               
    [    0.536062] NetLabel:  protocols = UNLABELED CIPSOv4                        
    [    0.536072] NetLabel:  unlabeled traffic allowed by default                 
    [    0.536451] tracer: 772 pages allocated for 65536 entries of 48 bytes       
    [    0.536452]    actual entries 65620                                         
    [    0.536552] AppArmor: AppArmor Filesystem Enabled                           
    [    0.536578] ACPI: RTC can wake from S4                                      
    [    0.544045] system 00:01: ioport range 0x4000-0x407f has been reserved      
    [    0.544047] system 00:01: ioport range 0x4080-0x40ff has been reserved      
    [    0.544049] system 00:01: ioport range 0x4400-0x447f has been reserved      
    [    0.544051] system 00:01: ioport range 0x4480-0x44ff has been reserved      
    [    0.544053] system 00:01: ioport range 0x4800-0x487f has been reserved      
    [    0.544055] system 00:01: ioport range 0x4880-0x48ff has been reserved      
    [    0.544057] system 00:01: ioport range 0x2000-0x207f has been reserved      
    [    0.544059] system 00:01: ioport range 0x2080-0x20ff has been reserved      
    [    0.544061] system 00:01: iomem range 0x78000000-0x7fffffff could not be reserved                                                                           
    [    0.544065] system 00:02: ioport range 0x4d0-0x4d1 has been reserved        
    [    0.544067] system 00:02: ioport range 0x800-0x87f has been reserved        
    [    0.544073] system 00:09: iomem range 0xf0000000-0xf3ffffff could not be reserved                                                                           
    [    0.544077] system 00:0a: iomem range 0xd5800-0xd7fff has been reserved     
    [    0.544079] system 00:0a: iomem range 0xf0000-0xf7fff could not be reserved 
    [    0.544081] system 00:0a: iomem range 0xf8000-0xfbfff could not be reserved 
    [    0.544083] system 00:0a: iomem range 0xfc000-0xfffff could not be reserved 
    [    0.544086] system 00:0a: iomem range 0x77ef0000-0x77efffff could not be reserved                                                                           
    [    0.544088] system 00:0a: iomem range 0xffff0000-0xffffffff could not be reserved                                                                           
    [    0.544090] system 00:0a: iomem range 0x0-0x9ffff could not be reserved     
    [    0.544092] system 00:0a: iomem range 0x100000-0x77eeffff could not be reserved                                                                             
    [    0.544094] system 00:0a: iomem range 0x77f00000-0x7fefffff could not be reserved                                                                           
    [    0.544096] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved                                                                           
    [    0.544099] system 00:0a: iomem range 0xfee00000-0xfeefffff could not be reserved                                                                           
    [    0.544101] system 00:0a: iomem range 0xfefff000-0xfeffffff could not be reserved                                                                           
    [    0.544103] system 00:0a: iomem range 0xfff80000-0xfff80fff could not be reserved                                                                           
    [    0.544105] system 00:0a: iomem range 0xfff90000-0xfffbffff could not be reserved                                                                           
    [    0.544108] system 00:0a: iomem range 0xfffed000-0xfffeffff could not be reserved                                                                           
    [    0.579028] pci 0000:00:10.0: PCI bridge, secondary bus 0000:01             
    [    0.579031] pci 0000:00:10.0:   IO window: 0xc000-0xcfff                    
    [    0.579034] pci 0000:00:10.0:   MEM window: 0xfdd00000-0xfddfffff           
    [    0.579037] pci 0000:00:10.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff                                                                          
    [    0.579046] pci 0000:00:10.0: setting latency timer to 64                   
    [    0.579048] bus: 00 index 0 io port: [0, ffff]                              
    [    0.579050] bus: 00 index 1 mmio: [0, ffffffff]                             
    [    0.579051] bus: 01 index 0 io port: [c000, cfff]                           
    [    0.579053] bus: 01 index 1 mmio: [fdd00000, fddfffff]                      
    [    0.579054] bus: 01 index 2 mmio: [fde00000, fdefffff]                      
    [    0.579056] bus: 01 index 3 io port: [0, ffff]                              
    [    0.579057] bus: 01 index 4 mmio: [0, ffffffff]                             
    [    0.579065] NET: Registered protocol family 2                               
    [    0.580047] Switched to high resolution mode on CPU 0

---

### Post by zoe-scutterbug on 2009-06-19
fixed...by upgrading distro 

i had gone back to intrepid after 2 or 3 bad jaunty installations, but this time it all  went good....except  my very favourite desktop environment, opengeu,  was  removed durring the auto upgrade and there is no jaunty release as yet.

Zoe

---

