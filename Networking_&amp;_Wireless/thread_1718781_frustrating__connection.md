---
title: "frustrating  connection"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by Rakeshvijayan on 2011-03-31
Hi friends 

I am new in connecting wireless and configuring such peripherals.so I expecting help from all  who read this post ,because I wandered on Internet  since three days for the solution  .
My issue is I have a Dlink DWA-510 divice in my desktop meachine .Before installing the ubuntu Os windows7 was used and works fine  I changed it to ubuntu 10.10 .I thought it will automatically ditect the wireless divice attached to the pci card .when I use the command ifconfig it  shows only the eth0 ,lo,and vertualbox adapter .I cant see the wlan device 

help me me:mad:

---

### Post by Rakeshvijayan on 2011-04-01
```

mac@mac-System-Product-Name:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
```

---

### Post by Rakeshvijayan on 2011-04-01
command: lsusb

```
lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

---

### Post by Rakeshvijayan on 2011-04-01
ifconfig ```
ifconfig
eth0      Link encap:Ethernet  HWaddr 20:cf:30:c9:10:f3  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fec9:10f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3295 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2812160 (2.8 MB)  TX bytes:695631 (695.6 KB)
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6062 (6.0 KB)  TX bytes:6062 (6.0 KB)
```command :iwconfig ```
mac@mac-System-Product-Name:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

```command :iwconfig wlan0```
iwconfig wlan0
wlan0     No such device

```command lsmod :```
lsmod 
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  30022  1 
binfmt_misc             6599  1 
vboxnetadp              6911  0 
vboxnetflt             18625  0 
vboxdrv               213743  2 vboxnetadp,vboxnetflt
snd_hda_codec_realtek   217980  1 
i915                  290938  3 
snd_hda_intel          22107  4 
drm_kms_helper         30200  1 i915
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
drm                   168054  4 i915,drm_kms_helper
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
parport_pc             26058  1 
psmouse                59033  0 
asus_atk0110           11423  0 
snd                    49006  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw               4022  0 
led_class               2633  0 
intel_agp              26360  2 i915
lp                      7342  0 
soundcore                880  1 snd
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
parport                31492  3 ppdev,parport_pc,lp
r8169                  36489  0 
mii                     4425  1 r8169

