---
title: "No Network Connection"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2010-05-03
Problem- no wireless or ethernet connection.    I just upgraded to 10.04.  I had wireless connection for 1 day and now nothing.  No ethernet connection either.  I CAN use both wireless and ethernet using my machine on Windows.....so the connection stuff does work.  Here's the output of of the commands I got from the &quot;sticky&quot;.     I can't display the output as this forum puts it all together as one continuous sentence with no line break!

---

### Post by PDA1 on 2010-05-03
Problem- no wireless or ethernet connection.    I just upgraded to 10.04.  I had wireless connection for 1 day and now nothing.  No ethernet connection either.  I CAN use both wireless and ethernet using my machine on Windows.....so the connection stuff does work.  Here's the output of of the commands I got from the &amp;quot;sticky&amp;quot;.


1-  Machine Brand and Model 

Gateway- laptop 
Model- MX6453
 
2. Wireless Brand, Model and Wireless Chipset

earl@earl-laptop:~$ lspci 
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10) 
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge 
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
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M] 
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14) 
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD) 

ALSO......

earl@earl-laptop:~$ lsusb 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 

lspci -nn | grep 'Wireless Brand'


I didn't get anything returned to the terminal so I suppose I have no idea what the command is supposed to be.

3.  Check interface
earl@earl-laptop:~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:1196 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1196 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:95120 (95.1 KB)  TX bytes:95120 (95.1 KB)

earl@earl-laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

earl@earl-laptop:~$ iwconfig wlan0 
wlan0     No such device 

4-  Check for modules:

earl@earl-laptop:~$ lsmod 
Module                  Size  Used by 
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8708  0 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_idt      51914  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon 
font                    7557  1 fbcon 
bitblit                 4707  1 fbcon 
softcursor              1189  1 bitblit 
vga16fb                11385  0 
vgastate                8961  1 vga16fb 
snd_hda_intel          21877  2 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel 
snd_hwdep               5412  1 snd_hda_codec 
snd_pcm_oss            35308  0 
iptable_filter          2271  0 
pcmcia                 33024  0 
snd_mixer_oss          13746  1 snd_pcm_oss 
ip_tables               9991  1 iptable_filter 
x_tables               14299  1 ip_tables 
snd_pcm                70662  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss 
arc4                    1153  0 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
radeon                674135  3 
snd_timer              19098  2 snd_pcm,snd_seq 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
ttm                    49943  1 radeon 
drm_kms_helper         29297  1 radeon 
drm                   162471  5 radeon,ttm,drm_kms_helper 
snd                    54148  17 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
mac80211              204922  0 
tifm_7xx1               3690  0 
i2c_algo_bit            5028  1 radeon 
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket 
video                  17375  0 
output                  1871  1 video 
tifm_core               6045  1 tifm_7xx1 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic 
cfg80211              126485  1 mac80211 
led_class               2864  0 
psmouse                63245  0 
serio_raw               3978  0 
i2c_piix4               8335  0 
soundcore               6620  1 snd 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm 
shpchp                 28820  0 
k8temp                  3024  0 
ati_agp                 5094  0 
agpgart                31724  3 ttm,drm,ati_agp 
lp                      7028  0 
parport                32635  2 ppdev,lp 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394 
sky2                   40775  0 
pata_atiixp             3148  2 

earl@earl-laptop:~$ lsmod | grep "wlan_module_name" 

earl@earl-laptop:~$ lshw -C network\\\\\\\\\\\\\\\\\\\\\\\ 
> 
WARNING: you should run this program as super-user. 
CPUID        



5  Kernel boot messages

