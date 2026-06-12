---
title: "Fresh Ubuntu 10.10 install."
date: 2010-12-15
forum: Multimedia Software
---

### Post by dslreports_snakeoil on 2010-12-15
I am a complete newbie when it comes to terminal comnands. So any output you may need posted, please hold my hand and explain how to get it for you.

I will tell you this:
The hard ware is a MSI mother board [AMD flavored] [exact numbers, not known at the moment, but can be recovered].
The audio is built into the mother board. It worked fine with Ubuntu 10.04

I read a few posts here and there, and ran a hardware diagnostic. It came back and said no sound card was installed.

Which I know isn't the case.

---

### Post by gordintoronto on 2010-12-15
To run a command, open Accessories/terminal. One useful command is:
lspci
It should produce about 20 lines of output, one of which might include the words "Audio device." If so, perhaps you could use your mouse to highlight that line, right-click and select "copy". Then paste it into a message.

For the most extreme detail about your hardware, use this:
sudo lshw | more
The third line of output should identify your motherboard. Write it down and include it in a message. Press the space bar to get the next screenful of output until you reach the end. There might be a dozen lines about your audio device several pages into the output.

Do you have a manual, and does it tell you how to get into the BIOS setup? It's possible your audio device has been disabled somehow, and that is a BIOS setting.

By the way, it's always useful to state a question, such as "how can I get sound?"

---

### Post by dslreports_snakeoil on 2010-12-15
Thank you. Here is the lspci out put:
00:00.0 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:00.5 PIC: VIA Technologies, Inc. K8M890CE I/O APIC Interrupt Controller
00:00.7 Host bridge: VIA Technologies, Inc. K8M890CE Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:02.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:03.0 PCI bridge: VIA Technologies, Inc. K8T890 PCI to PCI Bridge Controller
00:0f.0 IDE interface: VIA Technologies, Inc. VT8237A SATA 2-Port Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 07)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev a0)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237A PCI to ISA Bridge
00:11.7 Host bridge: VIA Technologies, Inc. VT8251 Ultra VLINK Controller
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 7c)
00:13.0 Host bridge: VIA Technologies, Inc. VT8237A Host Bridge
00:13.1 PCI bridge: VIA Technologies, Inc. VT8237A PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1)
04:05.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)


The hardware:
description: Desktop Computer
    product: MS-7253
    vendor: MICRO-STAR INTERNATIONAL CO., LTD
    version: 1.00
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=2
  *-core
       description: Motherboard
       product: MS-7253
       vendor: MICRO-STAR INTERNATIONAL CO., LTD
       physical id: 0
       version: 1.00
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies, LTD
          physical id: 0
          version: V1.2 (01/25/2007)
          size: 128KiB
          capacity: 448KiB
          capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect sock
etedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5pr


product: AMD Athlon(tm) 64 X2 Dual Core Processor 3600+

  description: Audio device
product: VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller)


Also, I did have ubuntu 10.04 LTS installed and the audio had been working.

I would have put sound in the title, but hit post just as I remembered to do that. For some reason you can't edit titles after the post is posted.

I looked at my motherboard's BIOS. As this was a very high end board [kidding it was only 40 bucks], my bios options are very very slim. There was no setting for disabling the onboard sound card.

---

### Post by gordintoronto on 2010-12-15
Sorry, I don't think I can help. Perhaps System/Preferences/Sound shows your sound device?

I have a laptop with an Azalia sound device, and it works just fine in the latest version of Linux Mint, which is based on Ubuntu 10.10.

In many cases, sound is stopped by a "mute" setting somewhere. Perhaps that is something to look for.

---

