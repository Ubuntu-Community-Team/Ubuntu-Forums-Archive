---
title: "HP dv7-6135dx wireless not working"
date: 2011-12-31
forum: Networking &amp; Wireless
---

### Post by Sxynerd on 2011-12-31
I'm having a wireless issue again i can't figure it out.  I am using Ubuntu 10.10 because I thought it would be a little better supported but I guess since the laptop is so new (comparatively) there isn't anything on it.  sometimes you can't win for loosing, lol.  Thank you, Please help.

The Laptop is a HP DV7-6135dx

Here are the standard readouts.


**lspci -nnk**
00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0104] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:01.0 PCI bridge [0604]: Intel Corporation Sandy Bridge PCI Express Root Port [8086:0101] (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0116] (rev 09)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 3 [8086:1c14] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 4 [8086:1c16] (rev b5)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c49] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 05)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Device [1002:6760]
	Subsystem: Hewlett-Packard Company Device [103c:1659]
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: r8169
	Kernel modules: r8169
0d:00.0 Network controller [0280]: Intel Corporation Device [8086:0886] (rev 67)
	Subsystem: Intel Corporation Device [8086:1315]
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5209] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
19:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 04)
	Subsystem: Hewlett-Packard Company Device [103c:1659]
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd

---

### Post by Sxynerd on 2011-12-31
**lsmod**
Module                  Size  Used by
nls_iso8859_1           4657  0 
nls_cp437               6375  0 
vfat                   10954  0 
fat                    56244  1 vfat
usb_storage            50788  0 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_idt      64763  1 
snd_hda_intel          26147  2 
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62411  0 
joydev                 11395  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
hp_wmi                  6467  0 
snd                    64277  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                62080  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
serio_raw               4910  0 
hp_accel               14304  0 
lis3lv02d              10384  1 hp_accel
input_polldev           4527  1 lis3lv02d
led_class               3393  1 hp_accel
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
hid                    84710  1 usbhid
i915                  335073  3 
drm_kms_helper         32836  1 i915
drm                   206198  3 i915,drm_kms_helper
ahci                   22370  2 
libahci                26148  1 ahci
r8169                  42286  0 
mii                     5261  1 r8169
xhci_hcd               62016  0 
i2c_algo_bit            6208  1 i915
intel_agp              32334  2 i915
video                  22176  1 i915
output                  2527  1 video
ramzswap               11551  0 
lzo_compress            2349  1 ramzswap

**uname -a**
Linux wolvee-HP-Pavilion-dv7-Notebook-PC 2.6.35-31-generic #63-Ubuntu SMP Mon Nov 28 19:29:10 UTC 2011 x86_64 GNU/Linux

**rfkill list**
0: hp-wwan: Wireless WAN
	Soft blocked: no
	Hard blocked: no

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.


**ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:ab:71:2e  
          inet addr:192.168.1.19  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e27:d7ff:feab:712e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:434046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:258276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:641126833 (641.1 MB)  TX bytes:18871440 (18.8 MB)
          Interrupt:45 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)


**cat /etc/network/interfaces**
auto lo
iface lo inet loopback

---

### Post by Sxynerd on 2012-01-01
Anyone?

---

### Post by dodo3773 on 2012-01-02
Based on that output I am pretty sure that the wireless driver is in your kernel. Have you tried:
```

sudo modprobe iwlagn

```

and then run iwconfig again? It should have gotten picked up. I did not think that external firmware was needed any more for that module.

---

### Post by Sxynerd on 2012-01-02
Thanks for the reply.  I have a major failure last night so I'll be reinstalling today. (My fault with the ATI drivers)  I'll let you know what the result are when I get it all set back up.

How are you able to tell what wireless card I have?  I can't see anything in that stuff I put int he posts.  There are almost no threads on this PC and it's confusing.  Most all of my PC's i've been able to search for problems easily and with almost robot like motions, copy what others had to do to fix the issues.  But not with this one.

---

### Post by dodo3773 on 2012-01-02
> **Sxynerd said:**
> Thanks for the reply.  I have a major failure last night so I'll be reinstalling today. (My fault with the ATI drivers)  I'll let you know what the result are when I get it all set back up.

