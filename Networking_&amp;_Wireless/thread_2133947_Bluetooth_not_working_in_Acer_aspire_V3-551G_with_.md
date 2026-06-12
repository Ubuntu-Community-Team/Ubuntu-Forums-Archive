---
title: "Bluetooth not working in Acer aspire V3-551G with AR9462 card."
date: 2013-04-09
forum: Networking &amp; Wireless
---

### Post by Inamati on 2013-04-09
OK so I managed to get my wireless card working with the invaluable help of Wild Man but bluetooth still doesn't work. It detects the adapter but it doesn't detect or gets detected by devices. I managed to get it working once by compiling compat driver but it ruined the wireless. Help.

---

### Post by chili555 on 2013-04-09
Once in a while, I like to race the Wild Man!

Remember you added a parameter to your files? Please add one more:```
options ath9k nohwcrypt=1 btcoex_enable=1
```Reboot and tell us if it's working.

---

### Post by Inamati on 2013-04-10
Sorry for the delay but it's been busy. I guess the race is still on. I tried what you suggested but didn't work. Still isn't detected or detects.

---

### Post by chili555 on 2013-04-10
> **Inamati said:**
> Sorry for the delay but it's been busy. I guess the race is still on. I tried what you suggested but didn't work. Still isn't detected or detects.That's the end of my limited skill in this area; I'll ask the Wild Man to help us out.

---

### Post by wildmanne39 on 2013-04-10
Hi, I do not know much about bluetooth but google is my friend so I hope it will help, please post the outcome of:
```
rfkill list all
lsmod
```
here by clicking on new reply and click # then paste the information between the brackets.

Edit: Indeed I meant [COLOR="#FF0000"]lsmod[/COLOR] Fat finger syndrome strikes again.
Thanks Chili555
Thanks

---

### Post by chili555 on 2013-04-11
He means:```
*lsmod*
rfkill list all
```

---

### Post by Inamati on 2013-04-12
[/CODE]> **Wild Man said:**
> Hi, I do not know much about bluetooth but google is my friend so I hope it will help, please post the outcome of:
```
rfkill list all
lsmod
```
here by clicking on new reply and click # then paste the information between the brackets.