```command :dmesg ```
[    0.152496] devtmpfs: initialized
[    0.152745] regulator: core version 0.5
[    0.152766] Time:  4:00:55  Date: 04/01/11
[    0.152799] NET: Registered protocol family 16
[    0.152816] Trying to unpack rootfs image as initramfs...
[    0.152896] EISA bus registered
[    0.152902] ACPI: bus type pci registered
[    0.152962] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.152965] PCI: not using MMCONFIG
[    0.153117] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=3
[    0.153118] PCI: Using configuration type 1 for base access
[    0.160284] bio: create slab <bio-0> at 0
[    0.161269] ACPI: EC: Look up EC in DSDT
[    0.162840] ACPI: Executed 1 blocks of module-level executable AML code
[    0.169707] ACPI: SSDT bf6a00f0 00298 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    0.170020] ACPI: Dynamic OEM Table Load:
[    0.170023] ACPI: SSDT (null) 00298 (v01    AMI   CPU1PM 00000001 INTL 20060113)
[    0.170313] ACPI: SSDT bf6a0390 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    0.170616] ACPI: Dynamic OEM Table Load:
[    0.170619] ACPI: SSDT (null) 00143 (v01    AMI   CPU2PM 00000001 INTL 20060113)
[    0.170684] ACPI: Interpreter enabled
[    0.170688] ACPI: (supports S0 S1 S3 S4 S5)
[    0.170709] ACPI: Using IOAPIC for interrupt routing
[    0.170758] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf0000000-0xf3ffffff] (base 0xf0000000)
[    0.172715] PCI: MMCONFIG at [mem 0xf0000000-0xf3ffffff] reserved in ACPI motherboard resources
[    0.172717] PCI: Using MMCONFIG for extended config space
[    0.180542] ACPI: No dock devices found.
[    0.180547] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.180647] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.180845] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.180847] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.180849] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.180851] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.180853] pci_root PNP0A08:00: host bridge window [mem 0xbf700000-0xffffffff]
[    0.180915] pci 0000:00:02.0: reg 10: [mem 0xfe980000-0xfe9fffff]
[    0.180920] pci 0000:00:02.0: reg 14: [io  0xdc00-0xdc07]
[    0.180924] pci 0000:00:02.0: reg 18: [mem 0xe0000000-0xefffffff pref]
[    0.180928] pci 0000:00:02.0: reg 1c: [mem 0xfe800000-0xfe8fffff]
[    0.180992] pci 0000:00:1b.0: reg 10: [mem 0xfe978000-0xfe97bfff 64bit]
[    0.181029] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.181032] pci 0000:00:1b.0: PME# disabled
[    0.181090] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.181093] pci 0000:00:1c.0: PME# disabled
[    0.181153] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.181156] pci 0000:00:1c.1: PME# disabled
[    0.181200] pci 0000:00:1d.0: reg 20: [io  0xd400-0xd41f]
[    0.181244] pci 0000:00:1d.1: reg 20: [io  0xd480-0xd49f]
[    0.181286] pci 0000:00:1d.2: reg 20: [io  0xd800-0xd81f]
[    0.181328] pci 0000:00:1d.3: reg 20: [io  0xd880-0xd89f]
[    0.181369] pci 0000:00:1d.7: reg 10: [mem 0xfe977c00-0xfe977fff]
[    0.181414] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.181418] pci 0000:00:1d.7: PME# disabled
[    0.181523] pci 0000:00:1f.0: quirk: [io  0x0800-0x087f] claimed by ICH6 ACPI/GPIO/TCO
[    0.181527] pci 0000:00:1f.0: quirk: [io  0x0480-0x04bf] claimed by ICH6 GPIO
[    0.181530] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0294 (mask 0003)
[    0.181567] pci 0000:00:1f.1: reg 10: [io  0x0000-0x0007]
[    0.181573] pci 0000:00:1f.1: reg 14: [io  0x0000-0x0003]
[    0.181579] pci 0000:00:1f.1: reg 18: [io  0x08f0-0x08f7]
[    0.181584] pci 0000:00:1f.1: reg 1c: [io  0x08f8-0x08fb]
[    0.181590] pci 0000:00:1f.1: reg 20: [io  0xffa0-0xffaf]
[    0.181622] pci 0000:00:1f.2: reg 10: [io  0xd080-0xd087]
[    0.181627] pci 0000:00:1f.2: reg 14: [io  0xd000-0xd003]
[    0.181632] pci 0000:00:1f.2: reg 18: [io  0xcc00-0xcc07]
[    0.181638] pci 0000:00:1f.2: reg 1c: [io  0xc880-0xc883]
[    0.181642] pci 0000:00:1f.2: reg 20: [io  0xc800-0xc80f]
[    0.181663] pci 0000:00:1f.2: PME# supported from D3hot
[    0.181666] pci 0000:00:1f.2: PME# disabled
[    0.181707] pci 0000:00:1f.3: reg 20: [io  0x0400-0x041f]
[    0.181770] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.181774] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.181778] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.181783] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.181845] pci 0000:01:00.0: reg 10: [io  0xe800-0xe8ff]
[    0.181864] pci 0000:01:00.0: reg 18: [mem 0xfdfff000-0xfdffffff 64bit pref]
[    0.181877] pci 0000:01:00.0: reg 20: [mem 0xfdfe0000-0xfdfeffff 64bit pref]
[    0.181885] pci 0000:01:00.0: reg 30: [mem 0xfeaf0000-0xfeafffff pref]
[    0.181921] pci 0000:01:00.0: supports D1 D2
[    0.181923] pci 0000:01:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.181927] pci 0000:01:00.0: PME# disabled
[    0.188019] pci 0000:00:1c.1: PCI bridge to [bus 01-01]
[    0.188023] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.188026] pci 0000:00:1c.1:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.188032] pci 0000:00:1c.1:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.188090] pci 0000:00:1e.0: PCI bridge to [bus 03-03] (subtractive decode)
[    0.188094] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.188097] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.188102] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.188104] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.188106] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.188108] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.188110] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.188112] pci 0000:00:1e.0:   bridge window [mem 0xbf700000-0xffffffff] (subtractive decode)
[    0.188127] pci_bus 0000:00: on NUMA node 0
[    0.188133] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.188268] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.188357] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.188410] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P5._PRT]
[    0.196043] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.196135] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.196224] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.196314] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.196404] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.196494] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.196587] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[    0.196676] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.196716] HEST: Table is not found!
[    0.196787] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.196795] vgaarb: loaded
[    0.196930] SCSI subsystem initialized
[    0.197000] libata version 3.00 loaded.
[    0.197051] usbcore: registered new interface driver usbfs
[    0.197060] usbcore: registered new interface driver hub
[    0.197078] usbcore: registered new device driver usb
[    0.197173] ACPI: WMI: Mapper loaded
[    0.197174] PCI: Using ACPI for IRQ routing
[    0.197178] PCI: pci_cache_line_size set to 64 bytes
[    0.197236] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.197239] reserve RAM buffer: 00000000bf690000 - 00000000bfffffff 
[    0.197315] NetLabel: Initializing
[    0.197317] NetLabel:  domain hash size = 128
[    0.197318] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.197328] NetLabel:  unlabeled traffic allowed by default
[    0.197352] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.197356] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.197360] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.200018] Switching to clocksource tsc
[    0.208784] AppArmor: AppArmor Filesystem Enabled
[    0.208804] pnp: PnP ACPI init
[    0.208824] ACPI: bus type pnp registered
[    0.212681] pnp: PnP ACPI: found 19 devices
[    0.212683] ACPI: ACPI bus type pnp unregistered
[    0.212686] PnPBIOS: Disabled by ACPI PNP
[    0.212697] system 00:01: [mem 0xfed14000-0xfed19fff] has been reserved
[    0.212704] system 00:07: [io  0x0290-0x0297] has been reserved
[    0.212709] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.212711] system 00:08: [io  0x0800-0x087f] has been reserved
[    0.212713] system 00:08: [io  0x0480-0x04bf] has been reserved
[    0.212715] system 00:08: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.212717] system 00:08: [mem 0xfed20000-0xfed8ffff] has been reserved
[    0.212722] system 00:0b: [mem 0xffc00000-0xffefffff] has been reserved
[    0.212726] system 00:0c: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.212728] system 00:0c: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.212733] system 00:11: [mem 0xf0000000-0xf3ffffff] has been reserved
[    0.212737] system 00:12: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.212739] system 00:12: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.212741] system 00:12: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.212744] system 00:12: [mem 0x00100000-0xbf6fffff] could not be reserved
[    0.248423] pci 0000:00:1c.0: BAR 14: assigned [mem 0xbf700000-0xbf8fffff]
[    0.248427] pci 0000:00:1c.0: BAR 15: assigned [mem 0xbf900000-0xbfafffff 64bit pref]
[    0.248430] pci 0000:00:1c.0: BAR 13: assigned [io  0x1000-0x1fff]
[    0.248432] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    0.248435] pci 0000:00:1c.0:   bridge window [io  0x1000-0x1fff]
[    0.248439] pci 0000:00:1c.0:   bridge window [mem 0xbf700000-0xbf8fffff]
[    0.248442] pci 0000:00:1c.0:   bridge window [mem 0xbf900000-0xbfafffff 64bit pref]
[    0.248448] pci 0000:00:1c.1: PCI bridge to [bus 01-01]
[    0.248450] pci 0000:00:1c.1:   bridge window [io  0xe000-0xefff]
[    0.248454] pci 0000:00:1c.1:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.248458] pci 0000:00:1c.1:   bridge window [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.248463] pci 0000:00:1e.0: PCI bridge to [bus 03-03]
[    0.248464] pci 0000:00:1e.0:   bridge window [io  disabled]
[    0.248468] pci 0000:00:1e.0:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.248471] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.248485] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.248491]   alloc irq_desc for 16 on node -1
[    0.248494]   alloc kstat_irqs on node -1
[    0.248502] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.248506] pci 0000:00:1c.0: setting latency timer to 64
[    0.248516]   alloc irq_desc for 17 on node -1
[    0.248517]   alloc kstat_irqs on node -1
[    0.248521] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.248525] pci 0000:00:1c.1: setting latency timer to 64
[    0.248532] pci 0000:00:1e.0: setting latency timer to 64
[    0.248536] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.248537] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.248539] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.248541] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.248543] pci_bus 0000:00: resource 8 [mem 0xbf700000-0xffffffff]
[    0.248545] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.248546] pci_bus 0000:02: resource 1 [mem 0xbf700000-0xbf8fffff]
[    0.248548] pci_bus 0000:02: resource 2 [mem 0xbf900000-0xbfafffff 64bit pref]
[    0.248550] pci_bus 0000:01: resource 0 [io  0xe000-0xefff]
[    0.248552] pci_bus 0000:01: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.248554] pci_bus 0000:01: resource 2 [mem 0xfdf00000-0xfdffffff 64bit pref]
[    0.248556] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.248558] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.248559] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.248561] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.248563] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.248565] pci_bus 0000:03: resource 8 [mem 0xbf700000-0xffffffff]
[    0.248600] NET: Registered protocol family 2
[    0.248661] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.248871] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.249345] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.249598] TCP: Hash tables configured (established 131072 bind 65536)
[    0.249600] TCP reno registered
[    0.249603] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.249618] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.249713] NET: Registered protocol family 1
[    0.249730] pci 0000:00:02.0: Boot video device
[    0.249829] PCI: CLS 32 bytes, default 64
[    0.249993] cpufreq-nforce2: No nForce2 chipset.
[    0.250017] Scanning for low memory corruption every 60 seconds
[    0.250116] audit: initializing netlink socket (disabled)
[    0.250125] type=2000 audit(1301630454.244:1): initialized
[    0.258028] highmem bounce pool size: 64 pages
[    0.258033] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.259168] VFS: Disk quotas dquot_6.5.2
[    0.259217] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.259670] fuse init (API version 7.14)
[    0.259738] msgmni has been set to 1657
[    0.260989] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.260992] io scheduler noop registered
[    0.260993] io scheduler deadline registered
[    0.261006] io scheduler cfq registered (default)
[    0.261094] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.261127]   alloc irq_desc for 40 on node -1
[    0.261129]   alloc kstat_irqs on node -1
[    0.261138] pcieport 0000:00:1c.0: irq 40 for MSI/MSI-X
[    0.261208] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.261236]   alloc irq_desc for 41 on node -1
[    0.261237]   alloc kstat_irqs on node -1
[    0.261243] pcieport 0000:00:1c.1: irq 41 for MSI/MSI-X
[    0.261323] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.261382] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.261455] intel_idle: MWAIT substates: 0x22220
[    0.261457] intel_idle: does not run on family 6 model 23
[    0.261540] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.261545] ACPI: Power Button [PWRB]
[    0.261580] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.261582] ACPI: Power Button [PWRF]
[    0.261776] ACPI: acpi_idle registered with cpuidle
[    0.264432] ERST: Table is not found!
[    0.264638] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.264729] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.264818] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.265190] 00:0f: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.265309] 00:10: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.266226] brd: module loaded
[    0.266640] loop: module loaded
[    0.266780] ata_piix 0000:00:1f.1: version 2.13
[    0.266792]   alloc irq_desc for 18 on node -1
[    0.266794]   alloc kstat_irqs on node -1
[    0.266800] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.266833] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.266909] scsi0 : ata_piix
[    0.266972] scsi1 : ata_piix
[    0.268182] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.268185] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.268202]   alloc irq_desc for 19 on node -1
[    0.268203]   alloc kstat_irqs on node -1
[    0.268207] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.268211] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.268238] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.268283] scsi2 : ata_piix
[    0.268324] scsi3 : ata_piix
[    0.269680] ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
[    0.269682] ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
[    0.269933] Fixed MDIO Bus: probed
[    0.269961] PPP generic driver version 2.4.2
[    0.269997] tun: Universal TUN/TAP device driver, 1.6
[    0.269999] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.270066] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.270081]   alloc irq_desc for 23 on node -1
[    0.270083]   alloc kstat_irqs on node -1
[    0.270087] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.270102] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.270105] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.270131] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.270152] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    0.270161] ehci_hcd 0000:00:1d.7: debug port 1
[    0.274051] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.274069] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe977c00
[    0.276040] isapnp: Scanning for PnP cards...
[    0.287949] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.288067] hub 1-0:1.0: USB hub found
[    0.288072] hub 1-0:1.0: 8 ports detected
[    0.288140] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.288155] uhci_hcd: USB Universal Host Controller Interface driver
[    0.288191] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.288197] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.288200] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.288229] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.288254] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000d400
[    0.288343] hub 2-0:1.0: USB hub found
[    0.288346] hub 2-0:1.0: 2 ports detected
[    0.288388] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.288393] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.288395] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.288419] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.288439] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d480
[    0.288524] hub 3-0:1.0: USB hub found
[    0.288527] hub 3-0:1.0: 2 ports detected
[    0.288568] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.288573] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.288575] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.288602] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.288632] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000d800
[    0.288717] hub 4-0:1.0: USB hub found
[    0.288720] hub 4-0:1.0: 2 ports detected
[    0.288764] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.288769] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.288771] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.288795] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.288823] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000d880
[    0.288914] hub 5-0:1.0: USB hub found
[    0.288919] hub 5-0:1.0: 2 ports detected
[    0.289026] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.292014] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.292019] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.292101] mice: PS/2 mouse device common for all mice
[    0.292200] rtc_cmos 00:03: RTC can wake from S4
[    0.292232] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.292254] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.292346] device-mapper: uevent: version 1.0.3
[    0.315497] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.325286] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.340074] device-mapper: multipath: version 1.1.1 loaded
[    0.340078] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.348085] EISA: Probing bus 0 at eisa.0
[    0.348088] EISA: Cannot allocate resource for mainboard
[    0.348090] Cannot allocate resource for EISA slot 1
[    0.348092] Cannot allocate resource for EISA slot 2
[    0.348093] Cannot allocate resource for EISA slot 3
[    0.348095] Cannot allocate resource for EISA slot 4
[    0.348096] Cannot allocate resource for EISA slot 5
[    0.348098] Cannot allocate resource for EISA slot 6
[    0.348099] Cannot allocate resource for EISA slot 7
[    0.348100] Cannot allocate resource for EISA slot 8
[    0.348102] EISA: Detected 0 cards.
[    0.360438] Freeing initrd memory: 10508k freed
[    0.365171] cpuidle: using governor ladder
[    0.365173] cpuidle: using governor menu
[    0.365488] TCP cubic registered
[    0.365608] NET: Registered protocol family 10
[    0.365922] lo: Disabled Privacy Extensions
[    0.366110] NET: Registered protocol family 17
[    0.366581] Using IPI No-Shortcut mode
[    0.366678] PM: Resume from disk failed.
[    0.366690] registered taskstats version 1
[    0.366875]   Magic number: 7:443:8
[    0.366973] rtc_cmos 00:03: setting system clock to 2011-04-01 04:00:55 UTC (1301630455)
[    0.366975] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.366977] EDD information not available.
[    0.454012] ata3.01: NODEV after polling detection
[    0.460169] ata3.00: ATAPI: HL-DT-ST DVDRAM GH22NS50, TN02, max UDMA/100
[    0.460842] ata4.00: ATA-8: WDC WD3200AAJS-22L7A0, 01.03E01, max UDMA/133
[    0.460844] ata4.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.476177] ata3.00: configured for UDMA/100
[    0.476864] ata4.00: configured for UDMA/133
[    0.628879] isapnp: No Plug & Play device found
[    0.632326] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS50  TN02 PQ: 0 ANSI: 5
[    0.654032] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.654037] Uniform CD-ROM driver Revision: 3.20
[    0.654195] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    0.654242] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    0.654336] scsi 3:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-2 01.0 PQ: 0 ANSI: 5
[    0.654416] sd 3:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    0.654431] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    0.654456] sd 3:0:0:0: [sda] Write Protect is off
[    0.654458] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.654479] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.654591]  sda: sda1 sda2 < sda5 sda6 >
[    0.715807] sd 3:0:0:0: [sda] Attached SCSI disk
[    0.715818] Freeing unused kernel memory: 684k freed
[    0.716151] Write protecting the kernel text: 4932k
[    0.716182] Write protecting the kernel read-only data: 1976k
[    0.728301] udev[83]: starting version 163
[    0.786760] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.786781] r8169 0000:01:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.786814] r8169 0000:01:00.0: setting latency timer to 64
[    0.786854]   alloc irq_desc for 42 on node -1
[    0.786856]   alloc kstat_irqs on node -1
[    0.786868] r8169 0000:01:00.0: irq 42 for MSI/MSI-X
[    0.787298] r8169 0000:01:00.0: eth0: RTL8168c/8111c at 0xf806a000, 20:cf:30:c9:10:f3, XID 1c4000c0 IRQ 42
[    1.217289] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    7.142727] udev[375]: starting version 163
[    7.221783] intel_rng: FWH not detected
[    7.232171] Adding 5306364k swap on /dev/sda6.  Priority:-1 extents:1 across:5306364k 
[    7.232804] Linux agpgart interface v0.103
[    7.270599] leds_ss4200: no LED devices found
[    7.275260] agpgart-intel 0000:00:00.0: Intel G33 Chipset
[    7.275974] agpgart-intel 0000:00:00.0: detected 7164K stolen memory
[    7.305015] lp: driver loaded but no devices found
[    7.364380] parport_pc 00:06: reported by Plug and Play ACPI
[    7.364501] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[    7.385788] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    7.407722] ppdev: user-space parallel port driver
[    7.453420] type=1400 audit(1301630462.582:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=711 comm="apparmor_parser"
[    7.453936] type=1400 audit(1301630462.582:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=711 comm="apparmor_parser"
[    7.454219] type=1400 audit(1301630462.582:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=711 comm="apparmor_parser"
[    7.462460] [drm] Initialized drm 1.1.0 20060810
[    7.468918] lp0: using parport0 (interrupt-driven).
[    7.483234] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.483280]   alloc irq_desc for 43 on node -1
[    7.483282]   alloc kstat_irqs on node -1
[    7.483292] HDA Intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[    7.483318] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    7.522785] psmouse serio1: ID: 10 00 64
[    7.532399] hda_codec: ALC887: BIOS auto-probing.
[    7.543570] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.543575] i915 0000:00:02.0: setting latency timer to 64
[    7.555138]   alloc irq_desc for 44 on node -1
[    7.555141]   alloc kstat_irqs on node -1
[    7.555150] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[    7.555160] [drm] set up 7M of stolen space
[    7.555638] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    7.555976] [drm] initialized overlay support
[    7.844092] Console: switching to colour frame buffer device 160x64
[    7.847943] fb0: inteldrmfb frame buffer device
[    7.847945] drm: registered panic notifier
[    7.847948] Slow work thread pool: Starting up
[    7.847996] Slow work thread pool: Ready
[    7.848027] No ACPI video bus found
[    7.848069] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    8.171926] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input3
[    8.341592] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    8.679192] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    8.779804] r8169 0000:01:00.0: eth0: link up
[    8.779812] r8169 0000:01:00.0: eth0: link up
[    8.797170] type=1400 audit(1301630463.926:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1010 comm="apparmor_parser"
[    8.797216] type=1400 audit(1301630463.926:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1011 comm="apparmor_parser"
[    8.797735] type=1400 audit(1301630463.926:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1011 comm="apparmor_parser"
[    8.798019] type=1400 audit(1301630463.926:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1011 comm="apparmor_parser"
[    8.800289] type=1400 audit(1301630463.926:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1012 comm="apparmor_parser"
[    8.800783] type=1400 audit(1301630463.930:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1014 comm="apparmor_parser"
[    8.801416] type=1400 audit(1301630463.930:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1014 comm="apparmor_parser"
[    9.096026] device eth0 entered promiscuous mode
[   10.486021] vboxdrv: Found 2 processor cores.
[   10.486649] vboxdrv: fAsync=0 offMin=0x1a4 offMax=0x7c4
[   10.487293] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   10.487295] vboxdrv: Successfully loaded version 4.0.4 (interface 0x00160000).
[   11.788598] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   11.997849] EXT4-fs (sda5): re-mounted. Opts: commit=0
[   19.264504] eth0: no IPv6 routers present
[   83.401670] ISO 9660 Extensions: Microsoft Joliet Level 3
[   83.531173] ISO 9660 Extensions: RRIP_1991A

``` command :sudo lshw -C network ```
 
[sudo] password for mac: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 20:cf:30:c9:10:f3
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:e800(size=256) memory:fdfff000-fdffffff memory:fdfe0000-fdfeffff memory:feaf0000-feafffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

Please suggest me if the card is istalled correct or not

---