How are you able to tell what wireless card I have?  I can't see anything in that stuff I put int he posts.  There are almost no threads on this PC and it's confusing.  Most all of my PC's i've been able to search for problems easily and with almost robot like motions, copy what others had to do to fix the issues.  But not with this one.

It is the network section of the lspci output. Try this:
```

lspci | grep -i NET

```

and you will see your card is an Intel wireless card. That is why I suggested you load the iwlagn module (because that is the intel wireless kernel module).

---

### Post by Sxynerd on 2012-01-02
No Luck.  Here is the output.

wolvee@ubuntu:~$ lspci | grep -i NET
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
0d:00.0 Network controller: Intel Corporation Device 0886 (rev 67)

wolvee@ubuntu:~$ sudo modprobe iwlagn
[sudo] password for wolvee: 

wolvee@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wolvee@ubuntu:~$

---

### Post by dodo3773 on 2012-01-02
If your system is up-to-date then maybe try updating your kernel to a newer version and see if that helps. Do you see any errors in dmesg? Also, check your bios options.

---

### Post by Sxynerd on 2012-01-02
this is what I get from that.  

[    0.897309] system 00:05: [io  0x0500-0x057f] has been reserved
[    0.897311] system 00:05: [io  0x164e-0x164f] has been reserved
[    0.897315] system 00:07: [io  0x0454-0x0457] has been reserved
[    0.897321] system 00:0a: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.897323] system 00:0a: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.897325] system 00:0a: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.897327] system 00:0a: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.897329] system 00:0a: [mem 0xe0000000-0xefffffff] has been reserved
[    0.897334] system 00:0a: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.897336] system 00:0a: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.897338] system 00:0a: [mem 0xff000000-0xffffffff] could not be reserved
[    0.897340] system 00:0a: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.897342] system 00:0a: [mem 0x9fa00000-0x9fa00fff] has been reserved
[    0.897346] system 00:0c: [mem 0x20000000-0x201fffff] could not be reserved
[    0.897348] system 00:0c: [mem 0x40000000-0x401fffff] could not be reserved
[    0.902813] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.902818] pci 0000:13:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.902859] pci 0000:01:00.0: BAR 6: assigned [mem 0xc6520000-0xc653ffff pref]
[    0.902861] pci 0000:00:01.0: PCI bridge to [bus 01-06]
[    0.902864] pci 0000:00:01.0:   bridge window [io  0x5000-0x5fff]
[    0.902866] pci 0000:00:01.0:   bridge window [mem 0xc6500000-0xc74fffff]
[    0.902869] pci 0000:00:01.0:   bridge window [mem 0xa0000000-0xafffffff 64bit pref]
[    0.902873] pci 0000:00:1c.0: PCI bridge to [bus 07-0c]
[    0.902876] pci 0000:00:1c.0:   bridge window [io  0x4000-0x4fff]
[    0.902881] pci 0000:00:1c.0:   bridge window [mem 0xc5500000-0xc64fffff]
[    0.902886] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc13fffff 64bit pref]
[    0.902892] pci 0000:00:1c.1: PCI bridge to [bus 0d-12]
[    0.902895] pci 0000:00:1c.1:   bridge window [io  0x3000-0x3fff]
[    0.902900] pci 0000:00:1c.1:   bridge window [mem 0xc4500000-0xc54fffff]
[    0.902905] pci 0000:00:1c.1:   bridge window [mem 0xc1400000-0xc23fffff 64bit pref]
[    0.902912] pci 0000:13:00.0: BAR 6: assigned [mem 0xc2400000-0xc240ffff pref]
[    0.902914] pci 0000:00:1c.2: PCI bridge to [bus 13-18]
[    0.902917] pci 0000:00:1c.2:   bridge window [io  0x2000-0x2fff]
[    0.902922] pci 0000:00:1c.2:   bridge window [mem 0xc3500000-0xc44fffff]
[    0.902927] pci 0000:00:1c.2:   bridge window [mem 0xc2400000-0xc33fffff 64bit pref]
[    0.902933] pci 0000:00:1c.3: PCI bridge to [bus 19-19]
[    0.902934] pci 0000:00:1c.3:   bridge window [io  disabled]
[    0.902940] pci 0000:00:1c.3:   bridge window [mem 0xc3400000-0xc34fffff]
[    0.902944] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    0.902956]   alloc irq_desc for 16 on node -1
[    0.902958]   alloc kstat_irqs on node -1
[    0.902963] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.902966] pci 0000:00:01.0: setting latency timer to 64
[    0.902974]   alloc irq_desc for 17 on node -1
[    0.902976]   alloc kstat_irqs on node -1
[    0.902978] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.902983] pci 0000:00:1c.0: setting latency timer to 64
[    0.902992] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.902997] pci 0000:00:1c.1: setting latency timer to 64
[    0.903005]   alloc irq_desc for 18 on node -1
[    0.903006]   alloc kstat_irqs on node -1
[    0.903009] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.903013] pci 0000:00:1c.2: setting latency timer to 64
[    0.903023]   alloc irq_desc for 19 on node -1
[    0.903024]   alloc kstat_irqs on node -1
[    0.903028] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.903033] pci 0000:00:1c.3: setting latency timer to 64
[    0.903037] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.903039] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.903040] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.903042] pci_bus 0000:00: resource 7 [mem 0x9fa00000-0xfeafffff]
[    0.903044] pci_bus 0000:01: resource 0 [io  0x5000-0x5fff]
[    0.903045] pci_bus 0000:01: resource 1 [mem 0xc6500000-0xc74fffff]
[    0.903047] pci_bus 0000:01: resource 2 [mem 0xa0000000-0xafffffff 64bit pref]
[    0.903049] pci_bus 0000:07: resource 0 [io  0x4000-0x4fff]
[    0.903050] pci_bus 0000:07: resource 1 [mem 0xc5500000-0xc64fffff]
[    0.903052] pci_bus 0000:07: resource 2 [mem 0xc0400000-0xc13fffff 64bit pref]
[    0.903054] pci_bus 0000:0d: resource 0 [io  0x3000-0x3fff]
[    0.903056] pci_bus 0000:0d: resource 1 [mem 0xc4500000-0xc54fffff]
[    0.903057] pci_bus 0000:0d: resource 2 [mem 0xc1400000-0xc23fffff 64bit pref]
[    0.903059] pci_bus 0000:13: resource 0 [io  0x2000-0x2fff]
[    0.903061] pci_bus 0000:13: resource 1 [mem 0xc3500000-0xc44fffff]
[    0.903062] pci_bus 0000:13: resource 2 [mem 0xc2400000-0xc33fffff 64bit pref]
[    0.903064] pci_bus 0000:19: resource 1 [mem 0xc3400000-0xc34fffff]
[    0.903086] NET: Registered protocol family 2
[    0.903310] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.904308] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.905620] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.905754] TCP: Hash tables configured (established 524288 bind 65536)
[    0.905756] TCP reno registered
[    0.905771] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.905806] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.905897] NET: Registered protocol family 1
[    0.905911] pci 0000:00:02.0: Boot video device
[    0.939604] pci 0000:19:00.0: xHCI HW did not halt within 2000 usec status = 0x0
[    0.939614] PCI: CLS 64 bytes, default 64
[    0.939616] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.939618] Placing 64MB software IO TLB between ffff880002166000 - ffff880006166000
[    0.939619] software IO TLB at phys 0x2166000 - 0x6166000
[    0.939647] Simple Boot Flag at 0x44 set to 0x1
[    0.939856] Scanning for low memory corruption every 60 seconds
[    0.939960] audit: initializing netlink socket (disabled)
[    0.939968] type=2000 audit(1325534540.790:1): initialized
[    0.951340] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.952432] VFS: Disk quotas dquot_6.5.2
[    0.952477] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.952914] fuse init (API version 7.14)
[    0.952977] msgmni has been set to 15872
[    1.000344] Freeing initrd memory: 10784k freed
[    1.003236] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.003239] io scheduler noop registered
[    1.003241] io scheduler deadline registered
[    1.003270] io scheduler cfq registered (default)
[    1.003347] pcieport 0000:00:01.0: setting latency timer to 64
[    1.003365]   alloc irq_desc for 40 on node -1
[    1.003366]   alloc kstat_irqs on node -1
[    1.003374] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    1.003422] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.003455]   alloc irq_desc for 41 on node -1
[    1.003457]   alloc kstat_irqs on node -1
[    1.003464] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    1.003531] pcieport 0000:00:1c.1: setting latency timer to 64
[    1.003565]   alloc irq_desc for 42 on node -1
[    1.003566]   alloc kstat_irqs on node -1
[    1.003573] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    1.003639] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.003672]   alloc irq_desc for 43 on node -1
[    1.003673]   alloc kstat_irqs on node -1
[    1.003680] pcieport 0000:00:1c.2: irq 43 for MSI/MSI-X
[    1.003749] pcieport 0000:00:1c.3: setting latency timer to 64
[    1.003783]   alloc irq_desc for 44 on node -1
[    1.003784]   alloc kstat_irqs on node -1
[    1.003791] pcieport 0000:00:1c.3: irq 44 for MSI/MSI-X
[    1.003857] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.003978] \_SB_.PCI0:_OSC invalid UUID
[    1.003980] _OSC request data:1 0 1f 
[    1.004081] \_SB_.PCI0:_OSC invalid UUID
[    1.004082] _OSC request data:1 0 1f 
[    1.004178] \_SB_.PCI0:_OSC invalid UUID
[    1.004180] _OSC request data:1 0 1f 
[    1.004286] \_SB_.PCI0:_OSC invalid UUID
[    1.004287] _OSC request data:1 0 1f 
[    1.004382] \_SB_.PCI0:_OSC invalid UUID
[    1.004383] _OSC request data:1 0 1f 
[    1.004477] \_SB_.PCI0:_OSC invalid UUID
[    1.004478] _OSC request data:1 0 1f 
[    1.004496] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.004554] intel_idle: MWAIT substates: 0x21120
[    1.004555] intel_idle: v0.4 model 0x2A
[    1.004556] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.005474] ACPI: AC Adapter [AC] (on-line)
[    1.005519] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01/PNP0C0D:00/input/input0
[    1.006376] ACPI: Lid Switch [LID]
[    1.006417] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.006421] ACPI: Power Button [PWRB]
[    1.006449] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.006451] ACPI: Power Button [PWRF]
[    1.006868] ACPI: acpi_idle yielding to intel_idle
[    1.023359] thermal LNXTHERM:01: registered as thermal_zone0
[    1.023365] ACPI: Thermal Zone [THRM] (69 C)
[    1.023421] ERST: Table is not found!
[    1.027629] Linux agpgart interface v0.103
[    1.027648] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.028759] brd: module loaded
[    1.029116] loop: module loaded
[    1.029420] Fixed MDIO Bus: probed
[    1.029441] PPP generic driver version 2.4.2
[    1.029462] tun: Universal TUN/TAP device driver, 1.6
[    1.029463] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.029511] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.029528] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.029545] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.029548] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.029571] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.029600] ehci_hcd 0000:00:1a.0: debug port 2
[    1.033476] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.033491] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xc750a000
[    1.047567] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.047671] hub 1-0:1.0: USB hub found
[    1.047675] hub 1-0:1.0: 2 ports detected
[    1.047724]   alloc irq_desc for 20 on node -1
[    1.047726]   alloc kstat_irqs on node -1
[    1.047731] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.047742] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.047745] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.047769] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.047793] ehci_hcd 0000:00:1d.0: debug port 2
[    1.051687] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.051699] ehci_hcd 0000:00:1d.0: irq 20, io mem 0xc7509000
[    1.057631] ACPI: Battery Slot [BAT0] (battery present)
[    1.067522] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.067684] hub 2-0:1.0: USB hub found
[    1.067690] hub 2-0:1.0: 2 ports detected
[    1.067732] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.067741] uhci_hcd: USB Universal Host Controller Interface driver
[    1.067823] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.080916] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.080921] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.080979] mice: PS/2 mouse device common for all mice
[    1.081071] rtc_cmos 00:06: RTC can wake from S4
[    1.081104] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    1.081132] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.081205] device-mapper: uevent: version 1.0.3
[    1.081261] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    1.081331] device-mapper: multipath: version 1.1.1 loaded
[    1.081333] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.081585] cpuidle: using governor ladder
[    1.081735] cpuidle: using governor menu
[    1.081926] TCP cubic registered
[    1.082017] NET: Registered protocol family 10
[    1.082360] lo: Disabled Privacy Extensions
[    1.082560] NET: Registered protocol family 17
[    1.084001] PM: Resume from disk failed.
[    1.084010] registered taskstats version 1
[    1.084224] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.084369]   Magic number: 12:201:42
[    1.084374] bdi 7:7: hash matches
[    1.084444] rtc_cmos 00:06: setting system clock to 2012-01-02 20:02:21 UTC (1325534541)
[    1.084447] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.084449] EDD information not available.
[    1.084536] Freeing unused kernel memory: 912k freed
[    1.084637] Write protecting the kernel read-only data: 10240k
[    1.084800] Freeing unused kernel memory: 400k freed
[    1.084984] Freeing unused kernel memory: 1640k freed
[    1.096964] udev[98]: starting version 163
[    1.114839] xhci_hcd 0000:19:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.114874] xhci_hcd 0000:19:00.0: setting latency timer to 64
[    1.114881] xhci_hcd 0000:19:00.0: xHCI Host Controller
[    1.114931] xhci_hcd 0000:19:00.0: new USB bus registered, assigned bus number 3
[    1.115144] xhci_hcd 0000:19:00.0: irq 19, io mem 0xc3400000
[    1.125049] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.125073] r8169 0000:07:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.125130] r8169 0000:07:00.0: setting latency timer to 64
[    1.125137] r8169 0000:07:00.0: (unregistered net_device): unknown MAC, using family default
[    1.125189]   alloc irq_desc for 45 on node -1
[    1.125191]   alloc kstat_irqs on node -1
[    1.125209] r8169 0000:07:00.0: irq 45 for MSI/MSI-X
[    1.126020] r8169 0000:07:00.0: eth0: RTL8168b/8111b at 0xffffc900117ea000, 2c:27:d7:ab:71:2e, XID 0c200000 IRQ 45
[    1.127215] usb usb3: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
[    1.127305] xHCI xhci_add_endpoint called for root hub
[    1.127308] xHCI xhci_check_bandwidth called for root hub
[    1.127339] hub 3-0:1.0: USB hub found
[    1.127344] hub 3-0:1.0: 4 ports detected
[    1.134341] ahci 0000:00:1f.2: version 3.0
[    1.134360] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.134408]   alloc irq_desc for 46 on node -1
[    1.134411]   alloc kstat_irqs on node -1
[    1.134423] ahci 0000:00:1f.2: irq 46 for MSI/MSI-X
[    1.147937] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x21 impl SATA mode
[    1.147942] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.147949] ahci 0000:00:1f.2: setting latency timer to 64
[    1.179352] scsi0 : ahci
[    1.179499] scsi1 : ahci
[    1.179641] scsi2 : ahci
[    1.179710] scsi3 : ahci
[    1.179825] scsi4 : ahci
[    1.179953] scsi5 : ahci
[    1.180073] ata1: SATA max UDMA/133 abar m2048@0xc7508000 port 0xc7508100 irq 46
[    1.180075] ata2: DUMMY
[    1.180075] ata3: DUMMY
[    1.180076] ata4: DUMMY
[    1.180077] ata5: DUMMY
[    1.180079] ata6: SATA max UDMA/133 abar m2048@0xc7508000 port 0xc7508380 irq 46
[    1.367880] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.518582] hub 1-1:1.0: USB hub found
[    1.518662] hub 1-1:1.0: 6 ports detected
[    1.529664] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.534901] ata6.00: ATAPI: hp      DVD A  DS8A5LH, 1H68, max UDMA/100
[    1.536434] ata6.00: configured for UDMA/100
[    1.538382] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.539137] ata1.00: ATA-8: TOSHIBA MK7559GSXP, GN001C, max UDMA/100
[    1.539146] ata1.00: 1465149168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.540094] ata1.00: configured for UDMA/100
[    1.557951] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK7559GS GN00 PQ: 0 ANSI: 5
[    1.558101] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.558136] sd 0:0:0:0: [sda] 1465149168 512-byte logical blocks: (750 GB/698 GiB)
[    1.558138] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.558192] sd 0:0:0:0: [sda] Write Protect is off
[    1.558195] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.558211] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.558330]  sda:
[    1.563123] scsi 5:0:0:0: CD-ROM            hp       DVD A  DS8A5LH   1H68 PQ: 0 ANSI: 5
[    1.574857] sr0: scsi3-mmc drive: 24x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.574867] Uniform CD-ROM driver Revision: 3.20
[    1.575033] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    1.575114] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    1.618683]  sda1 sda2 sda3 sda4
[    1.618962] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.637737] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.788299] hub 2-1:1.0: USB hub found
[    1.788404] hub 2-1:1.0: 6 ports detected
[    1.907647] usb 3-4: new full speed USB device using xhci_hcd and address 0
[    1.935218] xhci_hcd 0000:19:00.0: WARN: Stalled endpoint
[    1.937218] xhci_hcd 0000:19:00.0: WARN: Stalled endpoint
[    1.939217] xhci_hcd 0000:19:00.0: WARN: Stalled endpoint
[    1.948216] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    1.952220] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    1.955226] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    1.970295] usbcore: registered new interface driver hiddev
[    1.975407] input: Microsoft Microsoft® 2.4GHz Transceiver v4.0 as /devices/pci0000:00/0000:00:1c.3/0000:19:00.0/usb3/3-4/3-4:1.0/input/input4
[    1.975481] generic-usb 0003:045E:0745.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft® 2.4GHz Transceiver v4.0] on usb-0000:19:00.0-4/input0
[    1.988478] input: Microsoft Microsoft® 2.4GHz Transceiver v4.0 as /devices/pci0000:00/0000:00:1c.3/0000:19:00.0/usb3/3-4/3-4:1.1/input/input5
[    1.988563] generic-usb 0003:045E:0745.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft® 2.4GHz Transceiver v4.0] on usb-0000:19:00.0-4/input1
[    2.000256] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.003225] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.006212] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.009288] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.013250] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.016197] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.019265] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.022221] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.025198] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.028251] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.031254] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.034217] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.037212] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.037748] usb 1-1.1: new full speed USB device using ehci_hcd and address 3
[    2.040212] xhci_hcd 0000:19:00.0: WARN: short transfer on control ep
[    2.041429] input: Microsoft Microsoft® 2.4GHz Transceiver v4.0 as /devices/pci0000:00/0000:00:1c.3/0000:19:00.0/usb3/3-4/3-4:1.2/input/input6
[    2.041541] generic-usb 0003:045E:0745.0003: input,hiddev96,hidraw2: USB HID v1.11 Device [Microsoft Microsoft® 2.4GHz Transceiver v4.0] on usb-0000:19:00.0-4/input2
[    2.041560] usbcore: registered new interface driver usbhid
[    2.041562] usbhid: USB HID core driver
[    2.228341] usb 1-1.2: new high speed USB device using ehci_hcd and address 4
[    2.453900] EXT4-fs (loop0): INFO: recovery required on readonly filesystem
[    2.453903] EXT4-fs (loop0): write access will be enabled during recovery
[    2.517437] usb 2-1.5: new high speed USB device using ehci_hcd and address 3
[    2.957855] EXT4-fs (loop0): orphan cleanup on readonly fs
[    2.957862] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 654136
[    2.957909] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 1439033
[    2.957936] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 1439087
[    2.957946] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 1439081
[    2.957955] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 1439083
[    2.957965] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 1439097
[    2.957974] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 1438997
[    2.957984] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 1439129
[    2.957995] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 1439021
[    2.958021] EXT4-fs (loop0): ext4_orphan_cleanup: deleting unreferenced inode 1439135
[    2.958029] EXT4-fs (loop0): 10 orphan inodes deleted
[    2.958031] EXT4-fs (loop0): recovery complete
[    2.958670] EXT4-fs (loop0): mounted filesystem with ordered data mode. Opts: (null)
[    5.405195] udev[413]: starting version 163
[    6.944835] input: HP WMI hotkeys as /devices/virtual/input/input7
[    7.085381] lp: driver loaded but no devices found
[    7.173192] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    7.174432] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    7.202443] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xb0000000
[    7.287910] lis3lv02d: hardware type DV7 found.
[    7.415265] Linux video capture interface: v2.00
[    7.568481] uvcvideo: Found UVC 1.00 device HP TrueVision HD (5986:02ac)
[    7.576015] input: HP TrueVision HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input8
[    7.576074] usbcore: registered new interface driver uvcvideo
[    7.576076] USB Video Class driver (v0.1.0)
[    7.610192] lis3lv02d: unknown sensor type 0x33
[    7.610224] lis3lv02d: probe of HPQ0004:00 failed with error -22
[    7.610240] lis3lv02d driver loaded.
[    7.662218] [drm] Initialized drm 1.1.0 20060810
[    7.799751] type=1400 audit(1325552548.207:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=603 comm="apparmor_parser"
[    7.799762] type=1400 audit(1325552548.207:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=573 comm="apparmor_parser"
[    7.800219] type=1400 audit(1325552548.207:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=603 comm="apparmor_parser"
[    7.800259] type=1400 audit(1325552548.207:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=573 comm="apparmor_parser"
[    7.800467] type=1400 audit(1325552548.207:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=603 comm="apparmor_parser"
[    7.800511] type=1400 audit(1325552548.207:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=573 comm="apparmor_parser"
[    8.018951] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.018955] i915 0000:00:02.0: setting latency timer to 64
[    8.029798] Synaptics Touchpad, model: 1, fw: 7.5, id: 0x1e0b1, caps: 0xd00073/0x240000/0xa0400
[    8.060090] mtrr: no more MTRRs available
[    8.060093] [drm] MTRR allocation failed.  Graphics performance may suffer.
[    8.060165]   alloc irq_desc for 47 on node -1
[    8.060167]   alloc kstat_irqs on node -1
[    8.060175] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[    8.060182] [drm] set up 31M of stolen space
[    8.072759] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[    8.177403] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    8.177407] vgaarb: transferring owner from PCI:0000:00:02.0 to PCI:0000:01:00.0
[    8.459488] Skipping EDID probe due to cached edid
[    8.854653] Console: switching to colour frame buffer device 200x56
[    8.857290] fb0: inteldrmfb frame buffer device
[    8.857292] drm: registered panic notifier
[    8.857295] Slow work thread pool: Starting up
[    8.857364] Slow work thread pool: Ready
[    8.857868] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    8.979086] acpi device:2e: registered as cooling_device4
[    8.979875] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2c/LNXVIDEO:00/input/input10
[    8.979922] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[    9.103562] acpi device:3b: registered as cooling_device5
[    9.104270] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input11
[    9.104340] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    9.104380] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.104447]   alloc irq_desc for 22 on node -1
[    9.104450]   alloc kstat_irqs on node -1
[    9.104456] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.104512]   alloc irq_desc for 48 on node -1
[    9.104513]   alloc kstat_irqs on node -1
[    9.104522] HDA Intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[    9.104544] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.182930] Skipping EDID probe due to cached edid
[    9.816133] input: HDA Intel PCH Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    9.816191] input: HDA Intel PCH HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   11.041407] Adding 261116k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:1 across:261116k 
[   11.078799] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro
[   11.588280] type=1400 audit(1325552551.997:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=994 comm="apparmor_parser"
[   11.588749] type=1400 audit(1325552551.997:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=994 comm="apparmor_parser"
[   11.588999] type=1400 audit(1325552551.997:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=994 comm="apparmor_parser"
[   11.660387] type=1400 audit(1325552552.067:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=998 comm="apparmor_parser"
[   11.898951] ppdev: user-space parallel port driver
[   13.094636] r8169 0000:07:00.0: eth0: link up
[   13.094644] r8169 0000:07:00.0: eth0: link up
[   14.135176] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   14.216629] Skipping EDID probe due to cached edid
[   14.243915] Skipping EDID probe due to cached edid
[   17.522619] Skipping EDID probe due to cached edid
[   17.550854] Skipping EDID probe due to cached edid
[   17.578805] Skipping EDID probe due to cached edid
[   17.606615] Skipping EDID probe due to cached edid
[   19.232959] EXT4-fs (loop0): re-mounted. Opts: errors=remount-ro,commit=0
[   23.227415] eth0: no IPv6 routers present
[   25.464987] Skipping EDID probe due to cached edid
[   25.493878] Skipping EDID probe due to cached edid
[   25.521850] Skipping EDID probe due to cached edid
[   25.575329] Skipping EDID probe due to cached edid
[   31.307133] Skipping EDID probe due to cached edid
[   41.055884] r8169 0000:07:00.0: eth0: link down
[   64.339753] cfg80211: Calling CRDA to update world regulatory domain
[   64.377934] cfg80211: World regulatory domain updated:
[   64.377937]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   64.377941]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   64.377943]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   64.377946]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   64.377949]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   64.377951]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   64.461415] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   64.461418] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   78.338963] r8169 0000:07:00.0: eth0: link up
wolvee@ubuntu:~$

