---
title: "sound and video problems"
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by billybag on 2007-11-22
i have been having two problems for a while and every so often i enquire about it on here but with no responses.

the first problem is with video. ever since feisty fawn i have been having a problem in which every time i play a video,my whole screen gets fuzzy and i have to restart ubuntu to get out of it.

the second started when i updated to gutsy. the sound in firefox doesn't work. for flash videos like youtube. i have tried many many MANY 'solutions' and suggestion but none worked...maybe even made it worse. please help?

---

### Post by foxmulder881 on 2007-11-22
What mobo are you using?
And do you have your vid card drivers installed correctly?

---

### Post by billybag on 2007-11-27
i couldnt tell you.  i tied looking under my system specs but it is hard to distinguish one thing from the next. as far as i know my drivers are installed correctly. i mean... i have been using the same computer with ubuntcu ever since dapper and i have never had a problem until feisty with the fuzzy video and then gutsy with the flash

---

### Post by billybag on 2007-11-27
```

umame -a: Linux Waffle 2.6.22-14-386 #1 Sun Oct 14 22:36:54 GMT 2007 i686 GNU/Linux
lspci -nn: 00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller [1039:0646]
lspci -nn: 00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) [1039:0001]
lspci -nn: 00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] [1039:0962] (rev 04)
lspci -nn: 00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
lspci -nn: 00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513]
lspci -nn: 00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
lspci -nn: 00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
lspci -nn: 00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
lspci -nn: 00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f)
lspci -nn: 00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
lspci -nn: 00:09.0 Multimedia audio controller [0401]: C-Media Electronics Inc CM8738 [13f6:0111] (rev 10)
lspci -nn: 00:0a.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) [104c:8020]
lspci -nn: 00:0b.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50)
lspci -nn: 00:0b.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50)
lspci -nn: 00:0b.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 51)
lspci -nn: 00:0c.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
lspci -nn: 01:00.0 VGA compatible controller [0300]: S3 Inc. 86C410 Savage 2000 [5333:9102] (rev 02)
lspci -vnn: 00:00.0 Host bridge [0600]: Silicon Integrated Systems [SiS] SiS645DX Host & Memory & AGP Controller [1039:0646]
lspci -vnn: 	Flags: bus master, medium devsel, latency 32
lspci -vnn: 	Memory at e0000000 (32-bit, non-prefetchable) [size=64M]
lspci -vnn: 	Capabilities: [c0] AGP version 2.0
lspci -vnn: 
lspci -vnn: 00:01.0 PCI bridge [0604]: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) [1039:0001] (prog-if 00 [Normal decode])
lspci -vnn: 	Flags: bus master, fast devsel, latency 64
lspci -vnn: 	Bus: primary=00, secondary=01, subordinate=02, sec-latency=0
lspci -vnn: 	Memory behind bridge: c7c00000-dfefffff
lspci -vnn: 	Prefetchable memory behind bridge: bf900000-c7afffff
lspci -vnn: 
lspci -vnn: 00:02.0 ISA bridge [0601]: Silicon Integrated Systems [SiS] SiS962 [MuTIOL Media IO] [1039:0962] (rev 04)
lspci -vnn: 	Flags: bus master, medium devsel, latency 0
lspci -vnn: 
lspci -vnn: 00:02.1 SMBus [0c05]: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller [1039:0016]
lspci -vnn: 	Flags: medium devsel
lspci -vnn: 	I/O ports at 0c00 [size=32]
lspci -vnn: 
lspci -vnn: 00:02.5 IDE interface [0101]: Silicon Integrated Systems [SiS] 5513 [IDE] [1039:5513] (prog-if 80 [Master])
lspci -vnn: 	Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step) [1039:5513]
lspci -vnn: 	Flags: bus master, medium devsel, latency 128
lspci -vnn: 	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
lspci -vnn: 	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
lspci -vnn: 	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
lspci -vnn: 	[virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
lspci -vnn: 	I/O ports at ff00 [size=16]
lspci -vnn: 
lspci -vnn: 00:02.7 Multimedia audio controller [0401]: Silicon Integrated Systems [SiS] AC'97 Sound Controller [1039:7012] (rev a0)
lspci -vnn: 	Subsystem: Unknown device [a007:1019]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 11
lspci -vnn: 	I/O ports at dc00 [size=256]
lspci -vnn: 	I/O ports at d800 [size=128]
lspci -vnn: 	Capabilities: [48] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:03.0 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f) (prog-if 10 [OHCI])
lspci -vnn: 	Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 5
lspci -vnn: 	Memory at dfffd000 (32-bit, non-prefetchable) [size=4K]
lspci -vnn: 
lspci -vnn: 00:03.1 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f) (prog-if 10 [OHCI])
lspci -vnn: 	Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 11
lspci -vnn: 	Memory at dfffe000 (32-bit, non-prefetchable) [size=4K]
lspci -vnn: 
lspci -vnn: 00:03.2 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001] (rev 0f) (prog-if 10 [OHCI])
lspci -vnn: 	Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller [1039:7001]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 11
lspci -vnn: 	Memory at dffff000 (32-bit, non-prefetchable) [size=4K]
lspci -vnn: 
lspci -vnn: 00:03.3 USB Controller [0c03]: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002] (prog-if 20 [EHCI])
lspci -vnn: 	Subsystem: Silicon Integrated Systems [SiS] USB 2.0 Controller [1039:7002]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 11
lspci -vnn: 	Memory at dffdf000 (32-bit, non-prefetchable) [size=4K]
lspci -vnn: 	Capabilities: [50] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:09.0 Multimedia audio controller [0401]: C-Media Electronics Inc CM8738 [13f6:0111] (rev 10)
lspci -vnn: 	Subsystem: C-Media Electronics Inc CMI8738/C3DX PCI Audio Device [13f6:0111]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 11
lspci -vnn: 	I/O ports at d400 [size=256]
lspci -vnn: 	Capabilities: [c0] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:0a.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB12LV26 IEEE-1394 Controller (Link) [104c:8020] (prog-if 10 [OHCI])
lspci -vnn: 	Subsystem: VISIONTEK Unknown device [1545:0401]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 11
lspci -vnn: 	Memory at dfff8800 (32-bit, non-prefetchable) [size=2K]
lspci -vnn: 	Memory at dfff4000 (32-bit, non-prefetchable) [size=16K]
lspci -vnn: 	Capabilities: [44] Power Management version 1
lspci -vnn: 
lspci -vnn: 00:0b.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50) (prog-if 00 [UHCI])
lspci -vnn: 	Subsystem: First International Computer, Inc. VA-502 Mainboard [0925:1234]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 5
lspci -vnn: 	I/O ports at cc00 [size=32]
lspci -vnn: 	Capabilities: [80] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:0b.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50) (prog-if 00 [UHCI])
lspci -vnn: 	Subsystem: First International Computer, Inc. VA-502 Mainboard [0925:1234]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 5
lspci -vnn: 	I/O ports at d000 [size=32]
lspci -vnn: 	Capabilities: [80] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:0b.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 51) (prog-if 20 [EHCI])
lspci -vnn: 	Subsystem: First International Computer, Inc. Unknown device [0925:1234]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 11
lspci -vnn: 	Memory at dfffcf00 (32-bit, non-prefetchable) [size=256]
lspci -vnn: 	Capabilities: [80] Power Management version 2
lspci -vnn: 
lspci -vnn: 00:0c.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
lspci -vnn: 	Subsystem: Realtek Semiconductor Co., Ltd. RT8139 [10ec:8139]
lspci -vnn: 	Flags: bus master, medium devsel, latency 64, IRQ 5
lspci -vnn: 	I/O ports at c800 [size=256]
lspci -vnn: 	Memory at dfffce00 (32-bit, non-prefetchable) [size=256]
lspci -vnn: 	Expansion ROM at dffc0000 [disabled] [size=64K]
lspci -vnn: 	Capabilities: [50] Power Management version 2
lspci -vnn: 
lspci -vnn: 01:00.0 VGA compatible controller [0300]: S3 Inc. 86C410 Savage 2000 [5333:9102] (rev 02) (prog-if 00 [VGA])
lspci -vnn: 	Subsystem: S3 Inc. 86C410 Savage 2000 [5333:9102]
lspci -vnn: 	Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 5
lspci -vnn: 	Memory at dfe80000 (32-bit, non-prefetchable) [size=512K]
lspci -vnn: 	Memory at c0000000 (32-bit, prefetchable) [size=64M]
lspci -vnn: 	Memory at d8000000 (32-bit, non-prefetchable) [size=64M]
lspci -vnn: 	Memory at d4000000 (32-bit, non-prefetchable) [size=64M]
lspci -vnn: 	Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
lspci -vnn: 	Expansion ROM at dfe70000 [disabled] [size=64K]
lspci -vnn: 	Capabilities: [dc] Power Management version 1
lspci -vnn: 	Capabilities: [80] AGP version 2.0
lspci -vnn: 
modulemap: 1039:0646 sis_agp
modulemap: 1039:0016 i2c_sis96x
modulemap: 1039:5513 pata_sis
modulemap: 1039:7012 snd_intel8x0
modulemap: 1039:7001 ohci_hcd
modulemap: 1039:7001 ohci_hcd
modulemap: 1039:7001 ohci_hcd
modulemap: 1039:7002 ehci_hcd
modulemap: 13f6:0111 snd_cmipci
modulemap: 104c:8020 ohci1394
modulemap: 1106:3038 uhci_hcd
modulemap: 1106:3038 uhci_hcd
modulemap: 1106:3104 ehci_hcd
modulemap: 10ec:8139 8139too
modulemap: 5333:9102 i2c_savage4
lsmod: Module                  Size  Used by
lsmod: lp                     11460  0 
lsmod: parport_pc             36132  1 
lsmod: joydev                 10432  0 
lsmod: st                     39068  0 
lsmod: ipv6                  257700  8 
lsmod: xt_limit                2688  8 
lsmod: xt_tcpudp               3328  7 
lsmod: ipt_LOG                 6400  8 
lsmod: ipt_MASQUERADE          3456  0 
lsmod: ipt_TOS                 2304  0 
lsmod: ipt_REJECT              4736  5 
lsmod: nf_conntrack_irc        7192  0 
lsmod: nf_conntrack_ftp        9856  0 
lsmod: xt_state                2560  6 
lsmod: snd_rtctimer            3744  1 
lsmod: af_packet              21896  2 
lsmod: binfmt_misc            11400  1 
lsmod: rfcomm                 38684  2 
lsmod: l2cap                  22788  11 rfcomm
lsmod: bluetooth              52324  4 rfcomm,l2cap
lsmod: ppdev                   9348  0 
lsmod: speedstep_lib           5380  0 
lsmod: cpufreq_userspace       4116  0 
lsmod: cpufreq_stats           5508  0 
lsmod: cpufreq_powersave       1792  0 
lsmod: cpufreq_ondemand        8084  0 
lsmod: freq_table              4740  2 cpufreq_stats,cpufreq_ondemand
lsmod: cpufreq_conservative     6560  0 
lsmod: video                  17164  0 
lsmod: sbs                    18568  0 
lsmod: button                  8080  0 
lsmod: dock                    9476  0 
lsmod: container               4608  0 
lsmod: ac                      5252  0 
lsmod: battery                10116  0 
lsmod: sbp2                   23304  0 
lsmod: ide_generic             1280  0 [permanent]
lsmod: ide_disk               17408  0 
lsmod: ide_cd                 31776  0 
lsmod: ide_core              114772  3 ide_generic,ide_disk,ide_cd
lsmod: snd_cmipci             35872  1 
lsmod: snd_opl3_lib           11264  1 snd_cmipci
lsmod: snd_hwdep               9604  1 snd_opl3_lib
lsmod: snd_seq_dummy           4100  0 
lsmod: snd_seq_oss            33920  0 
lsmod: snd_intel8x0           34076  2 
lsmod: snd_ac97_codec        100132  1 snd_intel8x0
lsmod: ac97_bus                2432  1 snd_ac97_codec
lsmod: snd_pcm_oss            43392  0 
lsmod: snd_mixer_oss          16896  1 snd_pcm_oss
lsmod: snd_seq_midi            8832  0 
lsmod: snd_seq_midi_event      7808  2 snd_seq_oss,snd_seq_midi
lsmod: snd_mpu401              9128  0 
lsmod: snd_mpu401_uart         8960  2 snd_cmipci,snd_mpu401
lsmod: snd_pcm                77960  6 snd_cmipci,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
lsmod: snd_seq                51440  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lsmod: snd_timer              23044  4 snd_rtctimer,snd_opl3_lib,snd_pcm,snd_seq
lsmod: snd_rawmidi            25088  2 snd_seq_midi,snd_mpu401_uart
lsmod: snd_seq_device          8844  6 snd_opl3_lib,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
lsmod: analog                 12192  0 
lsmod: gameport               15240  2 snd_cmipci,analog
lsmod: parport                35656  3 lp,parport_pc,ppdev
lsmod: rtc                    13208  1 snd_rtctimer
lsmod: pcspkr                  3072  0 
lsmod: psmouse                38672  0 
lsmod: serio_raw               7044  0 
lsmod: snd                    54148  22 snd_rtctimer,snd_cmipci,snd_opl3_lib,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_pcm,snd_seq,snd_timer,snd_rawmidi,snd_seq_device
lsmod: soundcore               7520  1 snd
lsmod: i2c_savage4             3844  0 
lsmod: i2c_algo_bit            6532  1 i2c_savage4
lsmod: i2c_sis96x              5380  0 
lsmod: i2c_core               25104  3 i2c_savage4,i2c_algo_bit,i2c_sis96x
lsmod: snd_page_alloc         10376  2 snd_intel8x0,snd_pcm
lsmod: sis_agp                 9220  1 
lsmod: agpgart                33584  1 sis_agp
lsmod: shpchp                 33556  0 
lsmod: pci_hotplug            31288  1 shpchp
lsmod: evdev                  10240  4 
lsmod: iptable_nat             7812  0 
lsmod: nf_nat                 18476  2 ipt_MASQUERADE,iptable_nat
lsmod: nf_conntrack_ipv4      18060  8 iptable_nat
lsmod: nf_conntrack           62424  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
lsmod: nfnetlink               6040  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
lsmod: iptable_mangle          2944  0 
lsmod: iptable_filter          3072  1 
lsmod: ip_tables              12232  3 iptable_nat,iptable_mangle,iptable_filter
lsmod: x_tables               14980  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
lsmod: 8139too                26112  0 
lsmod: ext3                  129928  1 
lsmod: jbd                    53416  1 ext3
lsmod: mbcache                 8324  1 ext3
lsmod: sg                     36124  0 
lsmod: sr_mod                 16548  0 
lsmod: cdrom                  36512  2 ide_cd,sr_mod
lsmod: sd_mod                 29200  5 
lsmod: floppy                 58500  0 
lsmod: 8139cp                 23680  0 
lsmod: mii                     5632  2 8139too,8139cp
lsmod: ehci_hcd               35084  0 
lsmod: uhci_hcd               25232  0 
lsmod: ohci1394               35760  0 
lsmod: ieee1394               94904  2 sbp2,ohci1394
lsmod: ohci_hcd               21764  0 
lsmod: usbcore               136088  4 ehci_hcd,uhci_hcd,ohci_hcd
lsmod: pata_sis               14212  3 
lsmod: ata_generic             7556  0 
lsmod: libata                125040  2 pata_sis,ata_generic
lsmod: scsi_mod              146828  6 st,sbp2,sg,sr_mod,sd_mod,libata
lsmod: raid10                 24960  0 
lsmod: raid456               124944  0 
lsmod: xor                    16008  1 raid456
lsmod: raid1                  24320  0 
lsmod: raid0                   8704  0 
lsmod: multipath               8832  0 
lsmod: linear                  6528  0 
lsmod: md_mod                 79636  7 raid10,raid456,raid1,raid0,multipath,linear
lsmod: dm_mirror              22400  0 
lsmod: dm_snapshot            17952  0 
lsmod: dm_mod                 56768  2 dm_mirror,dm_snapshot
lsmod: thermal                13448  0 
lsmod: processor              23984  1 thermal
lsmod: fan                     4868  0 
lsmod: fuse                   44948  3 
lsmod: apparmor               38812  0 
lsmod: commoncap               7424  1 apparmor
df: Filesystem           1K-blocks      Used Available Use% Mounted on
df: /dev/sdb1             78052616  49393120  24694656  67% /
df: varrun                  128108       100    128008   1% /var/run
df: varlock                 128108         0    128108   0% /var/lock
df: udev                    128108        92    128016   1% /dev
df: devshm                  128108         0    128108   0% /dev/shm
df: lrm                     128108     35324     92784  28% /lib/modules/2.6.22-14-386/volatile
df: /dev/sda1             78140128  74781136   3358992  96% /media/named
free:              total       used       free     shared    buffers     cached
free: Mem:        256216     229148      27068          0       3352     112592
free: -/+ buffers/cache:     113204     143012
free: Swap:       738948     176268     562680
cardctl status: /usr/bin/report-hw: 50: cardctl: not found
cardctl ident: /usr/bin/report-hw: 51: cardctl: not found
/proc/cpuinfo: processor	: 0
/proc/cpuinfo: vendor_id	: GenuineIntel
/proc/cpuinfo: cpu family	: 15
/proc/cpuinfo: model		: 1
/proc/cpuinfo: model name	: Intel(R) Celeron(R) CPU 1.70GHz
/proc/cpuinfo: stepping	: 3
/proc/cpuinfo: cpu MHz		: 1693.201
/proc/cpuinfo: cache size	: 128 KB
/proc/cpuinfo: fdiv_bug	: no
/proc/cpuinfo: hlt_bug		: no
/proc/cpuinfo: f00f_bug	: no
/proc/cpuinfo: coma_bug	: no
/proc/cpuinfo: fpu		: yes
/proc/cpuinfo: fpu_exception	: yes
/proc/cpuinfo: cpuid level	: 2
/proc/cpuinfo: wp		: yes
/proc/cpuinfo: flags		: fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm
/proc/cpuinfo: bogomips	: 3389.17
/proc/cpuinfo: clflush size	: 64
/proc/cpuinfo: 
/proc/ioports: 0000-001f : dma1
/proc/ioports: 0020-0021 : pic1
/proc/ioports: 0040-0043 : timer0
/proc/ioports: 0050-0053 : timer1
/proc/ioports: 0060-006f : keyboard
/proc/ioports: 0070-0077 : rtc
/proc/ioports: 0080-008f : dma page reg
/proc/ioports: 00a0-00a1 : pic2
/proc/ioports: 00c0-00df : dma2
/proc/ioports: 00f0-00ff : fpu
/proc/ioports: 0170-0177 : 0000:00:02.5
/proc/ioports:   0170-0177 : libata
/proc/ioports: 01f0-01f7 : 0000:00:02.5
/proc/ioports:   01f0-01f7 : libata
/proc/ioports: 02f8-02ff : serial
/proc/ioports: 0300-0301 : MPU401 UART
/proc/ioports: 0330-0331 : MPU401 UART
/proc/ioports: 0376-0376 : 0000:00:02.5
/proc/ioports:   0376-0376 : libata
/proc/ioports: 0378-037a : parport0
/proc/ioports: 03c0-03df : vga+
/proc/ioports: 03f2-03f5 : floppy
/proc/ioports: 03f6-03f6 : 0000:00:02.5
/proc/ioports:   03f6-03f6 : libata
/proc/ioports: 03f7-03f7 : floppy DIR
/proc/ioports: 03f8-03ff : serial
/proc/ioports: 0778-077a : parport0
/proc/ioports: 0800-0803 : ACPI PM1a_EVT_BLK
/proc/ioports: 0804-0805 : ACPI PM1a_CNT_BLK
/proc/ioports: 0808-080b : ACPI PM_TMR
/proc/ioports: 0816-0816 : ACPI PM2_CNT_BLK
/proc/ioports: 0820-0823 : ACPI GPE0_BLK
/proc/ioports: 0830-0833 : ACPI GPE1_BLK
/proc/ioports: 0c00-0c1f : 0000:00:02.1
/proc/ioports:   0c00-0c1f : sis96x_smbus
/proc/ioports: 0cf8-0cff : PCI conf1
/proc/ioports: c800-c8ff : 0000:00:0c.0
/proc/ioports:   c800-c8ff : 8139too
/proc/ioports: cc00-cc1f : 0000:00:0b.0
/proc/ioports:   cc00-cc1f : uhci_hcd
/proc/ioports: d000-d01f : 0000:00:0b.1
/proc/ioports:   d000-d01f : uhci_hcd
/proc/ioports: d400-d4ff : 0000:00:09.0
/proc/ioports:   d400-d4ff : CMI8738-MC6
/proc/ioports: d800-d87f : 0000:00:02.7
/proc/ioports:   d800-d87f : SiS SI7012
/proc/ioports: dc00-dcff : 0000:00:02.7
/proc/ioports:   dc00-dcff : SiS SI7012
/proc/ioports: ff00-ff0f : 0000:00:02.5
/proc/ioports:   ff00-ff0f : libata
/proc/iomem: 00000000-0009fbff : System RAM
/proc/iomem:   00000000-00000000 : Crash kernel
/proc/iomem: 0009fc00-0009ffff : reserved
/proc/iomem: 000a0000-000bffff : Video RAM area
/proc/iomem: 000c0000-000cafff : Video ROM
/proc/iomem: 000f0000-000fffff : System ROM
/proc/iomem: 00100000-0ffeffff : System RAM
/proc/iomem:   00100000-002e25d4 : Kernel code
/proc/iomem:   002e25d5-003bda03 : Kernel data
/proc/iomem: 0fff0000-0fff7fff : ACPI Tables
/proc/iomem: 0fff8000-0fffffff : ACPI Non-volatile Storage
/proc/iomem: bf900000-c7afffff : PCI Bus #01
/proc/iomem:   c0000000-c3ffffff : 0000:01:00.0
/proc/iomem: c7c00000-dfefffff : PCI Bus #01
/proc/iomem:   d0000000-d3ffffff : 0000:01:00.0
/proc/iomem:   d4000000-d7ffffff : 0000:01:00.0
/proc/iomem:   d8000000-dbffffff : 0000:01:00.0
/proc/iomem:   dfe70000-dfe7ffff : 0000:01:00.0
/proc/iomem:   dfe80000-dfefffff : 0000:01:00.0
/proc/iomem: dffc0000-dffcffff : 0000:00:0c.0
/proc/iomem: dffdf000-dffdffff : 0000:00:03.3
/proc/iomem:   dffdf000-dffdffff : ehci_hcd
/proc/iomem: dfff4000-dfff7fff : 0000:00:0a.0
/proc/iomem: dfff8800-dfff8fff : 0000:00:0a.0
/proc/iomem:   dfff8800-dfff8fff : ohci1394
/proc/iomem: dfffce00-dfffceff : 0000:00:0c.0
/proc/iomem:   dfffce00-dfffceff : 8139too
/proc/iomem: dfffcf00-dfffcfff : 0000:00:0b.2
/proc/iomem:   dfffcf00-dfffcfff : ehci_hcd
/proc/iomem: dfffd000-dfffdfff : 0000:00:03.0
/proc/iomem:   dfffd000-dfffdfff : ohci_hcd
/proc/iomem: dfffe000-dfffefff : 0000:00:03.1
/proc/iomem:   dfffe000-dfffefff : ohci_hcd
/proc/iomem: dffff000-dfffffff : 0000:00:03.2
/proc/iomem:   dffff000-dfffffff : ohci_hcd
/proc/iomem: e0000000-e3ffffff : 0000:00:00.0
/proc/iomem: ffee0000-fff0fffe : reserved
/proc/iomem: fffc0000-ffffffff : reserved
/proc/interrupts:            CPU0       
/proc/interrupts:   0:    5880418    XT-PIC-XT        timer
/proc/interrupts:   1:       2191    XT-PIC-XT        i8042
/proc/interrupts:   2:          0    XT-PIC-XT        cascade
/proc/interrupts:   5:     161808    XT-PIC-XT        ohci_hcd:usb1, uhci_hcd:usb4, uhci_hcd:usb5, eth0
/proc/interrupts:   6:          5    XT-PIC-XT        floppy
/proc/interrupts:   7:          5    XT-PIC-XT        parport0
/proc/interrupts:   8:          2    XT-PIC-XT        rtc
/proc/interrupts:   9:          1    XT-PIC-XT        acpi
/proc/interrupts:  10:          0    XT-PIC-XT        MPU401 UART
/proc/interrupts:  11:      40597    XT-PIC-XT        ohci_hcd:usb2, ohci_hcd:usb3, ohci1394, ehci_hcd:usb6, ehci_hcd:usb7, SiS SI7012, CMI8738-MC6
/proc/interrupts:  12:     453428    XT-PIC-XT        i8042
/proc/interrupts:  14:     468484    XT-PIC-XT        libata
/proc/interrupts:  15:     452780    XT-PIC-XT        libata
/proc/interrupts: NMI:          0 
/proc/interrupts: LOC:          0 
/proc/interrupts: ERR:          0
/proc/interrupts: MIS:          0
/proc/meminfo: MemTotal:       256216 kB
/proc/meminfo: MemFree:         26956 kB
/proc/meminfo: Buffers:          3380 kB
/proc/meminfo: Cached:         112720 kB
/proc/meminfo: SwapCached:      24360 kB
/proc/meminfo: Active:         135276 kB
/proc/meminfo: Inactive:        67952 kB
/proc/meminfo: HighTotal:           0 kB
/proc/meminfo: HighFree:            0 kB
/proc/meminfo: LowTotal:       256216 kB
/proc/meminfo: LowFree:         26956 kB
/proc/meminfo: SwapTotal:      738948 kB
/proc/meminfo: SwapFree:       562680 kB
/proc/meminfo: Dirty:            8336 kB
/proc/meminfo: Writeback:           0 kB
/proc/meminfo: AnonPages:       79448 kB
/proc/meminfo: Mapped:          21996 kB
/proc/meminfo: Slab:            15896 kB
/proc/meminfo: SReclaimable:     8472 kB
/proc/meminfo: SUnreclaim:       7424 kB
/proc/meminfo: PageTables:       2200 kB
/proc/meminfo: NFS_Unstable:        0 kB
/proc/meminfo: Bounce:              0 kB
/proc/meminfo: CommitLimit:    867056 kB
/proc/meminfo: Committed_AS:   587900 kB
/proc/meminfo: VmallocTotal:   770040 kB
/proc/meminfo: VmallocUsed:      5360 kB
/proc/meminfo: VmallocChunk:   764360 kB
/proc/bus/input/devices: I: Bus=0017 Vendor=0001 Product=0001 Version=0100
/proc/bus/input/devices: N: Name="Macintosh mouse button emulation"
/proc/bus/input/devices: P: Phys=
/proc/bus/input/devices: S: Sysfs=/class/input/input0
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=mouse0 event0 
/proc/bus/input/devices: B: EV=7
/proc/bus/input/devices: B: KEY=70000 0 0 0 0 0 0 0 0
/proc/bus/input/devices: B: REL=3
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
/proc/bus/input/devices: N: Name="AT Translated Set 2 keyboard"
/proc/bus/input/devices: P: Phys=isa0060/serio0/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input1
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event1 
/proc/bus/input/devices: B: EV=120013
/proc/bus/input/devices: B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
/proc/bus/input/devices: B: MSC=10
/proc/bus/input/devices: B: LED=7
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0010 Vendor=001f Product=0001 Version=0100
/proc/bus/input/devices: N: Name="PC Speaker"
/proc/bus/input/devices: P: Phys=isa0061/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input2
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event2 
/proc/bus/input/devices: B: EV=40001
/proc/bus/input/devices: B: SND=6
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0011 Vendor=0002 Product=0006 Version=0056
/proc/bus/input/devices: N: Name="ImExPS/2 Logitech Wheel Mouse"
/proc/bus/input/devices: P: Phys=isa0060/serio1/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input3
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=mouse1 event3 
/proc/bus/input/devices: B: EV=7
/proc/bus/input/devices: B: KEY=1f0000 0 0 0 0 0 0 0 0
/proc/bus/input/devices: B: REL=143
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0002 Version=0000
/proc/bus/input/devices: N: Name="Power Button (FF)"
/proc/bus/input/devices: P: Phys=button_power/button/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input4
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event4 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=100000 0 0 0
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0001 Version=0000
/proc/bus/input/devices: N: Name="Power Button (CM)"
/proc/bus/input/devices: P: Phys=PNP0C0C/button/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input5
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event5 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=100000 0 0 0
/proc/bus/input/devices: 
/proc/bus/input/devices: I: Bus=0019 Vendor=0000 Product=0003 Version=0000
/proc/bus/input/devices: N: Name="Sleep Button (CM)"
/proc/bus/input/devices: P: Phys=PNP0C0E/button/input0
/proc/bus/input/devices: S: Sysfs=/class/input/input6
/proc/bus/input/devices: U: Uniq=
/proc/bus/input/devices: H: Handlers=kbd event6 
/proc/bus/input/devices: B: EV=3
/proc/bus/input/devices: B: KEY=4000 0 0 0 0
/proc/bus/input/devices: 
dmidecode: # dmidecode 2.9
dmidecode: SMBIOS 2.3 present.
dmidecode: 24 structures occupying 857 bytes.
dmidecode: Table at 0x000F0630.
dmidecode: 
dmidecode: Handle 0x0000, DMI type 0, 20 bytes
dmidecode: BIOS Information
dmidecode: 	Vendor: American Megatrends Inc.
dmidecode: 	Version: 07.00T
dmidecode: 	Release Date: 04/02/01
dmidecode: 	Address: 0xF0000
dmidecode: 	Runtime Size: 64 kB
dmidecode: 	ROM Size: 256 kB
dmidecode: 	Characteristics:
dmidecode: 		ISA is supported
dmidecode: 		PCI is supported
dmidecode: 		PNP is supported
dmidecode: 		APM is supported
dmidecode: 		BIOS is upgradeable
dmidecode: 		BIOS shadowing is allowed
dmidecode: 		ESCD support is available
dmidecode: 		Boot from CD is supported
dmidecode: 		Selectable boot is supported
dmidecode: 		BIOS ROM is socketed
dmidecode: 		EDD is supported
dmidecode: 		5.25"/360 KB floppy services are supported (int 13h)
dmidecode: 		5.25"/1.2 MB floppy services are supported (int 13h)
dmidecode: 		3.5"/720 KB floppy services are supported (int 13h)
dmidecode: 		3.5"/2.88 MB floppy services are supported (int 13h)
dmidecode: 		Print screen service is supported (int 5h)
dmidecode: 		8042 keyboard services are supported (int 9h)
dmidecode: 		Printer services are supported (int 17h)
dmidecode: 		CGA/mono video services are supported (int 10h)
dmidecode: 		ACPI is supported
dmidecode: 		USB legacy is supported
dmidecode: 		AGP is supported
dmidecode: 		LS-120 boot is supported
dmidecode: 		ATAPI Zip drive boot is supported
dmidecode: 		BIOS boot specification is supported
dmidecode: 
dmidecode: Handle 0x0001, DMI type 1, 25 bytes
dmidecode: System Information
dmidecode: 	Manufacturer: Matsonic
dmidecode: 	Product Name: MS9307C+
dmidecode: 	Version: 1.0
dmidecode: 	Serial Number: 00000000
dmidecode: 	UUID: Not Settable
dmidecode: 	Wake-up Type: Modem Ring
dmidecode: 
dmidecode: Handle 0x0002, DMI type 2, 8 bytes
dmidecode: Base Board Information
dmidecode: 	Manufacturer: Matsonic
dmidecode: 	Product Name: MS9307C+
dmidecode: 	Version: 1.0
dmidecode: 	Serial Number: 00000000
dmidecode: 
dmidecode: Handle 0x0003, DMI type 3, 17 bytes
dmidecode: Chassis Information
dmidecode: 	Manufacturer: Matsonic
dmidecode: 	Type: Desktop
dmidecode: 	Lock: Not Present
dmidecode: 	Version: 1.0
dmidecode: 	Serial Number: 00000000
dmidecode: 	Asset Tag: 0123ABC
dmidecode: 	Boot-up State: Unknown
dmidecode: 	Power Supply State: Unknown
dmidecode: 	Thermal State: Unknown
dmidecode: 	Security Status: Unknown
dmidecode: 	OEM Information: 0x00000000
dmidecode: 
dmidecode: Handle 0x0004, DMI type 4, 32 bytes
dmidecode: Processor Information
dmidecode: 	Socket Designation: Slot-1
dmidecode: 	Type: Central Processor
dmidecode: 	Family: Celeron
dmidecode: 	Manufacturer: Intel                                           
dmidecode: 	ID: 13 0F 00 00 55 00 00 00
dmidecode: 	Signature: Type 0, Family 15, Model 1, Stepping 3
dmidecode: 	Flags:
dmidecode: 		FPU (Floating-point unit on-chip)
dmidecode: 		DE (Debugging extension)
dmidecode: 		TSC (Time stamp counter)
dmidecode: 		PAE (Physical address extension)
dmidecode: 	Version: Intel(R) Pentium(R) 4 Processor                 
dmidecode: 	Voltage: 3.3 V 2.9 V
dmidecode: 	External Clock: 100 MHz
dmidecode: 	Max Speed: 300 MHz
dmidecode: 	Current Speed: 1700 MHz
dmidecode: 	Status: Populated, Enabled
dmidecode: 	Upgrade: Slot 1
dmidecode: 	L1 Cache Handle: 0x0005
dmidecode: 	L2 Cache Handle: 0x0006
dmidecode: 	L3 Cache Handle: Not Provided
dmidecode: 
dmidecode: Handle 0x0005, DMI type 7, 19 bytes
dmidecode: Cache Information
dmidecode: 	Socket Designation: Internal Cache
dmidecode: 	Configuration: Enabled, Not Socketed, Level 1
dmidecode: 	Operational Mode: Write Back
dmidecode: 	Location: Internal
dmidecode: 	Installed Size: 8 KB
dmidecode: 	Maximum Size: 1024 KB
dmidecode: 	Supported SRAM Types:
dmidecode: 		Synchronous
dmidecode: 	Installed SRAM Type: Pipeline Burst Synchronous
dmidecode: 	Speed: 40 ns
dmidecode: 	Error Correction Type: Single-bit ECC
dmidecode: 	System Type: Data
dmidecode: 	Associativity: 4-way Set-associative
dmidecode: 
dmidecode: Handle 0x0006, DMI type 7, 19 bytes
dmidecode: Cache Information
dmidecode: 	Socket Designation: Internal Cache
dmidecode: 	Configuration: Enabled, Not Socketed, Level 2
dmidecode: 	Operational Mode: Write Back
dmidecode: 	Location: Internal
dmidecode: 	Installed Size: 128 KB
dmidecode: 	Maximum Size: 1024 KB
dmidecode: 	Supported SRAM Types:
dmidecode: 		Synchronous
dmidecode: 	Installed SRAM Type: Synchronous
dmidecode: 	Speed: 40 ns
dmidecode: 	Error Correction Type: Parity
dmidecode: 	System Type: Unified
dmidecode: 	Associativity: Other
dmidecode: 
dmidecode: Handle 0x0007, DMI type 5, 24 bytes
dmidecode: Memory Controller Information
dmidecode: 	Error Detecting Method: 32-bit ECC
dmidecode: 	Error Correcting Capabilities:
dmidecode: 		Single-bit Error Correcting
dmidecode: 	Supported Interleave: One-way Interleave
dmidecode: 	Current Interleave: One-way Interleave
dmidecode: 	Maximum Memory Module Size: 128 MB
dmidecode: 	Maximum Total Memory Size: 512 MB
dmidecode: 	Supported Speeds:
dmidecode: 		70 ns
dmidecode: 		60 ns
dmidecode: 	Supported Memory Types:
dmidecode: 		Standard
dmidecode: 		FPM
dmidecode: 		EDO
dmidecode: 		Parity
dmidecode: 		ECC
dmidecode: 		SIMM
dmidecode: 	Memory Module Voltage: 3.3 V
dmidecode: 	Associated Memory Slots: 4
dmidecode: 		0x0008
dmidecode: 		0x0009
dmidecode: 		0x000A
dmidecode: 		0x000B
dmidecode: 	Enabled Error Correcting Capabilities:
dmidecode: 		Single-bit Error Correcting
dmidecode: 
dmidecode: Handle 0x0008, DMI type 6, 12 bytes
dmidecode: Memory Module Information
dmidecode: 	Socket Designation: ROW-0
dmidecode: 	Bank Connections: 4 11
dmidecode: 	Current Speed: Unknown
dmidecode: 	Type: DIMM SDRAM
dmidecode: 	Installed Size: 256 MB (Single-bank Connection)
dmidecode: 	Enabled Size: 256 MB (Single-bank Connection)
dmidecode: 	Error Status: OK
dmidecode: 
dmidecode: Handle 0x0009, DMI type 6, 12 bytes
dmidecode: Memory Module Information
dmidecode: 	Socket Designation: ROW-1
dmidecode: 	Bank Connections: 0 0
dmidecode: 	Current Speed: Unknown
dmidecode: 	Type: Unknown
dmidecode: 	Installed Size: Not Installed
dmidecode: 	Enabled Size: Not Installed
dmidecode: 	Error Status: OK
dmidecode: 
dmidecode: Handle 0x000A, DMI type 6, 12 bytes
dmidecode: Memory Module Information
dmidecode: 	Socket Designation: ROW-2
dmidecode: 	Bank Connections: 0 0
dmidecode: 	Current Speed: Unknown
dmidecode: 	Type: Unknown
dmidecode: 	Installed Size: Not Installed
dmidecode: 	Enabled Size: Not Installed
dmidecode: 	Error Status: OK
dmidecode: 
dmidecode: Handle 0x000B, DMI type 6, 12 bytes
dmidecode: Memory Module Information
dmidecode: 	Socket Designation: ROW-3
dmidecode: 	Bank Connections: 0 0
dmidecode: 	Current Speed: Unknown
dmidecode: 	Type: Unknown
dmidecode: 	Installed Size: Not Installed
dmidecode: 	Enabled Size: Not Installed
dmidecode: 	Error Status: OK
dmidecode: 
dmidecode: Handle 0x000C, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI1
dmidecode: 	Type: 32-bit PCI
dmidecode: 	Current Usage: Available
dmidecode: 	Length: Long
dmidecode: 	ID: 1
dmidecode: 	Characteristics:
dmidecode: 		3.3 V is provided
dmidecode: 		Opening is shared
dmidecode: 		PME signal is supported
dmidecode: 
dmidecode: Handle 0x000D, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI2
dmidecode: 	Type: 32-bit PCI
dmidecode: 	Current Usage: In Use
dmidecode: 	Length: Long
dmidecode: 	ID: 2
dmidecode: 	Characteristics:
dmidecode: 		3.3 V is provided
dmidecode: 		Opening is shared
dmidecode: 		PME signal is supported
dmidecode: 
dmidecode: Handle 0x000E, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI3
dmidecode: 	Type: 32-bit PCI
dmidecode: 	Current Usage: In Use
dmidecode: 	Length: Long
dmidecode: 	ID: 3
dmidecode: 	Characteristics:
dmidecode: 		3.3 V is provided
dmidecode: 		Opening is shared
dmidecode: 		PME signal is supported
dmidecode: 
dmidecode: Handle 0x000F, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI4
dmidecode: 	Type: 32-bit PCI
dmidecode: 	Current Usage: In Use
dmidecode: 	Length: Long
dmidecode: 	ID: 4
dmidecode: 	Characteristics:
dmidecode: 		3.3 V is provided
dmidecode: 		Opening is shared
dmidecode: 		PME signal is supported
dmidecode: 
dmidecode: Handle 0x0010, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: PCI5
dmidecode: 	Type: 32-bit PCI
dmidecode: 	Current Usage: In Use
dmidecode: 	Length: Long
dmidecode: 	ID: 5
dmidecode: 	Characteristics:
dmidecode: 		3.3 V is provided
dmidecode: 		Opening is shared
dmidecode: 		PME signal is supported
dmidecode: 
dmidecode: Handle 0x0011, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: ISA1
dmidecode: 	Type: 16-bit ISA
dmidecode: 	Current Usage: Unknown
dmidecode: 	Length: Long
dmidecode: 	Characteristics:
dmidecode: 		3.3 V is provided
dmidecode: 		Opening is shared
dmidecode: 		PME signal is supported
dmidecode: 
dmidecode: Handle 0x0012, DMI type 9, 13 bytes
dmidecode: System Slot Information
dmidecode: 	Designation: ISA2
dmidecode: 	Type: 16-bit ISA
dmidecode: 	Current Usage: Unknown
dmidecode: 	Length: Long
dmidecode: 	Characteristics:
dmidecode: 		3.3 V is provided
dmidecode: 		Opening is shared
dmidecode: 		PME signal is supported
dmidecode: 
dmidecode: Handle 0x0013, DMI type 11, 5 bytes
dmidecode: OEM Strings
dmidecode: 	String 1: SMBIOS Support from AMI
dmidecode: 	String 2: Tested by James
dmidecode: 
dmidecode: Handle 0x0014, DMI type 8, 9 bytes
dmidecode: Port Connector Information
dmidecode: 	Internal Reference Designator: USB
dmidecode: 	Internal Connector Type: Mini Centronics
dmidecode: 	External Reference Designator: Def
dmidecode: 	External Connector Type: DB-25 male
dmidecode: 	Port Type: SSA SCSI
dmidecode: 
dmidecode: Handle 0x0015, DMI type 12, 5 bytes
dmidecode: System Configuration Options
dmidecode: 	Option 1: System Management BIOS from Atlanta
dmidecode: 	Option 2: SMBIOS from AMI
dmidecode: 
dmidecode: Handle 0x0016, DMI type 13, 22 bytes
dmidecode: BIOS Language Information
dmidecode: 	Installable Languages: 4
dmidecode: 		English
dmidecode: 		Traditional Chinese
dmidecode: 		Simplified Chinese
dmidecode: 		Japanese
dmidecode: 	Currently Installed Language: English
dmidecode: 
dmidecode: Handle 0x0017, DMI type 127, 4 bytes
dmidecode: End Of Table
dmidecode: 

```

---

