---
title: "cx88 pci_abort errors after upgrade to 11.10"
date: 2011-10-15
forum: Multimedia Software
---

### Post by thejpster on 2011-10-15
I have been running MythTV since 2003 so I'm fairly used to it by now. My current system has an:

```

vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
stepping	: 2
cpu MHz		: 1000.000
cache size	: 512 KB

```

on an Asus M2N-VM DVI motherboard with 4GB DDR2, a single 500GB sata disk and a VDPAU compatible Geforce graphics card I use in place of the onboard graphics.

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
01:06.4 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [IR Port] (rev 05)
01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
01:07.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```

The system has two PCI capture cards - a Hauppage Nova HD-S2 and a K-World DVB-T card. Both worked perfectly under 11.04 - I could record on both cards simultaneously, multiple programs from each (on the same multiplex) in fact, even in HD, while watching something else in HD.

This morning, I updated my motherboard's BIOS from 0201 (or possibly 0203) to the latest stable version, 0905, and upgraded from Ubuntu 11.04 to 11.10 and MythTV is now broken. Whoops!

I believe both my DVB cards are managed by the cx88-dvb module:

```

Oct 15 15:34:13 fluffy kernel: [    6.223513] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
Oct 15 15:34:13 fluffy kernel: [    6.224355] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
Oct 15 15:34:13 fluffy kernel: [    6.224969] cx8800 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
Oct 15 15:34:13 fluffy kernel: [    6.226532] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
Oct 15 15:34:13 fluffy kernel: [    6.226535] cx88[0]: TV tuner type -1, Radio tuner type -1
Oct 15 15:34:13 fluffy kernel: [    6.693828] cx88[0]: hauppauge eeprom: model=69100
Oct 15 15:34:13 fluffy kernel: [    7.176130] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:08.0/0000:01:06.0/rc/rc1/input6
Oct 15 15:34:13 fluffy kernel: [    7.176204] rc1: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:08.0/0000:01:06.0/rc/rc1
Oct 15 15:34:13 fluffy kernel: [    7.176285] rc rc1: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
Oct 15 15:34:13 fluffy kernel: [    7.176291] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 19, latency: 64, mmio: 0xfc000000
Oct 15 15:34:13 fluffy kernel: [    7.176398] cx88[0]/0: registered device video0 [v4l2]
Oct 15 15:34:13 fluffy kernel: [    7.176425] cx88[0]/0: registered device vbi0
Oct 15 15:34:13 fluffy kernel: [    7.176735] cx8800 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Oct 15 15:34:13 fluffy kernel: [    7.178335] cx88[1]: subsystem: 17de:08a6, board: KWorld/VStream XPert DVB-T [card=14,autodetected], frontend(s): 1
Oct 15 15:34:13 fluffy kernel: [    7.178337] cx88[1]: TV tuner type 4, Radio tuner type -1
Oct 15 15:34:13 fluffy kernel: [    7.560123] input: cx88 IR (KWorld/VStream XPert D as /devices/pci0000:00/0000:00:08.0/0000:01:07.0/rc/rc2/input7
Oct 15 15:34:13 fluffy kernel: [    7.560196] rc2: cx88 IR (KWorld/VStream XPert D as /devices/pci0000:00/0000:00:08.0/0000:01:07.0/rc/rc2
Oct 15 15:34:13 fluffy kernel: [    7.560203] cx88[1]/0: found at 0000:01:07.0, rev: 5, irq: 18, latency: 64, mmio: 0xf8000000
Oct 15 15:34:13 fluffy kernel: [    7.560319] cx88[1]/0: registered device video1 [v4l2]
Oct 15 15:34:13 fluffy kernel: [    7.560346] cx88[1]/0: registered device vbi1
Oct 15 15:34:13 fluffy kernel: [    7.560449] cx88[0]/2: cx2388x 8802 Driver Manager
Oct 15 15:34:13 fluffy kernel: [    7.560468] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
Oct 15 15:34:13 fluffy kernel: [    7.560475] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 19, latency: 64, mmio: 0xfa000000
Oct 15 15:34:13 fluffy kernel: [    7.560531] cx88[1]/2: cx2388x 8802 Driver Manager
Oct 15 15:34:13 fluffy kernel: [    7.560542] cx88-mpeg driver manager 0000:01:07.2: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Oct 15 15:34:13 fluffy kernel: [    7.560547] cx88[1]/2: found at 0000:01:07.2, rev: 5, irq: 18, latency: 64, mmio: 0xf7000000
Oct 15 15:34:13 fluffy kernel: [    8.515447] cx88_audio 0000:01:06.1: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
Oct 15 15:34:13 fluffy kernel: [    8.515487] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
Oct 15 15:34:13 fluffy kernel: [    8.611699] cx88/2: cx2388x dvb driver version 0.0.8 loaded
Oct 15 15:34:13 fluffy kernel: [    8.611703] cx88/2: registering cx8802 driver, type: dvb access: shared
Oct 15 15:34:13 fluffy kernel: [    8.611707] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
Oct 15 15:34:13 fluffy kernel: [    8.611710] cx88[0]/2: cx2388x based DVB/ATSC card
Oct 15 15:34:13 fluffy kernel: [    8.611712] cx8802_alloc_frontends() allocating 1 frontend(s)
Oct 15 15:34:13 fluffy kernel: [    9.121385] DVB: registering new adapter (cx88[0])
Oct 15 15:34:13 fluffy kernel: [    9.121759] cx88[1]/2: subsystem: 17de:08a6, board: KWorld/VStream XPert DVB-T [card=14]
Oct 15 15:34:13 fluffy kernel: [    9.121762] cx88[1]/2: cx2388x based DVB/ATSC card
Oct 15 15:34:13 fluffy kernel: [    9.121764] cx8802_alloc_frontends() allocating 1 frontend(s)
Oct 15 15:34:13 fluffy kernel: [    9.517935] DVB: registering new adapter (cx88[1])
Oct 15 15:49:54 fluffy kernel: [   19.906473] cx88/0: cx2388x v4l2 driver version 0.0.8 loaded
Oct 15 15:49:54 fluffy kernel: [   19.908222] cx8800 0000:01:06.0: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
Oct 15 15:49:54 fluffy kernel: [   19.909998] cx88[0]: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69,autodetected], frontend(s): 1
Oct 15 15:49:54 fluffy kernel: [   19.910001] cx88[0]: TV tuner type -1, Radio tuner type -1
Oct 15 15:49:54 fluffy kernel: [   20.001895] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.8 loaded
Oct 15 15:49:54 fluffy kernel: [   20.107150] cx88[0]: hauppauge eeprom: model=69100
Oct 15 15:49:54 fluffy kernel: [   20.136224] input: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:08.0/0000:01:06.0/rc/rc0/input3
Oct 15 15:49:54 fluffy kernel: [   20.136308] rc0: cx88 IR (Hauppauge WinTV-HVR400 as /devices/pci0000:00/0000:00:08.0/0000:01:06.0/rc/rc0
Oct 15 15:49:54 fluffy kernel: [   20.139582] rc rc0: lirc_dev: driver ir-lirc-codec (cx88xx) registered at minor = 0
Oct 15 15:49:54 fluffy kernel: [   20.139592] cx88[0]/0: found at 0000:01:06.0, rev: 5, irq: 19, latency: 64, mmio: 0xfc000000
Oct 15 15:49:54 fluffy kernel: [   20.139711] cx88[0]/0: registered device video0 [v4l2]
Oct 15 15:49:54 fluffy kernel: [   20.139738] cx88[0]/0: registered device vbi0
Oct 15 15:49:54 fluffy kernel: [   20.140943] cx8800 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Oct 15 15:49:54 fluffy kernel: [   20.142840] cx88[1]: subsystem: 17de:08a6, board: KWorld/VStream XPert DVB-T [card=14,autodetected], frontend(s): 1
Oct 15 15:49:54 fluffy kernel: [   20.142843] cx88[1]: TV tuner type 4, Radio tuner type -1
Oct 15 15:49:54 fluffy kernel: [   21.004128] input: cx88 IR (KWorld/VStream XPert D as /devices/pci0000:00/0000:00:08.0/0000:01:07.0/rc/rc2/input6
Oct 15 15:49:54 fluffy kernel: [   21.004201] rc2: cx88 IR (KWorld/VStream XPert D as /devices/pci0000:00/0000:00:08.0/0000:01:07.0/rc/rc2
Oct 15 15:49:54 fluffy kernel: [   21.004207] cx88[1]/0: found at 0000:01:07.0, rev: 5, irq: 18, latency: 64, mmio: 0xf8000000
Oct 15 15:49:54 fluffy kernel: [   21.004312] cx88[1]/0: registered device video1 [v4l2]
Oct 15 15:49:54 fluffy kernel: [   21.004340] cx88[1]/0: registered device vbi1
Oct 15 15:49:54 fluffy kernel: [   21.011054] cx88[0]/2: cx2388x 8802 Driver Manager
Oct 15 15:49:54 fluffy kernel: [   21.011073] cx88-mpeg driver manager 0000:01:06.2: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
Oct 15 15:49:54 fluffy kernel: [   21.011081] cx88[0]/2: found at 0000:01:06.2, rev: 5, irq: 19, latency: 64, mmio: 0xfa000000
Oct 15 15:49:54 fluffy kernel: [   21.011195] cx88[1]/2: cx2388x 8802 Driver Manager
Oct 15 15:49:54 fluffy kernel: [   21.011203] cx88-mpeg driver manager 0000:01:07.2: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Oct 15 15:49:54 fluffy kernel: [   21.011208] cx88[1]/2: found at 0000:01:07.2, rev: 5, irq: 18, latency: 64, mmio: 0xf7000000
Oct 15 15:49:54 fluffy kernel: [   21.013662] cx88_audio 0000:01:06.1: PCI INT A -> Link[LNKA] -> GSI 19 (level, low) -> IRQ 19
Oct 15 15:49:54 fluffy kernel: [   21.013694] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards
Oct 15 15:49:54 fluffy kernel: [   21.019535] cx88/2: cx2388x dvb driver version 0.0.8 loaded
Oct 15 15:49:54 fluffy kernel: [   21.019539] cx88/2: registering cx8802 driver, type: dvb access: shared
Oct 15 15:49:54 fluffy kernel: [   21.019543] cx88[0]/2: subsystem: 0070:6906, board: Hauppauge WinTV-HVR4000(Lite) DVB-S/S2 [card=69]
Oct 15 15:49:54 fluffy kernel: [   21.019546] cx88[0]/2: cx2388x based DVB/ATSC card
Oct 15 15:49:54 fluffy kernel: [   21.019548] cx8802_alloc_frontends() allocating 1 frontend(s)
Oct 15 15:49:54 fluffy kernel: [   21.038043] DVB: registering new adapter (cx88[0])
Oct 15 15:49:54 fluffy kernel: [   21.038394] cx88[1]/2: subsystem: 17de:08a6, board: KWorld/VStream XPert DVB-T [card=14]
Oct 15 15:49:54 fluffy kernel: [   21.038397] cx88[1]/2: cx2388x based DVB/ATSC card
Oct 15 15:49:54 fluffy kernel: [   21.038399] cx8802_alloc_frontends() allocating 1 frontend(s)
Oct 15 15:49:54 fluffy kernel: [   21.048254] DVB: registering new adapter (cx88[1])

```

While MythTV is recording a program, at some point I will get the following repeated in kern.log every 0.007 seconds:

```

cx88[1]: irq mpeg  [0x80000] pci_abort*
cx88[1]/2-mpeg: general errors: 0x00080000

```

The recording is then broken and Myth backend usually crashes. 

So far, today's kern.log is 730MB and syslog is around the same but I've managed to manually break the 8.7 million line file into four chunks containing the kernel start up messages from the four boot-ups the machine has done today (including one under 11.04).

I had seen crashes under 11.04, but these were due to the imon VFD driver, although the symptoms were similar - a very high rate of repeated messages into syslog. I haven't seen that under 11.10, but then I haven't been able to leave the machine running for very long so far.

The machine is now running Memtest overnight to rule out memory issues but is anyone else now having trouble with cx88 DVB cards?

I'd welcome suggestions for files to post tomorrow morning when the memtest has run for long enough. Or should I just try and put my tarball of 11.04 back on and be done with it?

Fingers crossed it can be saved before WAF reaches an unrecoverable low and I'm forced to buy a 'real' PVR.

---

### Post by thejpster on 2011-10-16
I have taken the Hauppauge DVB-S2 card out and the remaining KWorld DVB-T card seems to be working OK. This will do for now, but if I get a quiet moment I'll swap in the DVB-S2 in place of the DVB-T and see how it fares on its own.

This would be so much easier if I had sufficient hardware to maintain production/test environments. Sadly the living room cabinet doesn't allow for such luxuries.

---

### Post by thejpster on 2011-10-16
A few more updates. I have taken the DVB-T card out and put the DVB-S2 card back in temporarily. I get the same errors.

If I stop myth-backend and run scan, I get:

```

myth-desktop@fluffy:~$ scan /usr/share/dvb/dvb-s/Astra-28.2E 
scanning /usr/share/dvb/dvb-s/Astra-28.2E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 11720000 H 29500000 3
initial transponder 11740000 V 27500000 2
initial transponder 11758000 H 27500000 2
initial transponder 11778000 V 27500000 2
initial transponder 11798000 H 29500000 3
initial transponder 11817000 V 27500000 2
initial transponder 11836000 H 27500000 2
initial transponder 11856000 V 27500000 2
initial transponder 11876000 H 27500000 2
initial transponder 11895000 V 27500000 2
initial transponder 11914000 H 27500000 2
initial transponder 11934000 V 27500000 2
initial transponder 11954000 H 27500000 2
initial transponder 12051000 V 27500000 2
initial transponder 12129000 V 27500000 2
initial transponder 12148000 H 27500000 2
initial transponder 12168000 V 27500000 2
initial transponder 12226000 H 27500000 2
initial transponder 12246000 V 27500000 2
initial transponder 12422000 H 27500000 2
initial transponder 12480000 V 27500000 2
initial transponder 11973000 V 27500000 2
initial transponder 11992000 H 27500000 2
initial transponder 12012000 V 27500000 2
initial transponder 12032000 H 27500000 2
initial transponder 12070000 H 27500000 2
initial transponder 12090000 V 27500000 2
initial transponder 12110000 H 27500000 2
initial transponder 12188000 H 27500000 2
initial transponder 12207000 V 27500000 2
initial transponder 12266000 H 27500000 2
initial transponder 12285000 V 27500000 2
initial transponder 12304000 H 27500000 2
initial transponder 12324000 V 29500000 3
initial transponder 12344000 H 29500000 3
initial transponder 12363000 V 29500000 3
initial transponder 12382000 H 27500000 2
initial transponder 12402000 V 27500000 2
initial transponder 12441000 V 27500000 2
initial transponder 12460000 H 27500000 2
initial transponder 10714000 H 22000000 5
initial transponder 10729000 V 22000000 5
initial transponder 10744000 H 22000000 5
initial transponder 10758000 V 22000000 5
initial transponder 10773000 H 22000000 5
initial transponder 10788000 V 22000000 5
initial transponder 10803000 H 22000000 5
initial transponder 10818000 V 22000000 5
initial transponder 10832000 H 22000000 5
initial transponder 10847000 V 22000000 5
initial transponder 10862000 H 22000000 5
initial transponder 10876000 V 22000000 5
initial transponder 10891000 H 22000000 5
initial transponder 10906000 V 22000000 5
initial transponder 10921000 H 22000000 5
initial transponder 10936000 V 22000000 5
initial transponder 11222170 H 27500000 2
initial transponder 11223670 V 27500000 2
initial transponder 11259000 V 27500000 2
initial transponder 11261000 H 27500000 2
initial transponder 11307000 H 27500000 2
initial transponder 11307000 V 27500000 2
initial transponder 11343000 V 27500000 2
initial transponder 11344000 H 27500000 2
initial transponder 11390000 H 27500000 2
initial transponder 11390000 V 27500000 2
initial transponder 11426000 H 27500000 2
initial transponder 11426000 V 27500000 2
initial transponder 11469000 H 27500000 2
initial transponder 11488000 V 27500000 2
initial transponder 11508000 H 27500000 2
initial transponder 11527000 V 27500000 2
initial transponder 11546000 H 27500000 2
initial transponder 11565000 V 27500000 2
initial transponder 11585000 H 27500000 2
initial transponder 11603850 V 27500000 2
initial transponder 11623000 H 27500000 2
initial transponder 11642000 V 27500000 2
initial transponder 11661540 H 27500000 2
initial transponder 11680770 V 27500000 2
initial transponder 12524000 H 27500000 2
initial transponder 12524000 V 27500000 2
initial transponder 12560000 H 27500000 2
initial transponder 12560000 V 27500000 2
initial transponder 12596000 V 27500000 2
initial transponder 12607000 H 27500000 3
initial transponder 12629000 V 6111000 3
initial transponder 12692000 V 19532000 1
>>> tune to: 11720:h:0:29500
DVB-S IF freq is 1120000
WARNING: >>> tuning failed!!!
>>> tune to: 11720:h:0:29500 (tuning failed)
DVB-S IF freq is 1120000
WARNING: >>> tuning failed!!!
>>> tune to: 11740:v:0:27500
DVB-S IF freq is 1140000
WARNING: >>> tuning failed!!!
>>> tune to: 11740:v:0:27500 (tuning failed)
DVB-S IF freq is 1140000
WARNING: >>> tuning failed!!!
>>> tune to: 11758:h:0:27500
DVB-S IF freq is 1158000
WARNING: >>> tuning failed!!!
>>> tune to: 11758:h:0:27500 (tuning failed)
DVB-S IF freq is 1158000
WARNING: >>> tuning failed!!!
>>> tune to: 11778:v:0:27500
DVB-S IF freq is 1178000
WARNING: filter timeout pid 0x0011
WARNING: filter timeout pid 0x0000
^C
ERROR: interrupted by SIGINT, dumping partial result...
dumping lists (0 services)

```

As soon as it locked on to a multiplex, it immediately filled my logs with the following (so I hit Control+C).

```

Oct 16 16:33:57 fluffy kernel: [ 2502.108785] cx88[0]: irq mpeg  [0x80000] pci_abort*
Oct 16 16:33:57 fluffy kernel: [ 2502.108790] cx88[0]/2-mpeg: general errors: 0x00080000
Oct 16 16:33:57 fluffy kernel: [ 2502.109008] cx88[0]: irq mpeg  [0x80000] pci_abort*
Oct 16 16:33:57 fluffy kernel: [ 2502.109010] cx88[0]/2-mpeg: general errors: 0x00080000
Oct 16 16:33:57 fluffy kernel: [ 2502.109495] cx88[0]: irq mpeg  [0x80000] pci_abort*
Oct 16 16:33:57 fluffy kernel: [ 2502.109498] cx88[0]/2-mpeg: general errors: 0x00080000
Oct 16 16:33:57 fluffy kernel: [ 2502.109982] cx88[0]: irq mpeg  [0x80000] pci_abort*
Oct 16 16:33:57 fluffy kernel: [ 2502.109985] cx88[0]/2-mpeg: general errors: 0x00080000
Oct 16 16:33:57 fluffy kernel: [ 2502.110472] cx88[0]: irq mpeg  [0x80000] pci_abort*

<snip 39,000 rows>

Oct 16 16:34:04 fluffy kernel: [ 2509.443651] cx88[0]/2-mpeg: general errors: 0x00080000
Oct 16 16:34:04 fluffy kernel: [ 2509.444141] cx88[0]: irq mpeg  [0x80000] pci_abort*
Oct 16 16:34:04 fluffy kernel: [ 2509.444144] cx88[0]/2-mpeg: general errors: 0x00080000
Oct 16 16:34:04 fluffy kernel: [ 2509.444152] cx8802_start_dma() Failed. Unsupported value in .mpeg (0x00000001)

```

---

### Post by thejpster on 2011-10-16
In the absence of any other ideas I've opened [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875803](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875803)

---

### Post by thejpster on 2011-10-16
It turns out that downgrading from BIOS 0905 to 0603 appears to fix the problem. I shall leave this all here in case anyone else has a similar issue (unlikely, but ...)

---