Edit: Indeed I meant [COLOR=#FF0000]lsmod[/COLOR] Fat finger syndrome strikes again.
Thanks Chili555
Thanks

```
0: phy0: Wireless LAN	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

```
Module                  Size  Used bypci_stub               12551  1 
vboxpci                22897  0 
vboxnetadp             25637  0 
vboxnetflt             27262  0 
vboxdrv               252271  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   17708  2 
parport_pc             31969  0 
rfcomm                 37277  12 
ppdev                  12818  0 
snd_hda_codec_realtek    63579  1 
snd_hda_codec_hdmi     31457  1 
snd_hda_intel          32516  5 
snd_hda_codec         111548  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13273  1 snd_hda_codec
uvcvideo               71278  0 
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videobuf2_core         32071  1 uvcvideo
snd_seq_midi           13133  0 
videodev               95842  2 uvcvideo,videobuf2_core
radeon                825498  4 
binfmt_misc            17261  1 
snd_rawmidi            25383  1 snd_seq_midi
arc4                   12474  2 
videobuf2_vmalloc      12757  1 uvcvideo
joydev                 17162  0 
videobuf2_memops       13213  1 videobuf2_vmalloc
btusb                  17987  0 
ath9k                 130234  0 
snd_seq_midi_event     14476  1 snd_seq_midi
bluetooth             183270  22 bnep,rfcomm,btusb
kvm_amd                54395  0 
ttm                    75535  1 radeon
kvm                   357807  1 kvm_amd
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
psmouse                84878  0 
mac80211              470397  1 ath9k
ath9k_common           13784  1 ath9k
snd_timer              24412  2 snd_pcm,snd_seq
aesni_intel            17939  3 
cryptd                 15615  1 aesni_intel
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
aes_i586               16996  1 aesni_intel
ath9k_hw              376363  2 ath9k,ath9k_common
ath                    19188  3 ath9k,ath9k_common,ath9k_hw
drm_kms_helper         47304  1 radeon
serio_raw              13032  0 
drm                   238811  6 radeon,ttm,drm_kms_helper
snd                    62146  20 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
k10temp                12959  0 
microcode              18210  0 
cfg80211              184165  3 ath9k,mac80211,ath
rtsx_pci_ms            12876  0 
memstick               15843  1 rtsx_pci_ms
wmi                    18591  0 
i2c_algo_bit           13198  1 radeon
i2c_piix4              12984  0 
video                  18895  0 
compat                 14558  5 ath9k,mac80211,ath9k_common,ath9k_hw,cfg80211
mac_hid                13038  0 
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
rtsx_pci_sdmmc         17239  0 
ahci                   25497  2 
libahci                25938  1 ahci
atl1c                  36176  0 
rtsx_pci               32060  2 rtsx_pci_ms,rtsx_pci_sdmmc
```

---

### Post by wildmanne39 on 2013-04-12
Hi, it looks like this is a bluetooth usb device correct? if so, insert the adapter in the usb port after the system has booted and see if it comes on.
Thanks

---

### Post by Inamati on 2013-04-12
It's not usb it's onboard and I believe it's the same card as the Wifi

---

### Post by wildmanne39 on 2013-04-12
You have three drivers loaded that are for an usb device, do you have a bluetooth mouse or something like that if not we can black list those drivers and see if that helps.
Thanks

---

### Post by Inamati on 2013-04-13
Yep I use a usb mouse

---

### Post by wildmanne39 on 2013-04-13
Please do:
```
sudo rmmod -r btusb
sudo rmmod -f bnep
sudo rmmod -f rfcomm
sudo rmmod -f bluetooth
sudo modprobe bluetooth
```
Thanks

---

### Post by Inamati on 2013-04-14
> **Wild Man said:**
> Please do:
```
sudo rmmod -r btusb
sudo rmmod -f bnep
sudo rmmod -f rfcomm
sudo rmmod -f bluetooth
sudo modprobe bluetooth
```
Thanks

All of those Gave the same error > Resource Temporarily Unavailable

The last one didn't do anything

---

### Post by wildmanne39 on 2013-04-15
Are you wanting to share files from your cell phone? Maybe this link will help.
[http://askubuntu.com/questions/131570/ubuntu-12-04-bluetooth-problem](http://askubuntu.com/questions/131570/ubuntu-12-04-bluetooth-problem)

I have researched your issue but I have been unable to find a solution.

---

### Post by Inamati on 2013-04-15
OK I'll search for the next couple of days and if I find a solution I'll post here. Thanks for the help.

---

### Post by ascmartins on 2013-04-20
Hi. I have the same issue with Acer V5-571G. If I connect a usb bluetooth device it works perfect, but the built in bluetooth has exactly the same proble: cannot detec or be detected. Any progress on this?

---

### Post by ascmartins on 2013-04-20
Hi. I have exactly the same issue with Acer V5-571G. Any progress on this?

---

### Post by Inamati on 2013-04-21
Ok so I tried this: [http://orkultus.wordpress.com/tag/bluetooth-ar9462-linux-linuxmint-ubuntu/](http://orkultus.wordpress.com/tag/bluetooth-ar9462-linux-linuxmint-ubuntu/) but the only thing it did is that I no longer have the bluetooth icon in the panel and it isn't detected. I tried some of the things in  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1024884](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1024884) with no luck but I might have done something wrong. Can somebody help me understand the bug report better?

Edit: Yep just ran rfkill list and it only detects the wireless...
 
Edit:  [https://bugs.launchpad.net/ubuntu/quantal/+source/linux/+bug/1024884/+activity](https://bugs.launchpad.net/ubuntu/quantal/+source/linux/+bug/1024884/+activity) in this bug they say they released a fix but I can't find it and the last attachment is just text. Also here [https://bugs.launchpad.net/ubuntu/quantal/+source/linux/+bug/1024884](https://bugs.launchpad.net/ubuntu/quantal/+source/linux/+bug/1024884) the same bug. I got the same error as this [https://bugs.launchpad.net/ubuntu/quantal/+source/linux/+bug/1024884/comments/53](https://bugs.launchpad.net/ubuntu/quantal/+source/linux/+bug/1024884/comments/53) but I don't know how to compile like he did. The same thing here [https://bugs.launchpad.net/ubuntu/quantal/+source/linux/+bug/1024884/comments/74](https://bugs.launchpad.net/ubuntu/quantal/+source/linux/+bug/1024884/comments/74) so apparently it involves compiling something.

Please I need help.

---

### Post by Inamati on 2013-04-22
Here is what i get with dmesg:

```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-27-generic (buildd@akateko) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #46-Ubuntu SMP Mon Mar 25 20:00:05 UTC 2013 (Ubuntu 3.5.0-27.46-generic 3.5.7.7)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000af9befff] usable
[    0.000000] BIOS-e820: [mem 0x00000000af9bf000-0x00000000afabefff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000afabf000-0x00000000afbbefff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000afbbf000-0x00000000afbfefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000afbff000-0x00000000afbfffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000afc00000-0x00000000cfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec10000-0x00000000fec10fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed80000-0x00000000fed80fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffc00000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000022effffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: Acer Aspire V3-551G/VA50_CM, BIOS V1.03 05/23/2012
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x22f000 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-through
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFE0000000 write-back
[    0.000000]   2 base 0000A0000000 mask FFFFF0000000 write-back
[    0.000000]   3 base 0000AFBBD000 mask FFFFFFFFF000 uncachable
[    0.000000]   4 base 0000FFC00000 mask FFFFFFC00000 write-protect
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 000000022f000000 aka 8944M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000fe1b0-0x000fe1bf] mapped at [c00fe1b0]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x3630a000-0x3717cfff]
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 ACRSYS)
[    0.000000] ACPI: XSDT afbfe120 0008C (v01 ACRSYS ACRPRDCT 00000001      01000013)
[    0.000000] ACPI: FACP afbfc000 0010C (v05 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: DSDT afbe9000 0EB54 (v01 ACRSYS ACRPRDCT F0000000 1025 00040000)
[    0.000000] ACPI: FACS afb78000 00040
[    0.000000] ACPI: UEFI afbfd000 00236 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: HPET afbfb000 00038 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: APIC afbfa000 00084 (v03 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: MCFG afbf9000 0003C (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: ASF! afbf8000 000A5 (v32 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: BOOT afbe8000 00028 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SLIC afbe7000 00176 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: WDRT afbe6000 00047 (v01 ACRSYS ACRPRDCT 00000000 1025 00040000)
[    0.000000] ACPI: WDAT afbe5000 001AC (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: FPDT afbe3000 00044 (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT afbe2000 00B9C (v01 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: SSDT afbe0000 01ED4 (v02 ACRSYS ACRPRDCT 00000001 1025 00040000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 8052MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x2effffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009efff]
[    0.000000]   node   0: [mem 0x00100000-0xaf9befff]
[    0.000000]   node   0: [mem 0xafbff000-0xafbfffff]
[    0.000000]   node   0: [mem 0x00000000-0x2effffff]
[    0.000000] On node 0 totalpages: 1960271
[    0.000000] free_area_init_node: node 0, pgdat c189db80, node_mem_map f1d2a200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 16105 pages used for memmap
[    0.000000]   HighMem zone: 1715929 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x10] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x11] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x12] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x13] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x10228210 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] e820: [mem 0xd0000000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bb3000 s34176 r0 d23168 u57344
[    0.000000] pcpu-alloc: s34176 r0 d23168 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 [0] 2 [0] 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1942382
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-27-generic root=UUID=a9b40aa8-6e18-42ad-9f18-3de459fca84b ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x7, cntxt size 0x340
[    0.000000] allocated 18317184 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0022f000)
[    0.000000] Memory: 7725148k/9158656k available (5956k kernel code, 115936k reserved, 2918k data, 756k init, 6928136k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff15000 - 0xfffff000   ( 936 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc18ab000 - 0xc1968000   ( 756 kB)
[    0.000000]       .data : 0xc15d11a4 - 0xc18aaa80   (2918 kB)
[    0.000000]       .text : 0xc1000000 - 0xc15d11a4   (5956 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:712 16
[    0.000000] CPU 0 irqstacks, hard=f740a000 soft=f740c000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.004000] Detected 1896.623 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 3793.24 BogoMIPS (lpj=7586492)
[    0.000006] pid_max: default: 32768 minimum: 301
[    0.000033] Security Framework initialized
[    0.000046] AppArmor: AppArmor initialized
[    0.000047] Yama: becoming mindful.
[    0.000097] Mount-cache hash table entries: 512
[    0.000302] Initializing cgroup subsys cpuacct
[    0.000305] Initializing cgroup subsys memory
[    0.000313] Initializing cgroup subsys devices
[    0.000315] Initializing cgroup subsys freezer
[    0.000317] Initializing cgroup subsys blkio
[    0.000319] Initializing cgroup subsys perf_event
[    0.000346] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.000350] CPU: Physical Processor ID: 0
[    0.000351] CPU: Processor Core ID: 0
[    0.000354] mce: CPU supports 7 MCE banks
[    0.002607] ACPI: Core revision 20120320
[    0.014450] ftrace: allocating 24569 entries in 48 pages
[    0.026024] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.026448] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066071] CPU0: AMD A8-4500M APU with Radeon(tm) HD Graphics    stepping 01
[    0.171509] Performance Events: AMD Family 15h PMU driver.
[    0.171515] ... version:                0
[    0.171516] ... bit width:              48
[    0.171518] ... generic registers:      6
[    0.171520] ... value mask:             0000ffffffffffff
[    0.171522] ... max period:             00007fffffffffff
[    0.171523] ... fixed-purpose events:   0
[    0.171525] ... event mask:             000000000000003f
[    0.171664] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.171760] CPU 1 irqstacks, hard=f74e4000 soft=f74e6000
[    0.181979] Initializing CPU#1
[    0.182735] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.171762] Booting Node   0, Processors  #1
[    0.185031] CPU 2 irqstacks, hard=f74f8000 soft=f74fa000
[    0.195018] Initializing CPU#2
[    0.196001] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.185036]  #2
[    0.198232] CPU 3 irqstacks, hard=f7504000 soft=f7506000
[    0.198236]  #3 Ok.
[    0.208246] Initializing CPU#3
[    0.209153] [Firmware Info]: CPU: Re-enabling disabled Topology Extensions Support
[    0.211368] Brought up 4 CPUs
[    0.211372] Total of 4 processors activated (15172.98 BogoMIPS).
[    0.212465] devtmpfs: initialized
[    0.212654] EVM: security.selinux
[    0.212656] EVM: security.SMACK64
[    0.212658] EVM: security.capability
[    0.212761] PM: Registering ACPI NVS region [mem 0xafabf000-0xafbbefff] (1048576 bytes)
[    0.213993] dummy: 
[    0.214069] RTC time: 13:25:12, date: 04/22/13
[    0.214112] NET: Registered protocol family 16
[    0.214266] EISA bus registered
[    0.214336] Trying to unpack rootfs image as initramfs...
[    0.214474] ACPI: bus type pci registered
[    0.214591] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.214595] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.214596] PCI: Using MMCONFIG for extended config space
[    0.214598] PCI: Using configuration type 1 for base access
[    0.214755] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.214757] mtrr: probably your BIOS does not setup all CPUs.
[    0.214758] mtrr: corrected configuration.
[    0.215840] bio: create slab <bio-0> at 0
[    0.215943] ACPI: Added _OSI(Module Device)
[    0.215946] ACPI: Added _OSI(Processor Device)
[    0.215948] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.215950] ACPI: Added _OSI(Processor Aggregator Device)
[    0.219098] ACPI: EC: Look up EC in DSDT
[    0.222233] ACPI: Executed 1 blocks of module-level executable AML code
[    0.227909] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.248168] ACPI: Interpreter enabled
[    0.248176] ACPI: (supports S0 S3 S4 S5)
[    0.248198] ACPI: Using IOAPIC for interrupt routing
[    0.399813] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.400153] ACPI: No dock devices found.
[    0.400159] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.400267] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.400412] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.400416] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.400419] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.400422] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.400424] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.400427] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.400430] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.400432] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.400435] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.400437] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.400440] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.400442] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.400445] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.400447] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.400450] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.400452] pci_root PNP0A08:00: host bridge window [mem 0xd0000000-0xf7ffffff]
[    0.400455] pci_root PNP0A08:00: host bridge window [mem 0xfc000000-0xfed3ffff]
[    0.400457] pci_root PNP0A08:00: host bridge window [mem 0xfed45000-0xffffffff]
[    0.400465] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000cf9ff])
[    0.400504] PCI host bridge to bus 0000:00
[    0.400510] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.400512] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.400515] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.400518] pci_bus 0000:00: root bus resource [mem 0x000c0000-0x000c3fff]
[    0.400520] pci_bus 0000:00: root bus resource [mem 0x000c4000-0x000c7fff]
[    0.400523] pci_bus 0000:00: root bus resource [mem 0x000c8000-0x000cbfff]
[    0.400525] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff]
[    0.400528] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff]
[    0.400530] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff]
[    0.400533] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff]
[    0.400535] pci_bus 0000:00: root bus resource [mem 0x000e0000-0x000e3fff]
[    0.400538] pci_bus 0000:00: root bus resource [mem 0x000e4000-0x000e7fff]
[    0.400540] pci_bus 0000:00: root bus resource [mem 0x000e8000-0x000ebfff]
[    0.400545] pci_bus 0000:00: root bus resource [mem 0x000ec000-0x000effff]
[    0.400548] pci_bus 0000:00: root bus resource [mem 0xd0000000-0xf7ffffff]
[    0.400551] pci_bus 0000:00: root bus resource [mem 0xfc000000-0xfed3ffff]
[    0.400554] pci_bus 0000:00: root bus resource [mem 0xfed45000-0xffffffff]
[    0.400564] pci 0000:00:00.0: [1022:1410] type 00 class 0x060000
[    0.400655] pci 0000:00:01.0: [1002:9903] type 00 class 0x030000
[    0.400666] pci 0000:00:01.0: reg 10: [mem 0xd0000000-0xdfffffff pref]
[    0.400673] pci 0000:00:01.0: reg 14: [io  0x5000-0x50ff]
[    0.400680] pci 0000:00:01.0: reg 18: [mem 0xf0500000-0xf053ffff]
[    0.400721] pci 0000:00:01.0: supports D1 D2
[    0.400737] pci 0000:00:01.1: [1002:9902] type 00 class 0x040300
[    0.400747] pci 0000:00:01.1: reg 10: [mem 0xf0544000-0xf0547fff]
[    0.400795] pci 0000:00:01.1: supports D1 D2
[    0.400815] pci 0000:00:02.0: [1022:1412] type 01 class 0x060400
[    0.400865] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.400887] pci 0000:00:04.0: [1022:1414] type 01 class 0x060400
[    0.400937] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.400956] pci 0000:00:05.0: [1022:1415] type 01 class 0x060400
[    0.401006] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.401073] pci 0000:00:07.0: [1022:1417] type 01 class 0x060400
[    0.401123] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.401214] pci 0000:00:10.0: [1022:7812] type 00 class 0x0c0330
[    0.401237] pci 0000:00:10.0: reg 10: [mem 0xf0548000-0xf0549fff 64bit]
[    0.401349] pci 0000:00:10.0: PME# supported from D0 D3hot D3cold
[    0.401394] pci 0000:00:10.1: [1022:7812] type 00 class 0x0c0330
[    0.401417] pci 0000:00:10.1: reg 10: [mem 0xf054a000-0xf054bfff 64bit]
[    0.401529] pci 0000:00:10.1: PME# supported from D0 D3hot D3cold
[    0.401570] pci 0000:00:11.0: [1022:7801] type 00 class 0x010601
[    0.401589] pci 0000:00:11.0: reg 10: [io  0x5118-0x511f]
[    0.401600] pci 0000:00:11.0: reg 14: [io  0x5124-0x5127]
[    0.401611] pci 0000:00:11.0: reg 18: [io  0x5110-0x5117]
[    0.401622] pci 0000:00:11.0: reg 1c: [io  0x5120-0x5123]
[    0.401633] pci 0000:00:11.0: reg 20: [io  0x5100-0x510f]
[    0.401644] pci 0000:00:11.0: reg 24: [mem 0xf0550000-0xf05507ff]
[    0.401694] pci 0000:00:12.0: [1022:7807] type 00 class 0x0c0310
[    0.401710] pci 0000:00:12.0: reg 10: [mem 0xf054f000-0xf054ffff]
[    0.401791] pci 0000:00:12.2: [1022:7808] type 00 class 0x0c0320
[    0.402228] pci 0000:00:12.2: reg 10: [mem 0xf054e000-0xf054e0ff]
[    0.404784] pci 0000:00:12.2: supports D1 D2
[    0.404787] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.404815] pci 0000:00:13.0: [1022:7807] type 00 class 0x0c0310
[    0.404830] pci 0000:00:13.0: reg 10: [mem 0xf054d000-0xf054dfff]
[    0.404908] pci 0000:00:13.2: [1022:7808] type 00 class 0x0c0320
[    0.405340] pci 0000:00:13.2: reg 10: [mem 0xf054c000-0xf054c0ff]
[    0.407903] pci 0000:00:13.2: supports D1 D2
[    0.407906] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.407933] pci 0000:00:14.0: [1022:780b] type 00 class 0x0c0500
[    0.408018] pci 0000:00:14.2: [1022:780d] type 00 class 0x040300
[    0.408044] pci 0000:00:14.2: reg 10: [mem 0xf0540000-0xf0543fff 64bit]
[    0.408126] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.408146] pci 0000:00:14.3: [1022:780e] type 00 class 0x060100
[    0.408228] pci 0000:00:14.4: [1022:780f] type 01 class 0x060401
[    0.408280] pci 0000:00:18.0: [1022:1400] type 00 class 0x060000
[    0.408304] pci 0000:00:18.1: [1022:1401] type 00 class 0x060000
[    0.408326] pci 0000:00:18.2: [1022:1402] type 00 class 0x060000
[    0.408348] pci 0000:00:18.3: [1022:1403] type 00 class 0x060000
[    0.408376] pci 0000:00:18.4: [1022:1404] type 00 class 0x060000
[    0.408397] pci 0000:00:18.5: [1022:1405] type 00 class 0x060000
[    0.408515] pci 0000:01:00.0: [1002:6840] type 00 class 0x030000
[    0.408534] pci 0000:01:00.0: reg 10: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.408548] pci 0000:01:00.0: reg 18: [mem 0xf0400000-0xf041ffff 64bit]
[    0.408558] pci 0000:01:00.0: reg 20: [io  0x4000-0x40ff]
[    0.408574] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.408612] pci 0000:01:00.0: supports D1 D2
[    0.415178] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.415187] pci 0000:00:02.0:   bridge window [io  0x4000-0x4fff]
[    0.415192] pci 0000:00:02.0:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.415198] pci 0000:00:02.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.415253] pci 0000:02:00.0: [1969:1083] type 00 class 0x020000
[    0.415278] pci 0000:02:00.0: reg 10: [mem 0xf0300000-0xf033ffff 64bit]
[    0.415289] pci 0000:02:00.0: reg 18: [io  0x3000-0x307f]
[    0.415383] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.423165] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.423174] pci 0000:00:04.0:   bridge window [io  0x3000-0x3fff]
[    0.423179] pci 0000:00:04.0:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.423273] pci 0000:03:00.0: [168c:0034] type 00 class 0x028000
[    0.423316] pci 0000:03:00.0: reg 10: [mem 0xf0200000-0xf027ffff 64bit]
[    0.423379] pci 0000:03:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.423466] pci 0000:03:00.0: supports D1 D2
[    0.423468] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.431165] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    0.431176] pci 0000:00:05.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.431266] pci 0000:04:00.0: [10ec:5209] type 00 class 0xff0000
[    0.431295] pci 0000:04:00.0: reg 10: [mem 0xf0101000-0xf0101fff]
[    0.431357] pci 0000:04:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.431429] pci 0000:04:00.0: supports D1 D2
[    0.431432] pci 0000:04:00.0: PME# supported from D1 D2 D3hot
[    0.439161] pci 0000:00:07.0: PCI bridge to [bus 04-07]
[    0.439171] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
[    0.439176] pci 0000:00:07.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.439182] pci 0000:00:07.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.439300] pci 0000:00:14.4: PCI bridge to [bus 08-08] (subtractive decode)
[    0.439311] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.439314] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.439317] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.439320] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.439322] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.439325] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.439328] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.439330] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.439333] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.439335] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.439338] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.439340] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.439343] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.439345] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.439348] pci 0000:00:14.4:   bridge window [mem 0xd0000000-0xf7ffffff] (subtractive decode)
[    0.439351] pci 0000:00:14.4:   bridge window [mem 0xfc000000-0xfed3ffff] (subtractive decode)
[    0.439353] pci 0000:00:14.4:   bridge window [mem 0xfed45000-0xffffffff] (subtractive decode)
[    0.439419] pci_bus 0000:00: on NUMA node 0
[    0.439427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.439569] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB2_._PRT]
[    0.439618] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.439658] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.439702] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    0.439801] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.439854]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.439857]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.439859] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.449750] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.449829] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.449907] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.449983] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.450044] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.450092] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.450139] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.450186] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0
[    0.450297] vgaarb: device added: PCI:0000:00:01.0,decodes=io+mem,owns=io+mem,locks=none
[    0.450315] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=none,locks=none
[    0.450319] vgaarb: loaded
[    0.450321] vgaarb: bridge control possible 0000:01:00.0
[    0.450323] vgaarb: no bridge control possible 0000:00:01.0
[    0.450539] SCSI subsystem initialized
[    0.450622] libata version 3.00 loaded.
[    0.450647] ACPI: bus type usb registered
[    0.450672] usbcore: registered new interface driver usbfs
[    0.450683] usbcore: registered new interface driver hub
[    0.450716] usbcore: registered new device driver usb
[    0.450824] PCI: Using ACPI for IRQ routing
[    0.452909] PCI: pci_cache_line_size set to 64 bytes
[    0.453062] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
[    0.453065] e820: reserve RAM buffer [mem 0xaf9bf000-0xafffffff]
[    0.453067] e820: reserve RAM buffer [mem 0xafc00000-0xafffffff]
[    0.453070] e820: reserve RAM buffer [mem 0x22f000000-0x22fffffff]
[    0.453168] NetLabel: Initializing
[    0.453171] NetLabel:  domain hash size = 128
[    0.453172] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.453184] NetLabel:  unlabeled traffic allowed by default
[    0.453312] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.453317] hpet0: 3 comparators, 32-bit 14.318180 MHz counter
[    0.455344] Switching to clocksource hpet
[    0.464069] AppArmor: AppArmor Filesystem Enabled
[    0.464096] pnp: PnP ACPI init
[    0.464114] ACPI: bus type pnp registered
[    0.464257] pnp 00:00: [bus 00-ff]
[    0.464261] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.464265] pnp 00:00: [io  0x0d00-0xffff window]
[    0.464268] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.464270] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.464273] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.464275] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.464278] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.464280] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.464283] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.464285] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.464287] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.464290] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.464292] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.464294] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.464297] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.464299] pnp 00:00: [mem 0xd0000000-0xf7ffffff window]
[    0.464302] pnp 00:00: [mem 0xfc000000-0xfed3ffff window]
[    0.464304] pnp 00:00: [mem 0xfed45000-0xffffffff window]
[    0.464306] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.464386] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.464436] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.464439] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.464502] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.464506] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.464510] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.464718] pnp 00:02: [irq 0 disabled]
[    0.464730] pnp 00:02: [irq 8]
[    0.464733] pnp 00:02: [mem 0xfed00000-0xfed003ff]
[    0.464769] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.464869] pnp 00:03: [io  0x0000-0x000f]
[    0.464872] pnp 00:03: [io  0x0081-0x008f]
[    0.464875] pnp 00:03: [io  0x00c0-0x00df]
[    0.464878] pnp 00:03: [dma 4]
[    0.464928] pnp 00:03: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.464938] pnp 00:04: [io  0x00f0-0x00fe]
[    0.464983] pnp 00:04: [irq 13]
[    0.465037] pnp 00:04: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.465124] pnp 00:05: [io  0x0070-0x0071]
[    0.465176] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.465185] pnp 00:06: [io  0x0061]
[    0.465237] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.465264] pnp 00:07: [io  0x0060]
[    0.465267] pnp 00:07: [io  0x0064]
[    0.465318] pnp 00:07: [irq 1]
[    0.465373] pnp 00:07: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.465475] pnp 00:08: [irq 12]
[    0.465530] pnp 00:08: Plug and Play ACPI device, IDs SYN1b48 SYN1b00 SYN0002 PNP0f13 (active)
[    0.465565] pnp 00:09: [io  0x0010-0x001f]
[    0.465568] pnp 00:09: [io  0x002e-0x002f]
[    0.465570] pnp 00:09: [io  0x0072-0x0073]
[    0.465572] pnp 00:09: [io  0x0080]
[    0.465575] pnp 00:09: [io  0x00b0-0x00b1]
[    0.465577] pnp 00:09: [io  0x0092]
[    0.465579] pnp 00:09: [io  0x0400-0x04cf]
[    0.465581] pnp 00:09: [io  0x04d0-0x04d1]
[    0.465584] pnp 00:09: [io  0x04d6]
[    0.465586] pnp 00:09: [io  0x0680-0x06ff]
[    0.465588] pnp 00:09: [io  0x077a]
[    0.465590] pnp 00:09: [io  0x0c00-0x0c01]
[    0.465592] pnp 00:09: [io  0x0c14]
[    0.465594] pnp 00:09: [io  0x0c50-0x0c52]
[    0.465596] pnp 00:09: [io  0x0c6c]
[    0.465598] pnp 00:09: [io  0x0c6f]
[    0.465601] pnp 00:09: [io  0x0cd0-0x0cdb]
[    0.465603] pnp 00:09: [io  0x0840-0x0847]
[    0.465691] system 00:09: [io  0x0400-0x04cf] has been reserved
[    0.465694] system 00:09: [io  0x04d0-0x04d1] has been reserved
[    0.465697] system 00:09: [io  0x04d6] has been reserved
[    0.465700] system 00:09: [io  0x0680-0x06ff] has been reserved
[    0.465704] system 00:09: [io  0x077a] has been reserved
[    0.465707] system 00:09: [io  0x0c00-0x0c01] has been reserved
[    0.465710] system 00:09: [io  0x0c14] has been reserved
[    0.465713] system 00:09: [io  0x0c50-0x0c52] has been reserved
[    0.465716] system 00:09: [io  0x0c6c] has been reserved
[    0.465718] system 00:09: [io  0x0c6f] has been reserved
[    0.465721] system 00:09: [io  0x0cd0-0x0cdb] has been reserved
[    0.465724] system 00:09: [io  0x0840-0x0847] has been reserved
[    0.465728] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.465775] pnp 00:0a: [mem 0x000e0000-0x000fffff]
[    0.465778] pnp 00:0a: [mem 0xffc00000-0xffffffff]
[    0.465858] system 00:0a: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.465861] system 00:0a: [mem 0xffc00000-0xffffffff] has been reserved
[    0.465865] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.527427] pnp: PnP ACPI: found 11 devices
[    0.527432] ACPI: ACPI bus type pnp unregistered
[    0.527435] PnPBIOS: Disabled by ACPI PNP
[    0.557607] Freeing initrd memory: 14796k freed
[    0.565024] pci 0000:03:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.565029] pci 0000:04:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.565102] pci 0000:00:05.0: BAR 15: assigned [mem 0xf0600000-0xf06fffff pref]
[    0.565107] pci 0000:01:00.0: BAR 6: assigned [mem 0xf0420000-0xf043ffff pref]
[    0.565111] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.565114] pci 0000:00:02.0:   bridge window [io  0x4000-0x4fff]
[    0.565119] pci 0000:00:02.0:   bridge window [mem 0xf0400000-0xf04fffff]
[    0.565123] pci 0000:00:02.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.565128] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.565131] pci 0000:00:04.0:   bridge window [io  0x3000-0x3fff]
[    0.565136] pci 0000:00:04.0:   bridge window [mem 0xf0300000-0xf03fffff]
[    0.565142] pci 0000:03:00.0: BAR 6: assigned [mem 0xf0600000-0xf060ffff pref]
[    0.565145] pci 0000:00:05.0: PCI bridge to [bus 03-03]
[    0.565149] pci 0000:00:05.0:   bridge window [mem 0xf0200000-0xf02fffff]
[    0.565153] pci 0000:00:05.0:   bridge window [mem 0xf0600000-0xf06fffff pref]
[    0.565158] pci 0000:04:00.0: BAR 6: assigned [mem 0xf0000000-0xf000ffff pref]
[    0.565161] pci 0000:00:07.0: PCI bridge to [bus 04-07]
[    0.565164] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
[    0.565168] pci 0000:00:07.0:   bridge window [mem 0xf0100000-0xf01fffff]
[    0.565172] pci 0000:00:07.0:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.565176] pci 0000:00:14.4: PCI bridge to [bus 08-08]
[    0.565280] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.565282] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.565285] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.565288] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.565290] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.565293] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.565295] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.565298] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.565300] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.565303] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.565305] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.565308] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.565310] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.565313] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.565315] pci_bus 0000:00: resource 18 [mem 0xd0000000-0xf7ffffff]
[    0.565318] pci_bus 0000:00: resource 19 [mem 0xfc000000-0xfed3ffff]
[    0.565320] pci_bus 0000:00: resource 20 [mem 0xfed45000-0xffffffff]
[    0.565323] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.565326] pci_bus 0000:01: resource 1 [mem 0xf0400000-0xf04fffff]
[    0.565329] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.565331] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.565334] pci_bus 0000:02: resource 1 [mem 0xf0300000-0xf03fffff]
[    0.565337] pci_bus 0000:03: resource 1 [mem 0xf0200000-0xf02fffff]
[    0.565339] pci_bus 0000:03: resource 2 [mem 0xf0600000-0xf06fffff pref]
[    0.565342] pci_bus 0000:04: resource 0 [io  0x2000-0x2fff]
[    0.565344] pci_bus 0000:04: resource 1 [mem 0xf0100000-0xf01fffff]
[    0.565347] pci_bus 0000:04: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.565350] pci_bus 0000:08: resource 4 [io  0x0000-0x0cf7]
[    0.565352] pci_bus 0000:08: resource 5 [io  0x0d00-0xffff]
[    0.565355] pci_bus 0000:08: resource 6 [mem 0x000a0000-0x000bffff]
[    0.565357] pci_bus 0000:08: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.565360] pci_bus 0000:08: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.565362] pci_bus 0000:08: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.565365] pci_bus 0000:08: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.565367] pci_bus 0000:08: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.565370] pci_bus 0000:08: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.565372] pci_bus 0000:08: resource 13 [mem 0x000dc000-0x000dffff]
[    0.565374] pci_bus 0000:08: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.565377] pci_bus 0000:08: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.565379] pci_bus 0000:08: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.565382] pci_bus 0000:08: resource 17 [mem 0x000ec000-0x000effff]
[    0.565384] pci_bus 0000:08: resource 18 [mem 0xd0000000-0xf7ffffff]
[    0.565387] pci_bus 0000:08: resource 19 [mem 0xfc000000-0xfed3ffff]
[    0.565389] pci_bus 0000:08: resource 20 [mem 0xfed45000-0xffffffff]
[    0.565425] NET: Registered protocol family 2
[    0.565482] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.565604] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.565849] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.565981] TCP: Hash tables configured (established 131072 bind 65536)
[    0.565983] TCP: reno registered
[    0.565986] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.565994] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.566051] NET: Registered protocol family 1
[    0.566064] pci 0000:00:01.0: Boot video device
[    0.759102] PCI: CLS 64 bytes, default 64
[    0.759200] Simple Boot Flag at 0x44 set to 0x1
[    0.759658] LVT offset 0 assigned for vector 0x400
[    0.759707] perf: AMD IBS detected (0x000000ff)
[    0.760018] audit: initializing netlink socket (disabled)
[    0.760033] type=2000 audit(1366637112.656:1): initialized
[    0.784699] highmem bounce pool size: 64 pages
[    0.784711] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.787605] VFS: Disk quotas dquot_6.5.2
[    0.787661] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.788362] fuse init (API version 7.19)
[    0.788503] msgmni has been set to 1585
[    0.789119] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    0.789207] io scheduler noop registered
[    0.789211] io scheduler deadline registered (default)
[    0.789218] io scheduler cfq registered
[    0.789472] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.789491] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.791406] ACPI: AC Adapter [ACAD] (on-line)
[    0.791481] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.791486] ACPI: Power Button [PWRB]
[    0.791688] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.791692] ACPI: Sleep Button [SLPB]
[    0.791894] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input2
[    0.815165] ACPI: Lid Switch [LID]
[    0.815238] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.815243] ACPI: Power Button [PWRF]
[    0.839169] ACPI: acpi_idle registered with cpuidle
[    0.970829] ACPI: Battery Slot [BAT1] (battery absent)
[    0.970863] GHES: HEST is not enabled!
[    0.971000] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.971051] isapnp: Scanning for PnP cards...
[    0.972762] Linux agpgart interface v0.103
[    0.975243] brd: module loaded
[    0.976323] loop: module loaded
[    0.976749] Fixed MDIO Bus: probed
[    0.976801] tun: Universal TUN/TAP device driver, 1.6
[    0.976803] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.976905] PPP generic driver version 2.4.2
[    0.976955] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.976995] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.977002] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.977010] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.977039] QUIRK: Enable AMD PLL fix
[    0.977051] ehci_hcd 0000:00:12.2: debug port 1
[    0.977076] ehci_hcd 0000:00:12.2: irq 17, io mem 0xf054e000
[    0.986590] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.986620] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.986623] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.986626] usb usb1: Product: EHCI Host Controller
[    0.986629] usb usb1: Manufacturer: Linux 3.5.0-27-generic ehci_hcd
[    0.986631] usb usb1: SerialNumber: 0000:00:12.2
[    0.986831] hub 1-0:1.0: USB hub found
[    0.986837] hub 1-0:1.0: 5 ports detected
[    0.986993] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.986999] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.987008] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.987032] ehci_hcd 0000:00:13.2: debug port 1
[    0.987047] ehci_hcd 0000:00:13.2: irq 17, io mem 0xf054c000
[    0.998567] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.998601] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.998604] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.998607] usb usb2: Product: EHCI Host Controller
[    0.998610] usb usb2: Manufacturer: Linux 3.5.0-27-generic ehci_hcd
[    0.998612] usb usb2: SerialNumber: 0000:00:13.2
[    0.998817] hub 2-0:1.0: USB hub found
[    0.998822] hub 2-0:1.0: 5 ports detected
[    0.998963] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.999058] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.999065] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.999095] ohci_hcd 0000:00:12.0: irq 18, io mem 0xf054f000
[    1.034521] ACPI: Battery Slot [BAT1] (battery absent)
[    1.058464] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.058470] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.058473] usb usb3: Product: OHCI Host Controller
[    1.058476] usb usb3: Manufacturer: Linux 3.5.0-27-generic ohci_hcd
[    1.058478] usb usb3: SerialNumber: 0000:00:12.0
[    1.058634] hub 3-0:1.0: USB hub found
[    1.058688] hub 3-0:1.0: 5 ports detected
[    1.058801] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.058807] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.058827] ohci_hcd 0000:00:13.0: irq 18, io mem 0xf054d000
[    1.118361] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.118366] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.118370] usb usb4: Product: OHCI Host Controller
[    1.118372] usb usb4: Manufacturer: Linux 3.5.0-27-generic ohci_hcd
[    1.118375] usb usb4: SerialNumber: 0000:00:13.0
[    1.118576] hub 4-0:1.0: USB hub found
[    1.118631] hub 4-0:1.0: 5 ports detected
[    1.118727] uhci_hcd: USB Universal Host Controller Interface driver
[    1.118839] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.118845] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 5
[    1.119051] xhci_hcd 0000:00:10.0: irq 18, io mem 0xf0548000
[    1.119116] xhci_hcd 0000:00:10.0: irq 40 for MSI/MSI-X
[    1.119125] xhci_hcd 0000:00:10.0: irq 41 for MSI/MSI-X
[    1.119133] xhci_hcd 0000:00:10.0: irq 42 for MSI/MSI-X
[    1.119141] xhci_hcd 0000:00:10.0: irq 43 for MSI/MSI-X
[    1.119149] xhci_hcd 0000:00:10.0: irq 44 for MSI/MSI-X
[    1.119254] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    1.119257] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.119259] usb usb5: Product: xHCI Host Controller
[    1.119262] usb usb5: Manufacturer: Linux 3.5.0-27-generic xhci_hcd
[    1.119264] usb usb5: SerialNumber: 0000:00:10.0
[    1.119343] xHCI xhci_add_endpoint called for root hub
[    1.119345] xHCI xhci_check_bandwidth called for root hub
[    1.119370] hub 5-0:1.0: USB hub found
[    1.119381] hub 5-0:1.0: 2 ports detected
[    1.119446] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.119450] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    1.122454] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[    1.122457] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.122459] usb usb6: Product: xHCI Host Controller
[    1.122462] usb usb6: Manufacturer: Linux 3.5.0-27-generic xhci_hcd
[    1.122464] usb usb6: SerialNumber: 0000:00:10.0
[    1.122543] xHCI xhci_add_endpoint called for root hub
[    1.122545] xHCI xhci_check_bandwidth called for root hub
[    1.122569] hub 6-0:1.0: USB hub found
[    1.122590] hub 6-0:1.0: 2 ports detected
[    1.309999] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.360701] isapnp: No Plug & Play device found
[    1.370043] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.370055] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 7
[    1.370257] xhci_hcd 0000:00:10.1: irq 17, io mem 0xf054a000
[    1.370323] xhci_hcd 0000:00:10.1: irq 45 for MSI/MSI-X
[    1.370332] xhci_hcd 0000:00:10.1: irq 46 for MSI/MSI-X
[    1.370340] xhci_hcd 0000:00:10.1: irq 47 for MSI/MSI-X
[    1.370348] xhci_hcd 0000:00:10.1: irq 48 for MSI/MSI-X
[    1.370356] xhci_hcd 0000:00:10.1: irq 49 for MSI/MSI-X
[    1.370467] usb usb7: New USB device found, idVendor=1d6b, idProduct=0002
[    1.370470] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.370473] usb usb7: Product: xHCI Host Controller
[    1.370476] usb usb7: Manufacturer: Linux 3.5.0-27-generic xhci_hcd
[    1.370478] usb usb7: SerialNumber: 0000:00:10.1
[    1.370663] xHCI xhci_add_endpoint called for root hub
[    1.370666] xHCI xhci_check_bandwidth called for root hub
[    1.370697] hub 7-0:1.0: USB hub found
[    1.370750] hub 7-0:1.0: 2 ports detected
[    1.370827] xhci_hcd 0000:00:10.1: xHCI Host Controller
[    1.370831] xhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 8
[    1.373664] usb usb8: New USB device found, idVendor=1d6b, idProduct=0003
[    1.373667] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.373670] usb usb8: Product: xHCI Host Controller
[    1.373672] usb usb8: Manufacturer: Linux 3.5.0-27-generic xhci_hcd
[    1.373674] usb usb8: SerialNumber: 0000:00:10.1
[    1.373760] xHCI xhci_add_endpoint called for root hub
[    1.373762] xHCI xhci_check_bandwidth called for root hub
[    1.373788] hub 8-0:1.0: USB hub found
[    1.373805] hub 8-0:1.0: 2 ports detected
[    1.374111] usbcore: registered new interface driver libusual
[    1.374164] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS0] at 0x60,0x64 irq 1,12
[    1.386437] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.386445] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.386662] mousedev: PS/2 mouse device common for all mice
[    1.386904] rtc_cmos 00:05: RTC can wake from S4
[    1.387035] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.387061] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    1.387123] device-mapper: uevent: version 1.0.3
[    1.387201] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.387237] EISA: Probing bus 0 at eisa.0
[    1.387240] EISA: Cannot allocate resource for mainboard
[    1.387242] Cannot allocate resource for EISA slot 1
[    1.387244] Cannot allocate resource for EISA slot 2
[    1.387245] Cannot allocate resource for EISA slot 3
[    1.387247] Cannot allocate resource for EISA slot 4
[    1.387248] Cannot allocate resource for EISA slot 5
[    1.387250] Cannot allocate resource for EISA slot 6
[    1.387251] Cannot allocate resource for EISA slot 7
[    1.387253] Cannot allocate resource for EISA slot 8
[    1.387254] EISA: Detected 0 cards.
[    1.387369] cpuidle: using governor ladder
[    1.387509] cpuidle: using governor menu
[    1.387511] EFI Variables Facility v0.08 2004-May-17
[    1.387818] ashmem: initialized
[    1.387968] TCP: cubic registered
[    1.388089] NET: Registered protocol family 10
[    1.388286] NET: Registered protocol family 17
[    1.388302] Key type dns_resolver registered
[    1.388356] Using IPI No-Shortcut mode
[    1.388576] PM: Hibernation image not present or could not be loaded.
[    1.388588] registered taskstats version 1
[    1.392175] Key type trusted registered
[    1.394814] Key type encrypted registered
[    1.397472] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.398058]   Magic number: 9:393:433
[    1.398196] rtc_cmos 00:05: setting system clock to 2013-04-22 13:25:13 UTC (1366637113)
[    1.398288] powernow-k8: Found 1 AMD A8-4500M APU with Radeon(tm) HD Graphics    (4 cpu cores) (version 2.20.00)
[    1.398314] powernow-k8: Core Performance Boosting: on.
[    1.398377] powernow-k8:    0 : pstate 0 (1900 MHz)
[    1.398379] powernow-k8:    1 : pstate 1 (1800 MHz)
[    1.398381] powernow-k8:    2 : pstate 2 (1700 MHz)
[    1.398383] powernow-k8:    3 : pstate 3 (1600 MHz)
[    1.398384] powernow-k8:    4 : pstate 4 (1400 MHz)
[    1.398982] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.398985] EDD information not available.
[    1.399305] Freeing unused kernel memory: 756k freed
[    1.399709] Write protecting the kernel text: 5960k
[    1.399742] Write protecting the kernel read-only data: 2412k
[    1.399744] NX-protecting the kernel data: 4280k
[    1.429458] udevd[100]: starting version 175
[    1.509105] usb 2-1: New USB device found, idVendor=1bcf, idProduct=2c18
[    1.509112] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.509116] usb 2-1: Product: HD Webcam
[    1.509120] usb 2-1: Manufacturer: NC.21411.00221729B2FLM0007
[    1.520080] Compat-wireless backport release: compat-wireless-v3.6.2-1-snpc
[    1.520084] Backport based on linux-stable.git v3.6.2
[    1.520086] compat.git: linux-stable.git
[    1.522106] rtsx_pci 0000:04:00.0: irq 50 for MSI/MSI-X
[    1.522171] rtsx_pci 0000:04:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 50
[    1.525247] ahci 0000:00:11.0: version 3.0
[    1.525902] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 2 ports 6 Gbps 0x3 impl SATA mode
[    1.525908] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part 
[    1.526638] scsi0 : ahci
[    1.526809] scsi1 : ahci
[    1.549694] ata1: SATA max UDMA/133 abar m2048@0xf0550000 port 0xf0550100 irq 19
[    1.549702] ata2: SATA max UDMA/133 abar m2048@0xf0550000 port 0xf0550180 irq 19
[    1.554852] atl1c 0000:02:00.0: version 1.0.1.0-NAPI
[    1.757283] Refined TSC clocksource calibration: 1896.549 MHz.
[    1.757290] Switching to clocksource tsc
[    1.869101] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.869142] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.870686] ata1.00: ATA-8: Hitachi HTS547575A9E384, JE4OA60A, max UDMA/133
[    1.870691] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.872367] ata1.00: configured for UDMA/133
[    1.872395] ata2.00: ATAPI: HL-DT-ST DVDRAM GT70N, YP10, max UDMA/133
[    1.872762] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54757 JE4O PQ: 0 ANSI: 5
[    1.872943] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.872947] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.873003] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.873017] sd 0:0:0:0: [sda] Write Protect is off
[    1.873022] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.873047] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.875359] ata2.00: configured for UDMA/133
[    1.960766]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    1.961481] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.964999] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GT70N     YP10 PQ: 0 ANSI: 5
[    1.971440] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.971446] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.971660] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.971755] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.992872] usb 4-4: new full-speed USB device number 2 using ohci_hcd
[    2.165721] usb 4-4: string descriptor 0 read error: -22
[    2.165729] usb 4-4: New USB device found, idVendor=04ca, idProduct=3006
[    2.165733] usb 4-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.276403] usb 5-1: new full-speed USB device number 2 using xhci_hcd
[    2.325567] usb 5-1: New USB device found, idVendor=09da, idProduct=9090
[    2.325572] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.325576] usb 5-1: Product: USB Device
[    2.325578] usb 5-1: Manufacturer: A4TECH
[    2.366658] usbcore: registered new interface driver usbhid
[    2.366663] usbhid: USB HID core driver
[    2.369747] input: A4TECH USB Device as /devices/pci0000:00/0000:00:10.0/usb5/5-1/5-1:1.0/input/input5
[    2.370343] hid-generic 0003:09DA:9090.0001: input,hiddev0,hidraw0: USB HID v1.11 Keyboard [A4TECH USB Device] on usb-0000:00:10.0-1/input0
[    2.370549] input: A4TECH USB Device as /devices/pci0000:00/0000:00:10.0/usb5/5-1/5-1:1.1/input/input6
[    2.370690] hid-generic 0003:09DA:9090.0002: input,hidraw1: USB HID v1.11 Mouse [A4TECH USB Device] on usb-0000:00:10.0-1/input1
[    2.855439] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   24.025328] Adding 7839740k swap on /dev/sda6.  Priority:-1 extents:1 across:7839740k 
[   24.035982] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.099922] udevd[337]: starting version 175
[   24.212039] cfg80211: Calling CRDA to update world regulatory domain
[   24.213617] [drm] Initialized drm 1.1.0 20060810
[   24.222731] ACPI Warning: 0x00000b00-0x00000b07 SystemIO conflicts with Region \_SB_.PCI0.SMBS.SMB0 1 (20120320/utaddress-251)
[   24.222744] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   24.236279] [drm] radeon defaulting to kernel modesetting.
[   24.236284] [drm] radeon kernel modesetting enabled.
[   24.236294] lp: driver loaded but no devices found
[   24.236472] VGA switcheroo: detected switching method \_SB_.PCI0.VGA_.ATPX handle
[   24.236958] [drm] initializing kernel modesetting (ARUBA 0x1002:0x9903 0x1025:0x0697).
[   24.237040] [drm] register mmio base: 0xF0500000
[   24.237045] [drm] register mmio size: 262144
[   24.239340] ATOM BIOS: Acer
[   24.239390] radeon 0000:00:01.0: VRAM: 512M 0x0000000000000000 - 0x000000001FFFFFFF (512M used)
[   24.239396] radeon 0000:00:01.0: GTT: 512M 0x0000000020000000 - 0x000000003FFFFFFF
[   24.240142] [drm] Detected VRAM RAM=512M, BAR=256M
[   24.240146] [drm] RAM width 64bits DDR
[   24.245892] [TTM] Zone  kernel: Available graphics memory: 406282 kiB
[   24.245896] [TTM] Zone highmem: Available graphics memory: 3870350 kiB
[   24.245900] [TTM] Initializing pool allocator
[   24.245909] [TTM] Initializing DMA pool allocator
[   24.245943] [drm] radeon: 512M of VRAM memory ready
[   24.245946] [drm] radeon: 512M of GTT memory ready.
[   24.245968] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   24.245971] [drm] Driver supports precise vblank timestamp query.
[   24.246021] radeon 0000:00:01.0: irq 51 for MSI/MSI-X
[   24.246039] radeon 0000:00:01.0: radeon: using MSI.
[   24.246619] [drm] radeon: irq initialized.
[   24.246626] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   24.249200] [drm] Loading ARUBA Microcode
[   24.278834] type=1400 audit(1366633536.416:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=515 comm="apparmor_parser"
[   24.279474] type=1400 audit(1366633536.416:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=515 comm="apparmor_parser"
[   24.279805] type=1400 audit(1366633536.416:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=515 comm="apparmor_parser"
[   24.300868] ath: phy0: ASPM enabled: 0x43
[   24.300874] ath: EEPROM regdomain: 0x6a
[   24.300876] ath: EEPROM indicates we should expect a direct regpair map
[   24.300880] ath: Country alpha2 being used: 00
[   24.300882] ath: Regpair used: 0x6a
[   24.300886] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   24.300889] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300892] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   24.300895] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300897] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   24.300900] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300902] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   24.300905] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300908] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   24.300911] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300914] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   24.300917] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300920] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   24.300924] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300926] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   24.300929] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300932] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   24.300935] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300938] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   24.300942] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300945] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   24.300948] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300951] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   24.300955] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300957] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   24.300960] cfg80211: 2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   24.300963] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   24.300966] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   24.300969] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.300973] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   24.300976] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.300979] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   24.300982] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.300985] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   24.300988] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.300991] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   24.300994] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.300997] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   24.301000] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301003] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   24.301007] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301010] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   24.301012] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301015] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[   24.301017] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301020] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[   24.301023] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301025] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[   24.301028] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301030] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[   24.301033] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301036] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[   24.301039] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301042] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[   24.301046] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301050] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[   24.301053] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301055] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[   24.301059] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301062] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[   24.301065] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301068] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[   24.301071] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301073] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[   24.301077] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301080] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   24.301082] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301085] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   24.301088] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301092] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   24.301096] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301099] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   24.301103] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301106] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   24.301110] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   24.301943] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   24.310286] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   24.310724] Registered led device: ath9k-phy0
[   24.310736] ieee80211 phy0: Atheros AR9462 Rev:2 mem=0xf8d00000, irq=17
[   24.342600] wmi: Mapper loaded
[   24.421437] Linux video capture interface: v2.00
[   24.423254] uvcvideo: Found UVC 1.00 device HD Webcam (1bcf:2c18)
[   24.430349] microcode: CPU0: patch_level=0x0600110f
[   24.431631] input: HD Webcam as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input7
[   24.431742] usbcore: registered new interface driver uvcvideo
[   24.431745] USB Video Class driver (1.1.1)
[   24.473951] Bluetooth: Core ver 2.16
[   24.474017] NET: Registered protocol family 31
[   24.474020] Bluetooth: HCI device and connection manager initialized
[   24.474024] Bluetooth: HCI socket layer initialized
[   24.474027] Bluetooth: L2CAP socket layer initialized
[   24.474034] Bluetooth: SCO socket layer initialized
[   24.536974] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   24.536981] cfg80211: World regulatory domain updated:
[   24.536984] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   24.536987] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.536991] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.536993] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   24.536997] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.536999] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   24.557871] acpi device:01: registered as cooling_device4
[   24.557914] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.558022] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   24.573693] acpi device:05: registered as cooling_device5
[   24.573730] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[   24.573812] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:03/LNXVIDEO:01/input/input9
[   24.585145] microcode: failed to load file amd-ucode/microcode_amd_fam15h.bin
[   24.585199] microcode: CPU1: patch_level=0x0600110f
[   24.587737] microcode: failed to load file amd-ucode/microcode_amd_fam15h.bin
[   24.587837] microcode: CPU2: patch_level=0x0600110f
[   24.589983] microcode: failed to load file amd-ucode/microcode_amd_fam15h.bin
[   24.590035] microcode: CPU3: patch_level=0x0600110f
[   24.592512] microcode: failed to load file amd-ucode/microcode_amd_fam15h.bin
[   24.592817] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   24.603330] kvm: Nested Virtualization enabled
[   24.603336] kvm: Nested Paging enabled
[   24.619136] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   24.619256] radeon 0000:00:01.0: WB enabled
[   24.619260] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000020000c00 and cpu addr 0xffc77c00
[   24.619264] radeon 0000:00:01.0: fence driver on ring 1 use gpu addr 0x0000000020000c04 and cpu addr 0xffc77c04
[   24.619267] radeon 0000:00:01.0: fence driver on ring 2 use gpu addr 0x0000000020000c08 and cpu addr 0xffc77c08
[   24.638120] [drm] ring test on 0 succeeded in 2 usecs
[   24.638782] [drm] ib test on ring 0 succeeded in 0 usecs
[   24.650775] [drm] radeon atom DIG backlight initialized
[   24.650781] [drm] Radeon Display Connectors
[   24.650783] [drm] Connector 0:
[   24.650785] [drm]   eDP-1
[   24.650787] [drm]   HPD1
[   24.650789] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[   24.650791] [drm]   Encoders:
[   24.650793] [drm]     LCD1: INTERNAL_UNIPHY2
[   24.650794] [drm] Connector 1:
[   24.650796] [drm]   VGA-1
[   24.650797] [drm]   HPD2
[   24.650800] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[   24.650801] [drm]   Encoders:
[   24.650802] [drm]     CRT1: INTERNAL_UNIPHY2
[   24.650804] [drm]     CRT1: NUTMEG
[   24.650805] [drm] Connector 2:
[   24.650807] [drm]   HDMI-A-1
[   24.650808] [drm]   HPD3
[   24.650810] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[   24.650811] [drm]   Encoders:
[   24.650813] [drm]     DFP1: INTERNAL_UNIPHY
[   24.703078] [drm] Internal thermal controller without fan control
[   24.703105] [drm] radeon: power management initialized
[   24.731973] usb 4-4: USB disconnect, device number 2
[   24.732984] usbcore: registered new interface driver ath3k
[   24.768856] btusb: disagrees about version of symbol hci_free_dev
[   24.768860] btusb: Unknown symbol hci_free_dev (err -22)
[   24.768890] btusb: disagrees about version of symbol hci_alloc_dev
[   24.768892] btusb: Unknown symbol hci_alloc_dev (err -22)
[   24.768909] btusb: disagrees about version of symbol hci_unregister_dev
[   24.768911] btusb: Unknown symbol hci_unregister_dev (err -22)
[   24.768925] btusb: disagrees about version of symbol hci_recv_fragment
[   24.768927] btusb: Unknown symbol hci_recv_fragment (err -22)
[   24.768931] btusb: disagrees about version of symbol hci_register_dev
[   24.768933] btusb: Unknown symbol hci_register_dev (err -22)
[   24.769011] btusb: disagrees about version of symbol hci_free_dev
[   24.769017] btusb: Unknown symbol hci_free_dev (err -22)
[   24.769045] btusb: disagrees about version of symbol hci_alloc_dev
[   24.769048] btusb: Unknown symbol hci_alloc_dev (err -22)
[   24.769065] btusb: disagrees about version of symbol hci_unregister_dev
[   24.769067] btusb: Unknown symbol hci_unregister_dev (err -22)
[   24.769080] btusb: disagrees about version of symbol hci_recv_fragment
[   24.769084] btusb: Unknown symbol hci_recv_fragment (err -22)
[   24.769090] btusb: disagrees about version of symbol hci_register_dev
[   24.769092] btusb: Unknown symbol hci_register_dev (err -22)
[   24.939608] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   25.169432] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xa40000/0xa0400
[   25.189118] init: failsafe main process (924) killed by TERM signal
[   25.227004] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   25.269347] ppdev: user-space parallel port driver
[   25.324589] type=1400 audit(1366633537.460:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=998 comm="apparmor_parser"
[   25.325350] type=1400 audit(1366633537.464:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=998 comm="apparmor_parser"
[   25.355709] type=1400 audit(1366633537.492:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1025 comm="apparmor_parser"
[   25.356460] type=1400 audit(1366633537.492:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1025 comm="apparmor_parser"
[   25.356878] type=1400 audit(1366633537.496:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1025 comm="apparmor_parser"
[   25.359932] type=1400 audit(1366633537.496:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1024 comm="apparmor_parser"
[   25.360424] type=1400 audit(1366633537.496:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1024 comm="apparmor_parser"
[   25.387588] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.387592] Bluetooth: BNEP filters: protocol multicast
[   25.405850] Bluetooth: RFCOMM TTY layer initialized
[   25.405857] Bluetooth: RFCOMM socket layer initialized
[   25.405859] Bluetooth: RFCOMM ver 1.11
[   25.496611] usb 4-4: new full-speed USB device number 3 using ohci_hcd
[   25.521871] atl1c 0000:02:00.0: irq 52 for MSI/MSI-X
[   25.542832] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.545345] vboxdrv: Found 4 processor cores.
[   25.550070] vboxdrv: fAsync=0 offMin=0x4fb offMax=0x16d0
[   25.550166] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   25.550169] vboxdrv: Successfully loaded version 4.1.18_Ubuntu (interface 0x00190000).
[   25.561146] init: alsa-restore main process (1083) terminated with status 19
[   25.603258] vboxpci: IOMMU not found (not registered)
[   25.681128] usb 4-4: string descriptor 0 read error: -22
[   25.681184] usb 4-4: New USB device found, idVendor=04ca, idProduct=3006
[   25.681187] usb 4-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   25.875120] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.901273] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.911759] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.916080] ACPI Error: [SSZE] Namespace lookup failure, AE_ALREADY_EXISTS (20120320/dsfield-143)
[   25.916088] ACPI Error: Method parse/execution failed [\_SB_.ACAD._PSR] (Node f74436f0), AE_ALREADY_EXISTS (20120320/psparse-536)
[   25.916101] ACPI Exception: AE_ALREADY_EXISTS, Error reading AC Adapter state (20120320/ac-118)
[   25.941954] btusb: disagrees about version of symbol hci_free_dev
[   25.941960] btusb: Unknown symbol hci_free_dev (err -22)
[   25.941990] btusb: disagrees about version of symbol hci_alloc_dev
[   25.941992] btusb: Unknown symbol hci_alloc_dev (err -22)
[   25.942012] btusb: disagrees about version of symbol hci_unregister_dev
[   25.942014] btusb: Unknown symbol hci_unregister_dev (err -22)
[   25.942031] btusb: disagrees about version of symbol hci_recv_fragment
[   25.942033] btusb: Unknown symbol hci_recv_fragment (err -22)
[   25.942038] btusb: disagrees about version of symbol hci_register_dev
[   25.942040] btusb: Unknown symbol hci_register_dev (err -22)
[   25.942116] btusb: disagrees about version of symbol hci_free_dev
[   25.942119] btusb: Unknown symbol hci_free_dev (err -22)
[   25.942153] btusb: disagrees about version of symbol hci_alloc_dev
[   25.942156] btusb: Unknown symbol hci_alloc_dev (err -22)
[   25.942177] btusb: disagrees about version of symbol hci_unregister_dev
[   25.942180] btusb: Unknown symbol hci_unregister_dev (err -22)
[   25.942197] btusb: disagrees about version of symbol hci_recv_fragment
[   25.942199] btusb: Unknown symbol hci_recv_fragment (err -22)
[   25.942204] btusb: disagrees about version of symbol hci_register_dev
[   25.942206] btusb: Unknown symbol hci_register_dev (err -22)
[   25.946072] ACPI: Marking method _PSR as Serialized because of AE_ALREADY_EXISTS error
[   26.030642] [drm] fb mappable at 0xD1144000
[   26.030648] [drm] vram apper at 0xD0000000
[   26.030651] [drm] size 4325376
[   26.030654] [drm] fb depth is 24
[   26.030657] [drm]    pitch is 5632
[   26.030851] fbcon: radeondrmfb (fb0) is primary device
[   26.626567] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   26.628807] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   26.653515] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0
[   26.786861] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   26.788582] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   28.309124] Console: switching to colour frame buffer device 170x48
[   28.313787] fb0: radeondrmfb frame buffer device
[   28.313788] drm: registered panic notifier
[   28.315979] [drm] Initialized radeon 2.18.0 20080528 for 0000:00:01.0 on minor 0
[   28.316050] radeon 0000:01:00.0: enabling device (0000 -> 0003)
[   28.316517] hda-intel: Force to non-snoop mode
[   28.316525] [drm] initializing kernel modesetting (TURKS 0x1002:0x6840 0x1025:0x0697).
[   28.316565] [drm] register mmio base: 0xF0400000
[   28.316567] [drm] register mmio size: 131072
[   28.316571] vga_switcheroo: enabled
[   28.316613] snd_hda_intel 0000:00:01.1: irq 53 for MSI/MSI-X
[   28.316761] radeon atpx: version is 1
[   28.598073] ATOM BIOS: Acer
[   28.598122] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   28.598126] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[   28.598769] [drm] Detected VRAM RAM=1024M, BAR=256M
[   28.598774] [drm] RAM width 128bits DDR
[   28.598800] [drm] radeon: 1024M of VRAM memory ready
[   28.598802] [drm] radeon: 512M of GTT memory ready.
[   28.598820] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   28.598821] [drm] Driver supports precise vblank timestamp query.
[   28.598871] radeon 0000:01:00.0: irq 54 for MSI/MSI-X
[   28.598888] radeon 0000:01:00.0: radeon: using MSI.
[   28.598980] [drm] radeon: irq initialized.
[   28.598986] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   28.599762] [drm] Loading TURKS Microcode
[   28.610641] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   28.610786] radeon 0000:01:00.0: WB enabled
[   28.610791] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffcb2c00
[   28.627085] [drm] ring test on 0 succeeded in 1 usecs
[   28.627328] [drm] ib test on ring 0 succeeded in 0 usecs
[   28.627639] [drm] Radeon Display Connectors
[   28.635134] [drm] Internal thermal controller without fan control
[   28.636155] [drm] radeon: power management initialized
[   28.636351] No connectors reported connected with modes
[   28.636354] [drm] Cannot find any crtc or sizes - going 1024x768
[   28.637647] [drm] fb mappable at 0xE0142000
[   28.637649] [drm] vram apper at 0xE0000000
[   28.637651] [drm] size 3145728
[   28.637653] [drm] fb depth is 24
[   28.637654] [drm]    pitch is 4096
[   28.637817] fb1: radeondrmfb frame buffer device
[   28.637964] [drm] Initialized radeon 2.18.0 20080528 for 0000:01:00.0 on minor 1
[   28.838006] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.1/sound/card0/input11
[   28.838383] snd_hda_intel 0000:00:14.2: irq 55 for MSI/MSI-X
[   28.884526] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card1/input12
[   28.884650] input: HD-Audio Generic Headphone as /devices/pci0000:00/0000:00:14.2/sound/card1/input13
[   29.546692] init: plymouth-splash main process (2385) terminated with status 2
[   31.104434] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   31.104439] vgaarb: device changed decodes: PCI:0000:00:01.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   33.560619] wlan0: authenticate with 00:05:ca:92:85:38
[   33.564858] wlan0: send auth to 00:05:ca:92:85:38 (try 1/3)
[   33.566456] wlan0: authenticated
[   33.574395] wlan0: associate with 00:05:ca:92:85:38 (try 1/3)
[   33.582189] wlan0: RX AssocResp from 00:05:ca:92:85:38 (capab=0xc31 status=0 aid=2)
[   33.582273] wlan0: associated
[   33.582494] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

