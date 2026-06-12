---
title: "Updated to 9.10 now all tuners asleep ?"
date: 2010-03-02
forum: Mythbuntu
---

### Post by laffinet on 2010-03-02
Hi !

I'm planning to update my 9.04 system and therefore installed 9.10 on a separate partition. 
Most things are working, however somehow all my tuners are asleep all of a sudden.

I have 2xLeadtek DTV2000H rev. J which are running fine on 9.04, but when I boot into 9.10 they are reported as "asleep", hence I have no tuner cards available.

I tried deleting and re-adding them in mythbackend-setup bu that didn't help.
I booted into 9.04, they are working fine. Back to 9.10, reported as asleep. What is going on ?

dmesg:
```
[    7.323678] cx2388x alsa driver version 0.0.7 loaded
[    7.324118] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 18
[    7.324123]   alloc irq_desc for 18 on node -1
[    7.324125]   alloc kstat_irqs on node -1
[    7.324136] cx88_audio 0000:01:06.1: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
[    7.324530] cx88[0]: subsystem: 107d:6f2b, board: WinFast DTV2000 H rev. J [card=82,autodetected], frontend(s): 1
[    7.324533] cx88[0]: TV tuner type 63, Radio tuner type -1
[    7.326704] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.7 loaded
[    7.331918] cx88/0: cx2388x v4l2 driver version 0.0.7 loaded
[    7.698113] tuner 2-0043: chip found @ 0x86 (cx88[0])
[    7.764837] tda9887 2-0043: creating new instance
[    7.764841] tda9887 2-0043: tda988[5/6/7] found
[    7.767839] tuner 2-0061: chip found @ 0xc2 (cx88[0])
[    7.896706] tuner-simple 2-0061: creating new instance
[    7.896711] tuner-simple 2-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[    7.900734] input: cx88 IR (WinFast DTV2000 H rev. as /devices/pci0000:00/0000:00:08.0/0000:01:06.1/input/input5
[    7.900785] IRQ 18/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    7.900828] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
[    7.901070] cx88[0]/2: cx2388x 8802 Driver Manager
[    7.901084] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
[    7.901092] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 18, latency: 64, mmio: 0xd9000000
[    7.901098] IRQ 18/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    7.901115] cx8800 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 18 (level, low) -> IRQ 18
[    7.901120] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 18, latency: 64, mmio: 0xdb000000
[    7.901129] IRQ 18/cx88[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    7.901163] cx88[0]/0: registered device video0 [v4l2]
[    7.901186] cx88[0]/0: registered device vbi0
[    7.901205] cx88[0]/0: registered device radio0
[    7.903269] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 17
[    7.903276]   alloc irq_desc for 17 on node -1
[    7.903278]   alloc kstat_irqs on node -1
[    7.903289] cx88_audio 0000:01:07.1: PCI INT A -> Link[LNKB] -> GSI 17 (level, low) -> IRQ 17
[    7.903650] cx88[1]: subsystem: 107d:6f2b, board: WinFast DTV2000 H rev. J [card=82,autodetected], frontend(s): 1
[    7.903653] cx88[1]: TV tuner type 63, Radio tuner type -1
[    8.033050] tuner 3-0043: chip found @ 0x86 (cx88[1])
[    8.033119] tda9887 3-0043: creating new instance
[    8.033121] tda9887 3-0043: tda988[5/6/7] found
[    8.036049] tuner 3-0061: chip found @ 0xc2 (cx88[1])
[    8.077053] tuner-simple 3-0061: creating new instance
[    8.077057] tuner-simple 3-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[    8.081017] input: cx88 IR (WinFast DTV2000 H rev. as /devices/pci0000:00/0000:00:08.0/0000:01:07.1/input/input6
[    8.081069] IRQ 17/cx88[1]: IRQF_DISABLED is not guaranteed on shared IRQs
[    8.081109] cx88[1]/1: CX88x/1: ALSA support for cx2388x boards
[    8.083274] cx88[1]/2: cx2388x 8802 Driver Manager
[    8.083294] cx88-mpeg driver manager 0000:01:07.2: PCI INT A -> Link[LNKB] -> GSI 17 (level, low) -> IRQ 17
[    8.083302] cx88[1]/2: found at 0000:01:07.2, rev: 5, irq: 17, latency: 64, mmio: 0xd6000000
[    8.083310] IRQ 17/cx88[1]: IRQF_DISABLED is not guaranteed on shared IRQs
[    8.083356] cx8800 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 17 (level, low) -> IRQ 17
[    8.083365] cx88[1]/0: found at 0000:01:07.0, rev: 5, irq: 17, latency: 64, mmio: 0xd8000000
[    8.083378] IRQ 17/cx88[1]: IRQF_DISABLED is not guaranteed on shared IRQs
[    8.083422] cx88[1]/0: registered device video1 [v4l2]
[    8.083445] cx88[1]/0: registered device vbi1
[    8.083471] cx88[1]/0: registered device radio1
[    8.243400]   alloc irq_desc for 31 on node -1
[    8.243404]   alloc kstat_irqs on node -1
[    8.243414] forcedeth 0000:00:0a.0: irq 31 for MSI/MSI-X
[    8.355358] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[    8.355362] cx88/2: registering cx8802 driver, type: dvb access: shared
[    8.355365] cx88[0]/2: subsystem: 107d:6f2b, board: WinFast DTV2000 H rev. J [card=82]
[    8.355368] cx88[0]/2: cx2388x based DVB/ATSC card
[    8.355370] cx8802_alloc_frontends() allocating 1 frontend(s)
[    8.535421] tuner-simple 2-0061: attaching existing instance
[    8.535425] tuner-simple 2-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[    8.539709] DVB: registering new adapter (cx88[0])
[    8.539715] DVB: registering adapter 0 frontend 0 (Conexant CX22702 DVB-T)...
[    8.539990] cx88[1]/2: subsystem: 107d:6f2b, board: WinFast DTV2000 H rev. J [card=82]
[    8.539993] cx88[1]/2: cx2388x based DVB/ATSC card
[    8.539995] cx8802_alloc_frontends() allocating 1 frontend(s)
[    8.558780] tuner-simple 3-0061: attaching existing instance
[    8.558785] tuner-simple 3-0061: type set to 63 (Philips FMD1216ME MK3 Hybrid Tuner)
[    8.567103] DVB: registering new adapter (cx88[1])
[    8.567111] DVB: registering adapter 1 frontend 0 (Conexant CX22702 DVB-T)...
[   10.080221] type=1503 audit(1267585510.520:20): operation="open" pid=1403 parent=1402 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   11.758518] __ratelimit: 6 callbacks suppressed
[   11.758522] type=1503 audit(1267585512.197:23): operation="open" pid=1670 parent=1669 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   12.860992] type=1503 audit(1267585513.300:24): operation="open" pid=1689 parent=1688 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   12.907614] type=1503 audit(1267585513.344:25): operation="open" pid=1700 parent=1699 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[   13.732109] svc: failed to register lockdv1 RPC service (errno 97).
[   13.733094] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   13.733242] NFSD: starting 90-second grace period
[   16.528563] CPU0 attaching NULL sched-domain.
[   16.528570] CPU1 attaching NULL sched-domain.
[   16.544078] CPU0 attaching sched-domain:
[   16.544083]  domain 0: span 0-1 level MC
[   16.544086]   groups: 0 1
[   16.544089]   domain 1: span 0-1 level CPU
[   16.544091]    groups: 0-1 (__cpu_power = 2048)
[   16.544097] CPU1 attaching sched-domain:
[   16.544099]  domain 0: span 0-1 level MC
[   16.544101]   groups: 1 0
[   16.544103]   domain 1: span 0-1 level CPU
[   16.544105]    groups: 0-1 (__cpu_power = 2048)
[   18.936019] eth0: no IPv6 routers present
[   21.729753] CPU0 attaching NULL sched-domain.
[   21.729760] CPU1 attaching NULL sched-domain.
[   21.748410] CPU0 attaching sched-domain:
[   21.748415]  domain 0: span 0-1 level MC
[   21.748418]   groups: 0 1
[   21.748424] CPU1 attaching sched-domain:
[   21.748425]  domain 0: span 0-1 level MC
[   21.748427]   groups: 1 0

```

lspci
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:10.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:11.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:06.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:06.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:07.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
01:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

```

---

### Post by laffinet on 2010-03-03
Nevermind.

Checked mythbackend setup, input connections. Changed video to blank, all good now.

Except that myth now reports four tuners that are unavailable (don't know where they are from and how to get rid of them) and four that are ok.

---