---

### Post by dodo3773 on 2012-01-02
Please use code tags. It makes it easier to read. Anyway it looks like iwlagn is loading. Is your system up to date? Maybe try updating your kernel to see if that helps. Other than that I am not sure.

---

### Post by Sxynerd on 2012-01-02
When you say update my Kernel do you mean, upgrade to 11.10 or something else?  <--noob

---

### Post by dodo3773 on 2012-01-02
> **Sxynerd said:**
> When you say update my Kernel do you mean, upgrade to 11.10 or something else?

No. I mean just the kernel itself. There must be a third party ppa or something for newer kernel versions. Try Ubuntu tweak or a Ubuntu Kernal ppa for a newer version. I found this:

[https://launchpad.net/~kernel-ppa/+archive/ppa](https://launchpad.net/~kernel-ppa/+archive/ppa)

I am not sure if it applies to your system or not though. The reason I recommended that is because the drivers and modules are already in the kernel. So, maybe a newer kernel would work better.

---

### Post by Sxynerd on 2012-01-03
I didn't have the heart to try something like that for the first time ever tonight.  I installed 11.10 and it worked out of the box with out any real issue.

Although The Wifi connection indicator is flashing between white and red and I don't know why.  the connection seems fine and I'm not loosing connection but it's flashing like it's going on and off.

Edit:  pulled out a line of my confusion.

---

### Post by Sxynerd on 2012-01-03
Should I start another thread?


After I close the laptop and it suspends the wireless can't connect but it will reconnect if I do a restart.

---

### Post by bkratz on 2012-01-03
> **Sxynerd said:**
> I didn't have the heart to try something like that for the first time ever tonight.  I installed 11.10 and it worked out of the box with out any real issue.

Although The Wifi connection indicator is flashing between white and red and I don't know why.  the connection seems fine and I'm not loosing connection but it's flashing like it's going on and off.


Does this apply to me as well?
[http://ubuntuforums.org/showpost.php?p=11054465&postcount=7](http://ubuntuforums.org/showpost.php?p=11054465&postcount=7)


Are you having problems with your ethernet connection too?  The r8169 driver has nothing to do with the wireless--just the wired.

---

### Post by Sxynerd on 2012-01-03
Yeah I noticed that after my reading comprehension kicked in after a nap, lol.  The wired connection is fine. It is just when I çlose the laptop lid the wireless keeps trying to connect but fails.  If I restart it goes back to normal and the connection is good.  Except of course that the light has turrets.

I don't know where to start.  My googlefu is usaly prettygood but I can't find a single solution.

---