---

### Post by chili555 on 2013-04-22
> [   25.941954] btusb: disagrees about version of symbol hci_free_dev
[   25.941960] btusb: Unknown symbol hci_free_dev (err -22)
[   25.941990] btusb: disagrees about version of symbol hci_alloc_dev
[   25.941992] btusb: Unknown symbol hci_alloc_dev (err -22)
[   25.942012] btusb: disagrees about version of symbol hci_unregister_dev
[   25.942014] btusb: Unknown symbol hci_unregister_dev (err -22)
[   25.942031] btusb: disagrees about version of symbol hci_recv_fragment
[   25.942033] btusb: Unknown symbol hci_recv_fragment (err -22)
[   25.942038] btusb: disagrees about version of symbol hci_register_dev
[   25.942040] btusb: Unknown symbol hci_register_dev (err -22)
[   25.942116] btusb: disagrees about version of symbol hci_free_dev
[   25.942119] btusb: Unknown symbol hci_free_dev (err -22)What did you compile and/or modify to get this? Did you try the compat-wireless package? Does your bluetooth device show up here?```
lsusb
```

---

### Post by Inamati on 2013-04-22
I have no idea what happened.

lsusb gives:
```
Bus 002 Device 002: ID 1bcf:2c18 Sunplus Innovation Technology Inc. Bus 004 Device 002: ID 04ca:3006 Lite-On Technology Corp. 
Bus 005 Device 002: ID 09da:9090 A4 Tech Co., Ltd XL-750BK Laser Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
```