[    0.177838] pci 0000:00:05.0: PME# disabled 
[    0.177908] pci 0000:00:13.0: reg 10 32bit mmio: [0xc0004000-0xc0004fff] 
[    0.178020] pci 0000:00:13.1: reg 10 32bit mmio: [0xc0005000-0xc0005fff] 
[    0.178142] pci 0000:00:13.2: reg 10 32bit mmio: [0xc0006000-0xc0006fff] 
[    0.178214] pci 0000:00:13.2: supports D1 D2 
[    0.178218] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot 
[    0.178224] pci 0000:00:13.2: PME# disabled 
[    0.178282] pci 0000:00:14.0: reg 10 io port: [0x8400-0x840f] 
[    0.178293] pci 0000:00:14.0: reg 14 32bit mmio: [0xfed00000-0xfed003ff] 
[    0.178331] HPET not enabled in BIOS. You might try hpet=force boot option 
[    0.178399] pci 0000:00:14.1: reg 10 io port: [0x1f0-0x1f7] 
[    0.178410] pci 0000:00:14.1: reg 14 io port: [0x3f4-0x3f7] 
[    0.178420] pci 0000:00:14.1: reg 18 io port: [0x00-0x07] 
[    0.178430] pci 0000:00:14.1: reg 1c io port: [0x00-0x03] 
[    0.178441] pci 0000:00:14.1: reg 20 io port: [0x8410-0x841f] 
[    0.178544] pci 0000:00:14.2: reg 10 64bit mmio: [0xc0000000-0xc0003fff] 
[    0.178611] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold 
[    0.178618] pci 0000:00:14.2: PME# disabled 
[    0.178870] pci 0000:01:05.0: reg 10 32bit mmio pref: [0xc8000000-0xcfffffff] 
[    0.178877] pci 0000:01:05.0: reg 14 io port: [0x9000-0x90ff] 
[    0.178883] pci 0000:01:05.0: reg 18 32bit mmio: [0xc0100000-0xc010ffff] 
[    0.178895] pci 0000:01:05.0: reg 30 32bit mmio pref: [0x000000-0x01ffff] 
[    0.178906] pci 0000:01:05.0: supports D1 D2 
[    0.178926] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff] 
[    0.178931] pci 0000:00:01.0: bridge 32bit mmio: [0xc0100000-0xc01fffff] 
[    0.178937] pci 0000:00:01.0: bridge 64bit mmio pref: [0xc8000000-0xcfffffff] 
[    0.180059] pci 0000:02:00.0: reg 10 64bit mmio: [0xc0200000-0xc0203fff] 
[    0.180069] pci 0000:02:00.0: reg 18 io port: [0xa000-0xa0ff] 
[    0.180135] pci 0000:02:00.0: supports D1 D2 
[    0.180138] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.180145] pci 0000:02:00.0: PME# disabled 
[    0.180213] pci 0000:00:04.0: bridge io port: [0xa000-0xafff] 
[    0.180218] pci 0000:00:04.0: bridge 32bit mmio: [0xc0200000-0xc02fffff] 
[    0.180269] pci 0000:05:00.0: reg 10 32bit mmio: [0xc0300000-0xc0303fff] 
[    0.180341] pci 0000:05:00.0: supports D1 D2 
[    0.180417] pci 0000:00:05.0: bridge 32bit mmio: [0xc0300000-0xc03fffff] 
[    0.180497] pci 0000:08:09.0: reg 10 32bit mmio: [0x000000-0x000fff] 
[    0.180531] pci 0000:08:09.0: supports D1 D2 
[    0.180535] pci 0000:08:09.0: PME# supported from D0 D1 D2 D3hot D3cold 
[    0.180543] pci 0000:08:09.0: PME# disabled 
[    0.180603] pci 0000:08:09.1: reg 10 32bit mmio: [0xc0405000-0xc04057ff] 
[    0.180616] pci 0000:08:09.1: reg 14 32bit mmio: [0xc0400000-0xc0403fff] 
[    0.180692] pci 0000:08:09.1: supports D1 D2 
[    0.180695] pci 0000:08:09.1: PME# supported from D0 D1 D2 D3hot 
[    0.180703] pci 0000:08:09.1: PME# disabled 
[    0.180761] pci 0000:08:09.2: reg 10 32bit mmio: [0xc0406000-0xc0406fff] 
[    0.180843] pci 0000:08:09.2: supports D1 D2 
[    0.180846] pci 0000:08:09.2: PME# supported from D0 D1 D2 D3hot 
[    0.180854] pci 0000:08:09.2: PME# disabled 
[    0.180922] pci 0000:00:14.4: transparent bridge 
[    0.180936] pci 0000:00:14.4: bridge 32bit mmio: [0xc0400000-0xc04fffff] 
[    0.180984] pci_bus 0000:00: on NUMA node 0 
[    0.180989] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT] 
[    0.181119] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT] 
[    0.181213] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT] 
[    0.181332] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT] 
[    0.181409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT] 
[    0.185086] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11) *0, disabled. 
[    0.185276] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11) *0, disabled. 
[    0.185463] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11) *0, disabled. 
[    0.185650] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11) *0, disabled. 
[    0.185838] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11) *0, disabled. 
[    0.186024] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11) *0, disabled. 
[    0.186210] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11) *0, disabled. 
[    0.186396] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11) *0, disabled. 
[    0.186584] ACPI: PCI Interrupt Link [LNKU] (IRQs 3 4 5 7 10 11) *0, disabled. 
[    0.186723] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none 
[    0.186731] vgaarb: loaded 
[    0.186867] SCSI subsystem initialized 
[    0.186984] libata version 3.00 loaded. 
[    0.187082] usbcore: registered new interface driver usbfs 
[    0.187098] usbcore: registered new interface driver hub 
[    0.187129] usbcore: registered new device driver usb 
[    0.187277] ACPI: WMI: Mapper loaded 
[    0.187280] PCI: Using ACPI for IRQ routing 
[    0.187489] NetLabel: Initializing 
[    0.187491] NetLabel:  domain hash size = 128 
[    0.187494] NetLabel:  protocols = UNLABELED CIPSOv4 
[    0.187513] NetLabel:  unlabeled traffic allowed by default 
[    0.189836] AppArmor: AppArmor Filesystem Enabled 
[    0.189858] pnp: PnP ACPI init 
[    0.189876] ACPI: bus type pnp registered 
[    0.192603] pnp 00:09: mem resource (0x0-0xfff) overlaps 0000:01:05.0 BAR 6 (0x0-0x1ffff), disabling 
[    0.192732] pnp: PnP ACPI: found 10 devices 
[    0.192732] ACPI: ACPI bus type pnp unregistered 
[    0.192732] PnPBIOS: Disabled by ACPI PNP 
[    0.192732] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved 
[    0.192732] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved 
[    0.192732] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved 
[    0.192732] system 00:08: ioport range 0x1080-0x1080 has been reserved 
[    0.192732] system 00:08: ioport range 0x220-0x22f has been reserved 
[    0.192732] system 00:08: ioport range 0x40b-0x40b has been reserved 
[    0.192732] system 00:08: ioport range 0x4d0-0x4d1 has been reserved 
[    0.192732] system 00:08: ioport range 0x4d6-0x4d6 has been reserved 
[    0.192732] system 00:08: ioport range 0x530-0x537 has been reserved 
[    0.192732] system 00:08: ioport range 0xc00-0xc01 has been reserved 
[    0.192732] system 00:08: ioport range 0xc14-0xc14 has been reserved 
[    0.192732] system 00:08: ioport range 0xc50-0xc52 has been reserved 
[    0.192732] system 00:08: ioport range 0xc6c-0xc6c has been reserved 
[    0.192732] system 00:08: ioport range 0xc6f-0xc6f has been reserved 
[    0.192732] system 00:08: ioport range 0xcd4-0xcd5 has been reserved 
[    0.192732] system 00:08: ioport range 0xcd6-0xcd7 has been reserved 
[    0.192732] system 00:08: ioport range 0xcd8-0xcdf has been reserved 
[    0.192732] system 00:08: ioport range 0x8000-0x805f has been reserved 
[    0.192732] system 00:08: ioport range 0xf40-0xf47 has been reserved 
[    0.192732] system 00:08: ioport range 0x87f-0x87f has been reserved 
[    0.192732] system 00:09: iomem range 0xe0000-0xfffff could not be reserved 
[    0.192732] system 00:09: iomem range 0xfff00000-0xffffffff could not be reserved 
[    0.228431] Switching to clocksource acpi_pm 
[    0.228976] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01 
[    0.228976] pci 0000:00:01.0:   IO window: 0x9000-0x9fff 
[    0.228976] pci 0000:00:01.0:   MEM window: 0xc0100000-0xc01fffff 
[    0.228976] pci 0000:00:01.0:   PREFETCH window: 0x000000c8000000-0x000000cfffffff 
[    0.228976] pci 0000:00:04.0: PCI bridge, secondary bus 0000:02 
[    0.228976] pci 0000:00:04.0:   IO window: 0xa000-0xafff 
[    0.228976] pci 0000:00:04.0:   MEM window: 0xc0200000-0xc02fffff 
[    0.228976] pci 0000:00:04.0:   PREFETCH window: disabled 
[    0.228976] pci 0000:00:05.0: PCI bridge, secondary bus 0000:05 
[    0.228976] pci 0000:00:05.0:   IO window: disabled 
[    0.228976] pci 0000:00:05.0:   MEM window: 0xc0300000-0xc03fffff 
[    0.228976] pci 0000:00:05.0:   PREFETCH window: disabled 
[    0.228976] pci 0000:08:09.0: CardBus bridge, secondary bus 0000:09 
[    0.228976] pci 0000:08:09.0:   IO window: 0x002000-0x0020ff 
[    0.228976] pci 0000:08:09.0:   IO window: 0x002400-0x0024ff 
[    0.228976] pci 0000:08:09.0:   PREFETCH window: 0x80000000-0x83ffffff 
[    0.228976] pci 0000:08:09.0:   MEM window: 0x84000000-0x87ffffff 
[    0.228976] pci 0000:00:14.4: PCI bridge, secondary bus 0000:08 
[    0.228976] pci 0000:00:14.4:   IO window: 0x2000-0x2fff 
[    0.228976] pci 0000:00:14.4:   MEM window: 0xc0400000-0xc04fffff 
[    0.228976] pci 0000:00:14.4:   PREFETCH window: 0x80000000-0x83ffffff 
[    0.228976] pci 0000:00:04.0: setting latency timer to 64 
[    0.228976] pci 0000:00:05.0: setting latency timer to 64 
[    0.228976]   alloc irq_desc for 20 on node -1 
[    0.228976]   alloc kstat_irqs on node -1 
[    0.228976] pci 0000:08:09.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[    0.228976] pci_bus 0000:00: resource 0 io:  [0x00-0xffff] 
[    0.228976] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff] 
[    0.228976] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff] 
[    0.228976] pci_bus 0000:01: resource 1 mem: [0xc0100000-0xc01fffff] 
[    0.228976] pci_bus 0000:01: resource 2 pref mem [0xc8000000-0xcfffffff] 
[    0.228976] pci_bus 0000:02: resource 0 io:  [0xa000-0xafff] 
[    0.228976] pci_bus 0000:02: resource 1 mem: [0xc0200000-0xc02fffff] 
[    0.228976] pci_bus 0000:05: resource 1 mem: [0xc0300000-0xc03fffff] 
[    0.228976] pci_bus 0000:08: resource 0 io:  [0x2000-0x2fff] 
[    0.228976] pci_bus 0000:08: resource 1 mem: [0xc0400000-0xc04fffff] 
[    0.228976] pci_bus 0000:08: resource 2 pref mem [0x80000000-0x83ffffff] 
[    0.228976] pci_bus 0000:08: resource 3 io:  [0x00-0xffff] 
[    0.228976] pci_bus 0000:08: resource 4 mem: [0x000000-0xffffffff] 
[    0.228976] pci_bus 0000:09: resource 0 io:  [0x2000-0x20ff] 
[    0.228976] pci_bus 0000:09: resource 1 io:  [0x2400-0x24ff] 
[    0.228976] pci_bus 0000:09: resource 2 pref mem [0x80000000-0x83ffffff] 
[    0.228976] pci_bus 0000:09: resource 3 mem: [0x84000000-0x87ffffff] 
[    0.228976] NET: Registered protocol family 2 
[    0.228976] IP route cache hash table entries: 32768 (order: 5, 131072 bytes) 
[    0.228976] TCP established hash table entries: 131072 (order: 8, 1048576 bytes) 
[    0.229702] TCP bind hash table entries: 65536 (order: 7, 524288 bytes) 
[    0.230076] TCP: Hash tables configured (established 131072 bind 65536) 
[    0.230079] TCP reno registered 
[    0.230194] NET: Registered protocol family 1 
[    0.230212] pci 0000:00:00.0: MSI quirk detected; MSI disabled 
[    0.230218] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled 
[    0.230289] pci 0000:01:05.0: Boot video device 
[    0.230552] cpufreq-nforce2: No nForce2 chipset. 
[    0.230587] Scanning for low memory corruption every 60 seconds 
[    0.230708] audit: initializing netlink socket (disabled) 
[    0.230721] type=2000 audit(1272876793.228:1): initialized 
[    0.243572] highmem bounce pool size: 64 pages 
[    0.243579] HugeTLB registered 4 MB page size, pre-allocated 0 pages 
[    0.245509] VFS: Disk quotas dquot_6.5.2 
[    0.245585] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    0.246283] fuse init (API version 7.13) 
[    0.246382] msgmni has been set to 1693 
[    0.246661] alg: No test for stdrng (krng) 
[    0.246732] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253) 
[    0.246737] io scheduler noop registered 
[    0.246740] io scheduler anticipatory registered 
[    0.246743] io scheduler deadline registered 
[    0.246790] io scheduler cfq registered (default) 
[    0.246952] pcieport 0000:00:04.0: setting latency timer to 64 
[    0.247018] pcieport 0000:00:05.0: setting latency timer to 64 
[    0.247067] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[    0.247096] pciehp: PCI Express Hot Plug Controller Driver version: 0.4 
[    0.248024] ACPI: AC Adapter [ACAD] (off-line) 
[    0.248115] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0 
[    0.248411] ACPI: Lid Switch [LID] 
[    0.248468] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1 
[    0.248473] ACPI: Sleep Button [SLPB] 
[    0.248529] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2 
[    0.248533] ACPI: Power Button [PWRB] 
[    0.248585] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3 
[    0.248589] ACPI: Power Button [PWRF] 
[    0.248797] ACPI: processor limited to max C-state 1 
[    0.248825] processor LNXCPU:00: registered as cooling_device0 
[    0.248867] processor LNXCPU:01: registered as cooling_device1 
[    0.251767] thermal LNXTHERM:01: registered as thermal_zone0 
[    0.251777] ACPI: Thermal Zone [THRM] (56 C) 
[    0.253658] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled 
[    0.255207] brd: module loaded 
[    0.255780] loop: module loaded 
[    0.255893] input: Macintosh mouse button emulation as /devices/virtual/input/input4 
[    0.256089]   alloc irq_desc for 16 on node -1 
[    0.256092]   alloc kstat_irqs on node -1 
[    0.256102] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.256157] pata_acpi 0000:00:14.1: setting latency timer to 64 
[    0.256547] Fixed MDIO Bus: probed 
[    0.256591] PPP generic driver version 2.4.2 
[    0.256640] tun: Universal TUN/TAP device driver, 1.6 
[    0.256643] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com> 
[    0.256743] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver 
[    0.256765]   alloc irq_desc for 19 on node -1 
[    0.256768]   alloc kstat_irqs on node -1 
[    0.256773] ehci_hcd 0000:00:13.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[    0.256796] ehci_hcd 0000:00:13.2: EHCI Host Controller 
[    0.256848] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 1 
[    0.256921] ehci_hcd 0000:00:13.2: irq 19, io mem 0xc0006000 
[    0.257098] isapnp: Scanning for PnP cards... 
[    0.297119] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00 
[    0.297292] usb usb1: configuration #1 chosen from 1 choice 
[    0.297331] hub 1-0:1.0: USB hub found 
[    0.297344] hub 1-0:1.0: 8 ports detected 
[    0.297444] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
[    0.297472] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[    0.297496] ohci_hcd 0000:00:13.0: OHCI Host Controller 
[    0.297544] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2 
[    0.297570] ohci_hcd 0000:00:13.0: irq 19, io mem 0xc0004000 
[    0.316970] ACPI: Battery Slot [BAT1] (battery present) 
[    0.353519] usb usb2: configuration #1 chosen from 1 choice 
[    0.353562] hub 2-0:1.0: USB hub found 
[    0.353578] hub 2-0:1.0: 4 ports detected 
[    0.353656] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
[    0.353679] ohci_hcd 0000:00:13.1: OHCI Host Controller 
[    0.353725] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3 
[    0.353750] ohci_hcd 0000:00:13.1: irq 19, io mem 0xc0005000 
[    0.409600] usb usb3: configuration #1 chosen from 1 choice 
[    0.409641] hub 3-0:1.0: USB hub found 
[    0.409657] hub 3-0:1.0: 4 ports detected 
[    0.409741] uhci_hcd: USB Universal Host Controller Interface driver 
[    0.409844] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12 
[    0.411486] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    0.411497] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    0.411646] mice: PS/2 mouse device common for all mice 
[    0.411854] rtc_cmos 00:04: RTC can wake from S4 
[    0.411903] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0 
[    0.411933] rtc0: alarms up to one month, 114 bytes nvram 
[    0.412054] device-mapper: uevent: version 1.0.3 
[    0.414728] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email] 
[    0.425076] device-mapper: multipath: version 1.1.0 loaded 
[    0.425082] device-mapper: multipath round-robin: version 1.0.0 loaded 
[    0.426280] EISA: Probing bus 0 at eisa.0 
[    0.426290] Cannot allocate resource for EISA slot 1 
[    0.426293] Cannot allocate resource for EISA slot 2 
[    0.426321] Cannot allocate resource for EISA slot 8 
[    0.426325] EISA: Detected 0 cards. 
[    0.437386] cpuidle: using governor ladder 
[    0.437389] cpuidle: using governor menu 
[    0.437997] TCP cubic registered 
[    0.438182] NET: Registered protocol family 10 
[    0.438798] lo: Disabled Privacy Extensions 
[    0.439240] NET: Registered protocol family 17 
[    0.439281] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-52 processors (2 cpu cores) (version 2.20.00) 
[    0.439316] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13 
[    0.439319] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e 
[    0.439367] Using IPI No-Shortcut mode 
[    0.439467] PM: Resume from disk failed. 
[    0.439482] registered taskstats version 1 
[    0.439896]   Magic number: 10:403:876 
[    0.440028] rtc_cmos 00:04: setting system clock to 2010-05-03 08:53:14 UTC (1272876794) 
[    0.440032] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
[    0.440035] EDD information not available. 
[    0.442801] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5 
[    0.443501] Freeing initrd memory: 7764k freed 
[    0.614445] isapnp: No Plug & Play device found 
[    0.614463] Freeing unused kernel memory: 656k freed 
[    0.615087] Write protecting the kernel text: 4676k 
[    0.615136] Write protecting the kernel read-only data: 1840k 
[    0.638193] udev: starting version 151 
[    0.745503] scsi0 : pata_atiixp 
[    0.768352] scsi1 : pata_atiixp 
[    0.769235] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8410 irq 14 
[    0.769239] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8418 irq 15 
[    0.780269]   alloc irq_desc for 17 on node -1 
[    0.780274]   alloc kstat_irqs on node -1 
[    0.780284] b43-pci-bridge 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[    0.780296] b43-pci-bridge 0000:05:00.0: setting latency timer to 64 
[    0.783606] sky2 driver version 1.25 
[    0.783659] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[    0.783676] sky2 0000:02:00.0: setting latency timer to 64 
[    0.783717] sky2 0000:02:00.0: Yukon-2 FE chip revision 1 
[    0.784610] sky2 eth0: addr 00:e0:b8:b9:73:c3 
[    0.844122] ssb: Sonics Silicon Backplane found on PCI device 0000:05:00.0 
[    0.940881] ata1.00: ATA-7: Hitachi HTS541616J9AT00, SB4OA70H, max UDMA/100 
[    0.940886] ata1.00: 312581808 sectors, multi 16: LBA48 
[    0.940929] ata1.01: ATAPI: HL-DT-ST DVD-RW GWA-4082N, CG03, max UDMA/33 
[    0.956829] ata1.00: configured for UDMA/100 
[    0.972583] ata1.01: configured for UDMA/33 
[    0.975037] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SB4O PQ: 0 ANSI: 5 
[    0.975241] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    0.975251] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB) 
[    0.975311] sd 0:0:0:0: [sda] Write Protect is off 
[    0.975315] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    0.976891] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    0.978795] scsi 0:0:1:0: CD-ROM            HL-DT-ST DVD-RW GWA-4082N CG03 PQ: 0 ANSI: 5 
[    0.978879]  sda: sda1 sda2 sda3 < sda5 sda6 > 
[    1.055376] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray 
[    1.055381] Uniform CD-ROM driver Revision: 3.20 
[    1.055474] sd 0:0:0:0: [sda] Attached SCSI disk 
[    1.055494] sr 0:0:1:0: Attached scsi CD-ROM sr0 
[    1.055568] sr 0:0:1:0: Attached scsi generic sg1 type 5 
[    1.214343] ohci1394 0000:08:09.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
[    1.269105] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[c0405000-c04057ff]  Max Packet=[2048]  IR/IT contexts=[4/8] 
[    1.814229] EXT4-fs (sda5): mounted filesystem with ordered data mode 
[    2.540392] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e0b803670162b4] 
[   26.507700] udev: starting version 151 
[   26.549292] lp: driver loaded but no devices found 
[   26.583149] Adding 2594456k swap on /dev/sda6.  Priority:-1 extents:1 across:2594456k 
[   26.611099] Linux agpgart interface v0.103 
[   26.658201] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141 
[   26.664960] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   26.666184] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x8400, revision 0 
[   26.839626] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function 
[   26.839666] [Firmware Bug]: _BCQ is used instead of _BQC 
[   26.850253] acpi device:1a: registered as cooling_device2 
[   26.850642] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/device:17/LNXVIDEO:00/input/input6 
[   26.850708] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no) 
[   26.852855] cfg80211: Calling CRDA to update world regulatory domain 
[   26.853117] yenta_cardbus 0000:08:09.0: CardBus bridge found [107b:0367] 
[   26.853147] yenta_cardbus 0000:08:09.0: Using CSCINT to route CSC interrupts to PCI 
[   26.853150] yenta_cardbus 0000:08:09.0: Routing CardBus interrupts to PCI 
[   26.853159] yenta_cardbus 0000:08:09.0: TI: mfunc 0x01ac1b22, devctl 0x64 
[   26.908066] cfg80211: World regulatory domain updated: 
[   26.908072] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
[   26.908077] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   26.908081] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   26.908085] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
[   26.908089] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   26.908092] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
[   26.908566] type=1505 audit(1272891220.968:2):  operation="profile_load" pid=561 name="/sbin/dhclient3" 
[   26.908923] type=1505 audit(1272891220.968:3):  operation="profile_load" pid=561 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   26.909150] type=1505 audit(1272891220.968:4):  operation="profile_load" pid=561 name="/usr/lib/connman/scripts/dhclient-script" 
[   26.944426] [drm] Initialized drm 1.1.0 20060810 
[   26.951701] b43-phy0: Broadcom 4311 WLAN found (core revision 10) 
[   27.003767] [drm] radeon defaulting to kernel modesetting. 
[   27.003771] [drm] radeon kernel modesetting enabled. 
[   27.003862] radeon 0000:01:05.0: power state changed by ACPI to D0 
[   27.003875] radeon 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
[   27.006284] [drm] radeon: Initializing kernel modesetting. 
[   27.006411] [drm] register mmio base: 0xC0100000 
[   27.006413] [drm] register mmio size: 65536 
[   27.006807] [drm] GPU reset succeed (RBBM_STATUS=0x00000140) 
[   27.006823] [drm:rs400_gart_adjust_size] *ERROR* Forcing to 32M GART size (because of ASIC bug ?) 
[   27.006872] [drm] Generation 2 PCI interface, using max accessible memory 
[   27.006875] [drm] radeon: VRAM 128M 
[   27.006878] [drm] radeon: VRAM from 0x78000000 to 0x7FFFFFFF 
[   27.006880] [drm] radeon: GTT 32M 
[   27.006883] [drm] radeon: GTT from 0x80000000 to 0x81FFFFFF 
[   27.006921] [drm] radeon: irq initialized. 
[   27.007141] [drm] Detected VRAM RAM=128M, BAR=128M 
[   27.007147] [drm] RAM width 128bits DDR 
[   27.007274] [TTM] Zone  kernel: Available graphics memory: 437758 kiB. 
[   27.007277] [TTM] Zone highmem: Available graphics memory: 965378 kiB. 
[   27.007299] [drm] radeon: 128M of VRAM memory ready 
[   27.007301] [drm] radeon: 32M of GTT memory ready. 
[   27.007325] [drm] GART: num cpu pages 8192, num gpu pages 8192 
[   27.007854] [drm] radeon: 2 quad pipes, 1 z pipes initialized. 
[   27.007878] [drm] radeon: cp idle (0x10000C03) 
[   27.007930] [drm] Loading R300 Microcode 
[   27.007935] platform radeon_cp.0: firmware: requesting radeon/R300_cp.bin 
[   27.015115] [drm] radeon: ring at 0x0000000080000000 
[   27.015139] [drm] ring test succeeded in 2 usecs 
[   27.015304] [drm] radeon: ib pool ready. 
[   27.015388] [drm] ib test succeeded in 0 usecs 
[   27.015426] [drm] Default TV standard: NTSC 
[   27.015428] [drm] 14.318180000 MHz TV ref clk 
[   27.015523] [drm] Panel ID String: SEC                     
[   27.015527] [drm] Panel Size 1280x800 
[   27.015594] [drm] Default TV standard: NTSC 
[   27.015596] [drm] 14.318180000 MHz TV ref clk 
[   27.015630] [drm] Radeon Display Connectors 
[   27.015633] [drm] Connector 0: 
[   27.015636] [drm]   VGA 
[   27.015639] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68 
[   27.015642] [drm]   Encoders: 
[   27.015644] [drm]     CRT1: INTERNAL_DAC2 
[   27.015647] [drm] Connector 1: 
[   27.015649] [drm]   LVDS 
[   27.015653] [drm]   DDC: 0x198 0x198 0x19c 0x19c 0x1a0 0x1a0 0x1a4 0x1a4 
[   27.015656] [drm]   Encoders: 
[   27.015658] [drm]     LCD1: INTERNAL_LVDS 
[   27.015661] [drm] Connector 2: 
[   27.015663] [drm]   S-video 
[   27.015665] [drm]   Encoders: 
[   27.015667] [drm]     TV1: INTERNAL_DAC2 
[   27.083268] phy0: Selected rate control algorithm 'minstrel' 
[   27.084186] Registered led device: b43-phy0::tx 
[   27.084207] Registered led device: b43-phy0::rx 
[   27.084227] Registered led device: b43-phy0::radio 
[   27.084313] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ] 
[   27.090292] yenta_cardbus 0000:08:09.0: ISA IRQ mask 0x0ef8, PCI irq 20 
[   27.090297] yenta_cardbus 0000:08:09.0: Socket status: 30000006 
[   27.090305] yenta_cardbus 0000:08:09.0: pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff 
[   27.090311] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x2000-0x2fff: clean. 
[   27.090531] yenta_cardbus 0000:08:09.0: pcmcia: parent PCI bridge Memory window: 0xc0400000 - 0xc04fffff 
[   27.090535] yenta_cardbus 0000:08:09.0: pcmcia: parent PCI bridge Memory window: 0x80000000 - 0x83ffffff 
[   27.107395] tifm_7xx1 0000:08:09.2: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
[   27.131462] ip_tables: (C) 2000-2006 Netfilter Core Team 
[   27.199623] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   27.229168] [drm] fb mappable at 0xC8040000 
[   27.229172] [drm] vram apper at 0xC8000000 
[   27.229175] [drm] size 4096000 
[   27.229178] [drm] fb depth is 24 
[   27.229180] [drm]    pitch is 5120 
[   27.229360] fb0: radeondrmfb frame buffer device 
[   27.229364] registered panic notifier 
[   27.229371] [drm] Initialized radeon 2.0.0 20080528 for 0000:01:05.0 on minor 0 
[   27.232285] vga16fb: initializing 
[   27.232292] vga16fb: mapped to 0xc00a0000 
[   27.232298] vga16fb: not registering due to another framebuffer present 
[   27.280154] Console: switching to colour frame buffer device 160x50 
[   27.337548] input: HDA ATI SB Mic at Ext Front Jack as /devices/pci0000:00/0000:00:14.2/sound/card0/input7 
[   27.391476] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008 
[   27.430891] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input8 
[   27.465679] type=1505 audit(1272891221.524:5):  operation="profile_load" pid=769 name="/usr/share/gdm/guest-session/Xsession" 
[   27.467749] type=1505 audit(1272891221.524:6):  operation="profile_replace" pid=770 name="/sbin/dhclient3" 
[   27.468172] type=1505 audit(1272891221.528:7):  operation="profile_replace" pid=770 name="/usr/lib/NetworkManager/nm-dhcp-client.action" 
[   27.468379] type=1505 audit(1272891221.528:8):  operation="profile_replace" pid=770 name="/usr/lib/connman/scripts/dhclient-script" 
[   27.472860] type=1505 audit(1272891221.532:9):  operation="profile_load" pid=771 name="/usr/bin/evince" 
[   27.477761] type=1505 audit(1272891221.536:10):  operation="profile_load" pid=771 name="/usr/bin/evince-previewer" 
[   27.480715] type=1505 audit(1272891221.540:11):  operation="profile_load" pid=771 name="/usr/bin/evince-thumbnailer" 
[   27.612504] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean. 
[   27.614872] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean. 
[   27.615872] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean. 
[   27.616716] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean. 
[   27.617661] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean. 
[   28.919129] ppdev: user-space parallel port driver 
[   90.164058] Clocksource tsc unstable (delta = -249254579 ns) 
[ 1154.627206] b43-pci-bridge 0000:05:00.0: PCI INT A disabled 
[ 3032.755232] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw. 
[ 3032.755237] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools. 
[ 3032.755241] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details. 