---

### Post by chili555 on 2013-04-22
> **Inamati said:**
> I have no idea what happened.You have no idea if you did or did not attempt to modify and compile compat-wireless as suggested in the link you provided? Or you did nothing at all and these errors appeared? Or...what??

This appears to be your bluetooth device:> Bus 004 Device 002: ID 04ca:3006 Lite-On Technology Corp. On my 13.04 system, the device is supported by ath3k. Your device ID is not in ath3k for 12.10 and earlier. You might burn the live CD for 13.04 and try it out.

---

### Post by Inamati on 2013-04-22
I believe it happened after I compiled something in those links but I can't remember what. 13.04 comes out in three days hopefully it will solve the problem if not I'll report back.

---

### Post by chili555 on 2013-04-22
Indeed. And in three days, the servers will be clogged and you won't get a decent download time for a week or so. On the other hand, if you choose to download it today, I am confident you'll have smooth sailing. That's why I already have it!!

---

### Post by Inamati on 2013-04-22
> **chili555 said:**
> Indeed. And in three days, the servers will be clogged and you won't get a decent download time for a week or so. On the other hand, if you choose to download it today, I am confident you'll have smooth sailing. That's why I already have it!!

Good point. Lol. Just tell me something the version that's up for download is missing stuff right? They will still make changes or is it like the final version?

---

### Post by chili555 on 2013-04-22
The version that is up right now is not missing anything I know of. There have been a couple of updates in the ten days or so that I've run it, but there would have been in 12.10 as well, I'd guess. The advantage of running the live CD is that you can check off your must-haves before you install: Graphics? Check! Wireless? Check! BT? Check! Etc.

---

### Post by Inamati on 2013-04-26
Ok so with ubuntu 13.04 I can detect and be detected by other devices but can't send or receive files. Any idea?

---

### Post by chili555 on 2013-04-26
> **Inamati said:**
> Ok so with ubuntu 13.04 I can detect and be detected by other devices but can't send or receive files. Any idea?Frankly, I was over my head finding and activating a driver! I have no further suggestions.

---

### Post by Inamati on 2013-04-26
> **chili555 said:**
> Frankly, I was over my head finding and activating a driver! I have no further suggestions.

Ok will search and report back

---

### Post by Inamati on 2013-04-26
OK got it. I couldn't received because I didn't have the receive files in folder option set in personal sharing but after that I still couldn't send just receive so I installed blueman and removed gnome-bluetooth and now everything works fine. Sends and received without issue. Problem solved.

---

### Post by Inamati on 2013-04-26
How do I mark the thread solved?

---

### Post by chili555 on 2013-04-26
Glad it'sworking. I believe you edit the title of the thread and change it from:> Bluetooth not working in Acer aspire V3-551G with AR9462 card....to:> [SOLVED]Bluetooth not working in Acer aspire V3-551G with AR9462 card.

---

### Post by Inamati on 2013-04-27
> **chili555 said:**
> Glad it'sworking. I believe you edit the title of the thread and change it from:...to:

Nope. You choose edit post and then go advanced and you change the prefix to solved.

---

### Post by Espionage724 on 2013-08-20
Not sure if I have the same card or not, but I do have an Aspire V3-551G-X419.

Bluetooth can be toggled with the Wireless button (F3) + Fn keys. Pattern is as followed:

Wireless Off, Bluetooth On
Wireless On, Bluetooth Off
Wireless On, Bluetooth On
Wireless Off, Bluetooth Off

Almost certain the Wireless LED (4th light; orange) only reflects the actual Wireless card state, and not Bluetooth (so if the light is off, Wireless is off).

I didn't see any manual with my laptop that mentioned this behavior; just something I found out. Might help someone out or something.

---