6- Network Configuration

earl@earl-laptop:~$ sudo lshw -C network 
[sudo] password for earl: 
  *-network DISABLED      
       description: Ethernet interface 
       product: 88E8038 PCI-E Fast Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 14 
       serial: 00:e0:b8:b9:73:c3 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:16 memory:c0200000-c0203fff ioport:a000(size=256) 
  *-network UNCLAIMED 
       description: Network controller 
       product: BCM4311 802.11b/g WLAN 
       vendor: Broadcom Corporation 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       version: 01 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress cap_list 
       configuration: latency=0 
       resources: memory:c0300000-c0303fff 


7- Scan for networks

earl@earl-laptop:~$ iwlist scan 
lo        Interface doesn't support scanning. 

eth0      Interface doesn't support scanning. 

earl@earl-laptop:~$ iwlist scan wlan0 
iwlist: unknown command `wlan0' (check 'iwlist &#8211;help'). 

8- Ubuntu version 

earl@earl-laptop:~$ lsb_release -d 
Description:	Ubuntu 10.04 LTS 


9- Kernel/architecture (including 32 vs. 64 bit):

earl@earl-laptop:~$ uname -mr 
2.6.32-21-generic i686 


10-  Restarting the network:

earl@earl-laptop:~$ sudo /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                   [ OK ]

---

### Post by arubislander on 2010-05-03
I've had the same problem on my Acer netbook running Lucid. The first time I encountered it I was at a loss what to do, no amount of manually nudging the connection seemed to help, so I ended up re-installing (it was a new netbook, so not much loss). I did notice though that it happened after waking up from hibernation (or suspend). 

When it happened again after the re-install I noticed that if I hibernated or suspended the machine and then woke it up, depending on when it died (hibernating or suspending), my network would come back to life. Once I had to hibernate, wake, suspend, wake and then restart before I got my network going again.

---

### Post by PDA1 on 2010-05-03
I have no idea how to "wake up" my computer after hibernating or suspend.  In windows I just hit the power button and it starts up again.  Not so with Ubuntu.

---

### Post by klemes on 2010-05-03
The fact that you had a working connection before and now you don't points to something probably simple being neglected.I would definately look at my network-manager settings and first of all if I had networking disabled.
Might be something simple as that.

---

### Post by PDA1 on 2010-05-03
How do I setup or check my network manager settings?     

Since I've upgraded to 10.04 (which I wish I never did) I've lost the capability to do a &quot;right click&quot; on the network connection icon next to the volume control at the top of my screen.     

Also, when I try to SHUT DOWN my computer never completely shuts off like it used to in before I upgraded.  It goes through the normal shut down procedure, the cpu fans keeps running but the screen is black.

---

### Post by PDA1 on 2010-05-03
See my other post under the same name.  I couldn't format this properly

---

### Post by PDA1 on 2010-05-03
Problem- no Networking enabled with Ubuntu 10.04. 
 Network connection was lost 1 day after I upgraded from 9.04. I couldn't connect to the web with wireless or ethernet and Networking was grayed and said it was “disabled” 
 The steps are numbered below 
 (DO NOT enter the numbers when you're using Terminal)(anything in quotes marks doesn't need to be typed- they are there for reference only)
 
Here's how I fixed it- 
 Start TERMINAL 
 
[LIST=1]
[*]     sudo Nautilus
[/LIST]
 
[LIST=1]
[*]     Go to the folder /var/lib/NetworkManager/ 
[*]     Edit the file NetworkManager.state to read “setting NetworkingEnabled=true” 
[*]     Save the edited NetworkManager.state file 
[*]     Close Nautilus 
[*]     Using TERMINAL type “sudo restart network-manager”
[/LIST]
  This should enable networking again. I hope it works for you.....believe it or not it did for me.

---

### Post by Stanver on 2010-05-03
Same happend to me. I put Kubuntu 10.04 to sleep and found that it would not wake up again.
After reboot, the ethernet link to the ADSL modem/router was no more and nothing that I did would resurrect it.
After some head scratching and spelunking in Ubuntu's innards, I discovered that the ethernet entry had been completely stripped out of the "/etc/network/interfaces" file. I reinstated the appropriate lines (sudo pico) and restarted networking with "sudo /etc/init.d/networking restart".
For those interested, my "/etc/network/interfaces" now contains the following:
    auto eth0 lo
    iface eth0 inet dhcp
    iface lo inet loopback

---

### Post by PDA1 on 2010-05-03
Problem- no Networking enabled with Ubuntu 10.04. 
 Network connection was lost 1 day after I upgraded from 9.04. I couldn't connect to the web with wireless or ethernet and Networking was grayed and said it was &#8220;disabled&#8221; 
 The steps are numbered below 
 (DO NOT enter the numbers when you're using Terminal)(anything in quotes marks doesn't need to be typed- they are there for reference only)
 
Here's how I fixed it- 
 Start TERMINAL 
 
[LIST=1]
[*]     sudo Nautilus
[/LIST]
 
[LIST=1]
[*]     Go to the folder /var/lib/NetworkManager/ 
[*]     Edit the file NetworkManager.state to read &#8220;setting NetworkingEnabled=true&#8221; 
[*]     Save the edited NetworkManager.state file 
[*]     Close Nautilus 
[*]     Using TERMINAL type &#8220;sudo restart network-manager&#8221;
[/LIST]
  This should enable networking again. I hope it works for you.....believe it or not it did for me.

---

### Post by Iowan on 2010-05-03
Threads merged.

---

### Post by ccolbert on 2010-05-03
As I am *BRAND NEW* to Ubuntu (and Linux in general), could I bother you to go into more detail around the specifics on how to accomplish those tasks? Opening Terminal and navigating to a directory are about the extent of my knowledge. For example:
- Is "sudo Nautilus" just another way of opening Terminal or is it a separate command altogether?
- How would one go about 'editing' NetworkManager.state?
- How do you save it after editing?

My issue is that wired and wireless both worked just fine since installation (a few days ago) but once the laptop went to sleep/hibernation for the first time last night, now I can't get it to work again so I'm hoping this fix does the trick. Thanks and please excuse my ignorance.

---

