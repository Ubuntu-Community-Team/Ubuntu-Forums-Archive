---
title: "Lost Sound"
date: 2010-11-01
forum: Multimedia Software
---

### Post by Brzhk on 2010-11-01
Hello,

Today my computer will not play any sound. I have absolutely no idea what do i need to show you, but here's some info i guess would be interesting. Has anyone met the same problem?

My computer details:
* intel HDA integrated (in my GA-X58A-UD3R)
*one X-fi xtreme audio that never worked under linux


[QUOTE="lspci -v"]00:00.0 Host bridge: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port (rev 13)
	Subsystem: Giga-byte Technology Device 5000
	Flags: fast devsel, IRQ 11
	Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000c000-0000cfff
	Memory behind bridge: fb900000-fb9fffff
	Prefetchable memory behind bridge: 00000000dff00000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:02.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: fb700000-fb7fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fb600000-fb6fffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:10.0 PIC: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: <access denied>

00:10.1 PIC: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 (rev 13) (prog-if 00 [8259])
	Flags: fast devsel

00:11.0 PIC: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: <access denied>

00:11.1 PIC: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 (rev 13) (prog-if 00 [8259])
	Flags: fast devsel

00:13.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller (rev 13) (prog-if 20 [IO(X)-APIC])
	Flags: bus master, fast devsel, latency 0
	Memory at fbfff000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>

00:14.0 PIC: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: i7core_edac
	Kernel modules: i7core_edac

00:14.1 PIC: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel modules: mce-xeon75xx

00:14.2 PIC: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13) (prog-if 00 [8259])
	Flags: fast devsel
	Capabilities: <access denied>

00:15.0 PIC: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers (rev 13) (prog-if 20 [IO(X)-APIC])
	Flags: fast devsel

00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at ff00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at fe00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fd00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fbffe000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 50
	Memory at fbff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: fbe00000-fbefffff
	Prefetchable memory behind bridge: 00000000f0000000-00000000f01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
	I/O behind bridge: 0000b000-0000bfff
	Memory behind bridge: fbd00000-fbdfffff
	Prefetchable memory behind bridge: 00000000f0200000-00000000f03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: fbc00000-fbcfffff
	Prefetchable memory behind bridge: 00000000f0400000-00000000f05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fbb00000-fbbfffff
	Prefetchable memory behind bridge: 00000000fba00000-00000000fbafffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at fc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at fb00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 (prog-if 00 [UHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at fa00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 (prog-if 20 [EHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fbffd000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=32
	Memory behind bridge: fb800000-fb8fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 47
	I/O ports at f900 [size=8]
	I/O ports at f800 [size=4]
	I/O ports at f700 [size=8]
	I/O ports at f600 [size=4]
	I/O ports at f500 [size=32]
	Memory at fbffc000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: medium devsel, IRQ 10
	Memory at fbffb000 (64-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

01:00.0 SATA controller: Marvell Technology Group Ltd. Device 9128 (rev 11) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology Device b000
	Flags: bus master, fast devsel, latency 0, IRQ 49
	I/O ports at cf00 [size=8]
	I/O ports at ce00 [size=4]
	I/O ports at cd00 [size=8]
	I/O ports at cc00 [size=4]
	I/O ports at cb00 [size=16]
	Memory at fb9ff000 (32-bit, non-prefetchable) [size=2K]
	[virtual] Expansion ROM at dff00000 [disabled] [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

02:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03) (prog-if 30)
	Subsystem: Giga-byte Technology Device 5007
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fb7fe000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd

03:00.0 VGA compatible controller: ATI Technologies Inc Radeon HD 5870 (Cypress) (prog-if 00 [VGA controller])
	Subsystem: ATI Technologies Inc Device 0b00
	Flags: bus master, fast devsel, latency 0, IRQ 52
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at fb6c0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at de00 [size=256]
	[virtual] Expansion ROM at fb600000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

03:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
	Subsystem: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
	Flags: bus master, fast devsel, latency 0, IRQ 51
	Memory at fb6fc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

04:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=04, secondary=05, subordinate=05, sec-latency=32
	Memory behind bridge: fbe00000-fbefffff
	Capabilities: <access denied>
	Kernel modules: shpchp

05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
	Subsystem: Creative Labs SB1040
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at fbefc000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

06:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fbdfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

06:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 18
	I/O ports at bf00 [size=8]
	I/O ports at be00 [size=4]
	I/O ports at bd00 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at bb00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

07:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 01 [AHCI 1.0])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fbcfe000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

07:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at af00 [size=8]
	I/O ports at ae00 [size=4]
	I/O ports at ad00 [size=8]
	I/O ports at ac00 [size=4]
	I/O ports at ab00 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: pata_jmicron

08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, fast devsel, latency 0, IRQ 48
	I/O ports at ee00 [size=256]
	Memory at fbaff000 (64-bit, prefetchable) [size=4K]
	Memory at fbaf8000 (64-bit, prefetchable) [size=16K]
	[virtual] Expansion ROM at fba00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

09:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at fb8ff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fb8f8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: firewire_ohci
	Kernel modules: firewire-ohci, ohci1394
[/QUOTE]

[QUOTE="lsmod | grep snd"] 
snd_hda_codec_ca0110     7434  1 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_realtek   299533  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  4 snd_hda_codec_ca0110,snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         105727  0 
snd_usbmidi_lib        21313  1 snd_usb_audio
snd_hwdep               6660  2 snd_usb_audio,snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi            5932  0 
snd_rawmidi            22207  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64117  16 snd_hda_codec_ca0110,snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm[/QUOTE]

[QUOTE="aplay -l"]
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC889 Analog [ALC889 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC889 Digital [ALC889 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  1: Generic [HD-Audio Generic], périphérique 3 : ATI HDMI [ATI HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  2: Generic_1 [HD-Audio Generic], périphérique 0 : CA0110 Analog [CA0110 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  2: Generic_1 [HD-Audio Generic], périphérique 1 : CA0110 Digital [CA0110 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  3: BUA200M [BUA-200M], périphérique 0 : USB Audio [USB Audio]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
[/QUOTE]

[QUOTE="messages"]Nov  1 09:20:39 gauss kernel: [   11.488944] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x10cba000
Nov  1 09:20:46 gauss kernel: [   18.493982] generic-usb 0003:047F:0716.0005: timeout initializing reports
Nov  1 09:20:46 gauss kernel: [   18.494092] generic-usb 0003:047F:0716.0005: hiddev98,hidraw4: USB HID v1.11 Device [Plantronics BUA-200M] on usb-0000:00:1a.7-6.3/input3
Nov  1 09:20:46 gauss kernel: [   18.498177] 6:1:1 : no or invalid class specific endpoint descriptor
Nov  1 09:20:46 gauss kernel: [   18.500812] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.
Nov  1 09:20:46 gauss kernel: [   18.501901] 6:2:1 : no or invalid class specific endpoint descriptor
Nov  1 09:20:46 gauss kernel: [   18.504383] 6:2:1: endpoint lacks sample rate attribute bit, cannot set.
Nov  1 09:20:48 gauss kernel: [   20.499731] usbcore: registered new interface driver snd-usb-audio
Nov  1 09:20:48 gauss kernel: [   20.568267] ppdev: user-space parallel port driver
Nov  1 09:20:48 gauss kernel: [   21.042538] [fglrx] Firegl kernel thread PID: 1672
Nov  1 09:20:48 gauss kernel: [   21.042795] [fglrx] IRQ 52 Enabled
Nov  1 09:20:48 gauss kernel: [   21.274114] [fglrx] Gart USWC size:1280 M.
Nov  1 09:20:48 gauss kernel: [   21.274117] [fglrx] Gart cacheable size:508 M.
Nov  1 09:20:48 gauss kernel: [   21.274121] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Nov  1 09:20:48 gauss kernel: [   21.274123] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
Nov  1 09:20:48 gauss kernel: [   21.274126] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
Nov  1 09:20:50 gauss kernel: [   23.108614] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro,commit=0
Nov  1 09:20:50 gauss kernel: [   23.196201] EXT4-fs (sdb1): re-mounted. Opts: commit=0
Nov  1 09:20:51 gauss kernel: [   23.809411] EXT4-fs (sdb5): re-mounted. Opts: commit=0
Nov  1 09:20:51 gauss kernel: [   23.811869] EXT4-fs (sdb6): re-mounted. Opts: commit=0
Nov  1 09:20:54 gauss kernel: [   26.590762] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
Nov  1 09:20:55 gauss kernel: [   27.496342] 6:2:1: endpoint lacks sample rate attribute bit, cannot set.
Nov  1 09:20:57 gauss kernel: [   29.511044] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.
Nov  1 09:21:09 gauss pulseaudio[1721]: main.c: Failed to acquire org.pulseaudio.Server: org.freedesktop.DBus.Error.Disconnected: Connection is closed
Nov  1 09:21:09 gauss pulseaudio[1721]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  1 09:21:12 gauss kernel: [   44.480287] 6:2:1: endpoint lacks sample rate attribute bit, cannot set.
Nov  1 09:21:13 gauss kernel: [   45.496500] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.
Nov  1 09:21:29 gauss kernel: [   61.495205] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.
Nov  1 09:21:31 gauss kernel: [   63.488730] 6:2:1: endpoint lacks sample rate attribute bit, cannot set.
Nov  1 09:21:33 gauss pulseaudio[1967]: alsa-mixer.c: Unable to load mixer: Argument invalide
Nov  1 09:21:35 gauss kernel: [   67.509223] 6:1:1: endpoint lacks sample rate attribute bit, cannot set.
Nov  1 09:21:36 gauss pulseaudio[1967]: alsa-mixer.c: Unable to load mixer: Argument invalide
Nov  1 09:21:38 gauss kernel: [   70.598295] azx_single_wait_for_response: 26 callbacks suppressed
Nov  1 09:21:50 gauss kernel: [   82.539727] lo: Disabled Privacy Extensions
[/QUOTE]

---

### Post by Brzhk on 2010-11-01
added: [LIST]
[*]bash alsa-info.sh --stdout 
[/LIST]

> **"bash alsa-info.sh --stdout"]
/sbin/alsactl: get_control:249: Cannot read control '2,0,0,Headset Capture Volume,0': Invalid argument
cat: /tmp/alsa-info.png2WIQiL3/alsactl.tmp: No such file or directory
upload=true&script=true&cardinfo=
!!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Nov  1 08:47:40 UTC 2010


!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"


!!DMI Information
!!---------------

Manufacturer:      Gigabyte Technology Co., Ltd.
Product Name:      X58A-UD3R


!!Kernel Information
!!------------------

Kernel release:    2.6.35-22-generic
Operating System:  GNU/Linux
Architecture:      x86_64
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.23


!!Loaded ALSA modules
!!-------------------

snd_hda_intel
snd_hda_intel
snd_hda_intel
snd_usb_audio


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbff4000 irq 50
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfb6fc000 irq 51
 2 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbefc000 irq 16
 3 [BUA200M        ]: USB-Audio - BUA-200M
                      Plantronics BUA-200M at usb-0000:00:1a.7-6.3, full speed


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
03:00.1 Audio device: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series]
04:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
05:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG


!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:3a3e
	Subsystem: 1458:a102
--
03:00.1 0403: 1002:aa50
	Subsystem: 1002:aa50
--
05:00.0 0403: 1102:0009
	Subsystem: 1102:0018


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_hda_intel
	bdl_pos_adj : 1,32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_hda_intel
	bdl_pos_adj : 1,32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_hda_intel
	bdl_pos_adj : 1,32,32,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	beep_mode : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	enable_msi : -1
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	index : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	model : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	patch : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	position_fix : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	power_save : 0
	power_save_controller : Y
	probe_mask : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	probe_only : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	single_cmd : N

!!Module: snd_usb_audio
	async_unlink : Y
	device_setup : 0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0
	enable : Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y,Y
	id : (null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null),(null)
	ignore_ctl_error : N
	index : -2,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	nrpacks : 8
	pid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1
	vid : -1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1,-1


!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC889
Address: 2
Function Id: 0x1
Vendor Id: 0x10ec0889
Subsystem Id: 0x1458a022
Revision Id: 0x100004
No Modem Function Group found
Default PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=1
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC889 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Converter: stream=0, channel=0
  Digital: Enabled Copyright
  Digital category: 0x12
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x07 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=0, device=0
  Control: name="Capture Volume", index=0, device=0
  Device: name="ALC889 Analog", type="Audio", device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x80 0x80]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x24
Node 0x08 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=1, device=0
  Control: name="Capture Volume", index=1, device=0
  Device: name="ALC889 Analog", type="Audio", device=2
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x23
Node 0x09 [Audio Input] wcaps 0x10011b: Stereo Amp-In
  Control: name="Capture Switch", index=2, device=0
  Control: name="Capture Volume", index=2, device=0
  Amp-In caps: ofs=0x10, nsteps=0x2e, stepsize=0x03, mute=1
  Amp-In vals:  [0x00 0x00]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Connection: 1
     0x22
Node 0x0a [Audio Input] wcaps 0x100391: Stereo Digital
  Control: name="IEC958 Capture Switch", index=0, device=0
  Control: name="IEC958 Capture Default", index=0, device=0
  Device: name="ALC889 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital: Enabled
  Digital category: 0x0
  PCM:
    rates [0x570]: 32000 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x1f
Node 0x0b [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Front Mic Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Front Mic Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=1, ofs=0
  Control: name="Line Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Control: name="Line Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x17, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-In vals:  [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97] [0x97 0x97]
  Connection: 10
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17
Node 0x0c [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Front Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Front Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x3e, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x40 0x40]
  Connection: 2
     0x02 0x0b
Node 0x0d [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Surround Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Surround Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x3e, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3e 0x3e]
  Connection: 2
     0x03 0x0b
Node 0x0e [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Center Playback Volume", index=0, device=0
    ControlAmp: chs=1, dir=Out, idx=0, ofs=0
  Control: name="LFE Playback Volume", index=0, device=0
    ControlAmp: chs=2, dir=Out, idx=0, ofs=0
  Control: name="Center Playback Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=2, ofs=0
  Control: name="LFE Playback Switch", index=0, device=0
    ControlAmp: chs=2, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x3e, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3e 0x3e]
  Connection: 2
     0x04 0x0b
Node 0x0f [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Control: name="Side Playback Volume", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Control: name="Side Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=2, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x3e, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3e 0x3e]
  Connection: 2
     0x05 0x0b
Node 0x10 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC889 Digital", type="SPDIF", device=1
  Converter: stream=0, channel=0
  Digital: Enabled Copyright
  Digital category: 0x12
  PCM:
    rates [0x5f0]: 32000 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x11 [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x99430140: [Fixed] SPDIF Out at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0x4, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x10
Node 0x12 [Pin Complex] wcaps 0x400001: Stereo
  Pincap 0x00000020: IN
  Pin Default 0x411111f0: [N/A] Speaker at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x00:
Node 0x13 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x14 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x01014410: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x15 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000003c: IN OUT HP Detect
  Pin Default 0x01011412: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Black
    DefAssociation = 0x1, Sequence = 0x2
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d* 0x0e 0x0f 0x26
Node 0x16 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x01016411: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e* 0x0f 0x26
Node 0x17 [Pin Complex] wcaps 0x40018d: Stereo Amp-Out
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x00000034: IN OUT Detect
  Pin Default 0x01012414: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f* 0x26
Node 0x18 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x01a19c50: [Jack] Mic at Ext Rear
    Conn = 1/8, Color = Pink
    DefAssociation = 0x5, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x19 [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Front Mic Boost", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02a19c60: [Jack] Mic at Ext Front
    Conn = 1/8, Color = Pink
    DefAssociation = 0x6, Sequence = 0x0
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x1a [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x80 0x80]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x0181345f: [Jack] Line In at Ext Rear
    Conn = 1/8, Color = Blue
    DefAssociation = 0x5, Sequence = 0xf
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c 0x0d 0x0e 0x0f 0x26*
Node 0x1b [Pin Complex] wcaps 0x40018f: Stereo Amp-In Amp-Out
  Control: name="Headphone Playback Switch", index=0, device=0
    ControlAmp: chs=3, dir=Out, idx=0, ofs=0
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0000373c: IN OUT HP Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x02214c20: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x2, Sequence = 0x0
  Pin-ctls: 0xc0: OUT HP VREF_HIZ
  Unsolicited: tag=00, enabled=0
  Connection: 5
     0x0c* 0x0d 0x0e 0x0f 0x26
Node 0x1c [Pin Complex] wcaps 0x400081: Stereo
  Pincap 0x00000024: IN Detect
  Pin Default 0x593301f0: [N/A] CD at Int ATAPI
    Conn = ATAPI, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x1d [Pin Complex] wcaps 0x400000: Mono
  Pincap 0x00000020: IN
  Pin Default 0x4005e601: [N/A] Line Out at Ext N/A
    Conn = Optical, Color = White
    DefAssociation = 0x0, Sequence = 0x1
  Pin-ctls: 0x20: IN
Node 0x1e [Pin Complex] wcaps 0x400300: Mono Digital
  Pincap 0x00000010: OUT
  Pin Default 0x014b6130: [Jack] SPDIF Out at Ext Rear
    Conn = Comb, Color = Orange
    DefAssociation = 0x3, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x40: OUT
  Connection: 1
     0x06
Node 0x1f [Pin Complex] wcaps 0x400280: Mono Digital
  Pincap 0x00000020: IN
  Pin Default 0x01cb7170: [Jack] SPDIF In at Ext Rear
    Conn = Comb, Color = Yellow
    DefAssociation = 0x7, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
Node 0x20 [Vendor Defined Widget] wcaps 0xf00040: Mono
  Processing caps: benign=0, ncoeff=28
Node 0x21 [Vendor Defined Widget] wcaps 0xf00000: Mono
Node 0x22 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=2, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x23 [Audio Mixer] wcaps 0x20010b: Stereo Amp-In
  Control: name="Input Source", index=1, device=0
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80] [0x80 0x80]
  Connection: 11
     0x18 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b
Node 0x24 [Audio Selector] wcaps 0x300101: Stereo
  Control: name="Input Source", index=0, device=0
  Connection: 12
     0x18* 0x19 0x1a 0x1b 0x1c 0x1d 0x14 0x15 0x16 0x17 0x0b 0x12
Node 0x25 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x26 [Audio Mixer] wcaps 0x20010f: Stereo Amp-In Amp-Out
  Amp-In caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-In vals:  [0x00 0x00] [0x00 0x00]
  Amp-Out caps: ofs=0x3e, nsteps=0x40, stepsize=0x03, mute=0
  Amp-Out vals:  [0x3e 0x3e]
  Connection: 2
     0x25 0x0b
Codec: ATI R6xx HDMI
Address: 0
Function Id: 0x1
Vendor Id: 0x1002aa01
Subsystem Id: 0x00aa0100
Revision Id: 0x100200
No Modem Function Group found
Default PCM:
    rates [0x70]: 32000 44100 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Device: name="ATI HDMI", type="HDMI", device=3
  Converter: stream=0, channel=0
  Digital: Enabled
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x00000094: OUT Detect HDMI
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
Codec: Creative CA0110-IBG
Address: 1
Function Id: 0x1
Vendor Id: 0x1102000a
Subsystem Id: 0x11021006
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
N/A
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
Invalid AFG subtree
--endcollapse--


!!USB Mixer information
!!---------------------------
--startcollapse--

USB Mixer: usb_id=0x047f0716, ctrlif=0, ctlerr=0
Card: Plantronics BUA-200M at usb-0000:00:1a.7-6.3, full speed
  Unit: 2
    Control: name="Headset Capture Volume", index=0
    Info: id=2, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 5
    Control: name="PCM Playback Volume", index=0
    Info: id=5, control=2, cmask=0x0, channels=1, type="S16"
    Volume: min=0, max=1, dBmin=0, dBmax=0
  Unit: 5
    Control: name="PCM Playback Switch", index=0
    Info: id=5, control=1, cmask=0x0, channels=1, type="INV_BOOLEAN"
    Volume: min=0, max=1, dBmin=0, dBmax=0
--endcollapse--


!!ALSA Device nodes
!!-----------------

crw-rw----+ 1 root audio 116, 10 Nov  1 09:20 /dev/snd/controlC0
crw-rw----+ 1 root audio 116, 13 Nov  1 09:20 /dev/snd/controlC1
crw-rw----+ 1 root audio 116, 19 Nov  1 09:20 /dev/snd/controlC2
crw-rw----+ 1 root audio 116, 22 Nov  1 09:20 /dev/snd/controlC3
crw-rw----+ 1 root audio 116,  9 Nov  1 09:20 /dev/snd/hwC0D2
crw-rw----+ 1 root audio 116, 12 Nov  1 09:20 /dev/snd/hwC1D0
crw-rw----+ 1 root audio 116, 18 Nov  1 09:20 /dev/snd/hwC2D1
crw-rw----+ 1 root audio 116,  8 Nov  1 09:25 /dev/snd/pcmC0D0c
crw-rw----+ 1 root audio 116,  7 Nov  1 09:21 /dev/snd/pcmC0D0p
crw-rw----+ 1 root audio 116,  6 Nov  1 09:21 /dev/snd/pcmC0D1c
crw-rw----+ 1 root audio 116,  5 Nov  1 09:21 /dev/snd/pcmC0D1p
crw-rw----+ 1 root audio 116,  4 Nov  1 09:20 /dev/snd/pcmC0D2c
crw-rw----+ 1 root audio 116, 11 Nov  1 09:21 /dev/snd/pcmC1D3p
crw-rw----+ 1 root audio 116, 17 Nov  1 09:21 /dev/snd/pcmC2D0c
crw-rw----+ 1 root audio 116, 16 Nov  1 09:21 /dev/snd/pcmC2D0p
crw-rw----+ 1 root audio 116, 15 Nov  1 09:21 /dev/snd/pcmC2D1c
crw-rw----+ 1 root audio 116, 14 Nov  1 09:21 /dev/snd/pcmC2D1p
crw-rw----+ 1 root audio 116, 21 Nov  1 09:21 /dev/snd/pcmC3D0c
crw-rw----+ 1 root audio 116, 20 Nov  1 09:21 /dev/snd/pcmC3D0p
crw-rw----+ 1 root audio 116,  3 Nov  1 09:20 /dev/snd/seq
crw-rw----+ 1 root audio 116,  2 Nov  1 09:20 /dev/snd/timer

/dev/snd/by-id:
total 0
drwxr-xr-x 2 root root  60 Nov  1 09:20 .
drwxr-xr-x 4 root root 500 Nov  1 09:20 ..
lrwxrwxrwx 1 root root  12 Nov  1 09:20 usb-Plantronics_BUA-200M-00 -> ../controlC3

/dev/snd/by-path:
total 0
drwxr-xr-x 2 root root 120 Nov  1 09:20 .
drwxr-xr-x 4 root root 500 Nov  1 09:20 ..
lrwxrwxrwx 1 root root  12 Nov  1 09:20 pci-0000:00:1a.7-usb-0:6.3:1.0 -> ../controlC3
lrwxrwxrwx 1 root root  12 Nov  1 09:20 pci-0000:00:1b.0 -> ../controlC0
lrwxrwxrwx 1 root root  12 Nov  1 09:20 pci-0000:03:00.1 -> ../controlC1
lrwxrwxrwx 1 root root  12 Nov  1 09:20 pci-0000:05:00.0 -> ../controlC2


!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic_1 [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Generic_1 [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: BUA200M [BUA-200M], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC889 Analog [ALC889 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 2: Generic_1 [HD-Audio Generic], device 0: CA0110 Analog [CA0110 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 2: Generic_1 [HD-Audio Generic], device 1: CA0110 Digital [CA0110 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: BUA200M [BUA-200M], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xfbff4000 irq 50'
  Mixer name	: 'Realtek ALC889'
  Components	: 'HDA:10ec0889,1458a022,00100004'
  Controls      : 38
  Simple ctrls  : 21
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pswitch penum
  Playback channels: Front Left - Front Right
  Mono:
  Front Left: Playback [on]
  Front Right: Playback [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [2.00dB] [on]
  Front Right: Playback 64 [100%] [2.00dB] [on]
Simple mixer control 'Front Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Front Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 62 [97%] [0.00dB] [on]
  Front Right: Playback 62 [97%] [0.00dB] [on]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 62 [97%] [0.00dB] [on]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 62 [97%] [0.00dB] [on]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 62 [97%] [0.00dB] [on]
  Front Right: Playback 62 [97%] [0.00dB] [on]
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 23 [74%] [0.00dB] [off]
  Front Right: Playback 23 [74%] [0.00dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Mono
  Mono: Playback [on] Capture [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [off]
  Front Right: Capture 0 [0%] [-16.00dB] [off]
Simple mixer control 'Capture',1
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Capture',2
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 46
  Front Left: Capture 0 [0%] [-16.00dB] [on]
  Front Right: Capture 0 [0%] [-16.00dB] [on]
Simple mixer control 'Input Source',0
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',1
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'
Simple mixer control 'Input Source',2
  Capabilities: cenum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'

!!-------Mixer controls for card 1 [Generic]

Card hw:1 'Generic'/'HD-Audio Generic at 0xfb6fc000 irq 51'
  Mixer name	: 'ATI R6xx HDMI'
  Components	: 'HDA:1002aa01,00aa0100,00100200'
  Controls      : 4
  Simple ctrls  : 1
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

!!-------Mixer controls for card 2 [Generic_1]

Card hw:2 'Generic_1'/'HD-Audio Generic at 0xfbefc000 irq 16'
  Mixer name	: 'Creative CA0110-IBG'
  Components	: 'HDA:1102000a,11021006,00100000'
  Controls      : 25
  Simple ctrls  : 11
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 103
  Mono:
  Front Left: Playback 103 [100%] [0.00dB] [off]
  Front Right: Playback 103 [100%] [0.00dB] [off]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 103
  Mono:
  Front Left: Playback 103 [100%] [0.00dB] [off]
  Front Right: Playback 103 [100%] [0.00dB] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [0.00dB] [off]
  Front Right: Playback 127 [100%] [0.00dB] [off]
Simple mixer control 'Line',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 127
  Front Left: Capture 125 [98%] [-64.00dB] [off]
  Front Right: Capture 125 [98%] [-64.00dB] [off]
Simple mixer control 'Mic',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 127
  Front Left: Capture 127 [100%] [0.00dB] [off]
  Front Right: Capture 127 [100%] [0.00dB] [off]
Simple mixer control 'IEC958',0
  Capabilities: cvolume pswitch pswitch-joined cswitch cswitch-joined penum
  Playback channels: Mono
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 127
  Mono: Playback [on]
  Front Left: Capture 127 [100%] [0.00dB] [on]
  Front Right: Capture 127 [100%] [0.00dB] [on]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]

!!-------Mixer controls for card 3 [BUA200M]

amixer: Mixer load hw:3 error: Invalid argument
Card hw:3 'BUA200M'/'Plantronics BUA-200M at usb-0000:00:1a.7-6.3, full speed'
  Mixer name	: 'USB Mixer'
  Components	: 'USB047f:0716'
  Controls      : 3
amixer: Mixer hw:3 load error: Invalid argument


!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--


!!All Loaded Modules
!!------------------

Module
usb_storage
parport_pc
ppdev
snd_hda_codec_ca0110
binfmt_misc
kvm_intel
kvm
snd_hda_codec_atihdmi
snd_hda_codec_realtek
snd_hda_intel
snd_hda_codec
snd_usb_audio
snd_usbmidi_lib
snd_hwdep
snd_pcm
snd_seq_midi
snd_rawmidi
snd_seq_midi_event
snd_seq
snd_timer
snd_seq_device
fglrx
i7core_edac
joydev
psmouse
serio_raw
snd
xpad
shpchp
led_class
edac_core
xhci_hcd
soundcore
snd_page_alloc
lp
parport
firewire_ohci
firewire_core
hid_logitech
ff_memless
usbhid
hid
crc_itu_t
r8169
ahci
pata_jmicron
mii
libahci


!!Sysfs Files
!!-----------

/sys/class/sound/hwC0D2/init_pin_configs:
0x11 0x99430140
0x12 0x411111f0
0x14 0x01014410
0x15 0x01011412
0x16 0x01016411
0x17 0x01012414
0x18 0x01a19c50
0x19 0x02a19c60
0x1a 0x0181345f
0x1b 0x02214c20
0x1c 0x593301f0
0x1d 0x4005e601
0x1e 0x014b6130
0x1f 0x01cb7170

/sys/class/sound/hwC0D2/driver_pin_configs:

/sys/class/sound/hwC0D2/user_pin_configs:

/sys/class/sound/hwC0D2/init_verbs:

/sys/class/sound/hwC1D0/init_pin_configs:
0x03 0x18560010

/sys/class/sound/hwC1D0/driver_pin_configs:

/sys/class/sound/hwC1D0/user_pin_configs:

/sys/class/sound/hwC1D0/init_verbs:

/sys/class/sound/hwC2D1/init_pin_configs:
0x0b 0x01014010
0x0c 0x01016011
0x0d 0x01011012
0x0e 0x01012014
0x0f 0x02214020
0x10 0x01813030
0x11 0x02a19040
0x12 0x01452150
0x13 0x01c51160

/sys/class/sound/hwC2D1/driver_pin_configs:

/sys/class/sound/hwC2D1/user_pin_configs:

/sys/class/sound/hwC2D1/init_verbs:


!!ALSA/HDA dmesg
!!------------------

[    6.357743]   alloc kstat_irqs on node -1
[    6.357750] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    6.357893]   alloc irq_desc for 50 on node -1
[    6.357894]   alloc kstat_irqs on node -1
[    6.357903] HDA Intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[    6.357928] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.398174] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[    6.460952] hda_codec: ALC889: BIOS auto-probing.
[    6.461097] firewire_core: created device fw0: GUID 00e95a36006cf049, S400
[    6.469316] HDA Intel 0000:03:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.469389]   alloc irq_desc for 51 on node -1
[    6.469391]   alloc kstat_irqs on node -1
[    6.469400] HDA Intel 0000:03:00.1: irq 51 for MSI/MSI-X
[    6.469425] HDA Intel 0000:03:00.1: setting latency timer to 64
[    6.632882] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
--
[    6.935841] r8169 0000:08:00.0: eth0: link up
[    7.517565] HDA Intel 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.609273] EXT4-fs (sdd1): re-mounted. Opts: errors=remount-ro,commit=0
--
[    8.045246] EXT4-fs (sdb6): re-mounted. Opts: commit=0
[    8.444550] hda-intel: spurious response 0x0:0x0, last cmd=0x000000
[   11.488944] hda-intel: azx_get_response timeout, switching to polling mode: last cmd=0x10cba000
[   12.506743] hda_intel: azx_get_response timeout, switching to single_cmd mode: last cmd=0x10cba000
[   17.376184] eth0: no IPv6 routers present
--
[   23.811869] EXT4-fs (sdb6): re-mounted. Opts: commit=0
[   26.590762] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   27.496342] 6:2:1: endpoint lacks sample rate attribute bit, cannot set.
--
[   70.598295] azx_single_wait_for_response: 26 callbacks suppressed
[   70.598299] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.599224] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.600145] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.601189] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.602358] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.603382] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.604293] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.605307] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.606410] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.607312] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.608222] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.609177] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.610208] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.611183] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.612168] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.613315] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.614362] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.615322] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.616233] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.617245] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.618355] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   70.906019] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   71.184992] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   71.464196] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   71.744747] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   72.024134] hda_codec: rates == 0 (nid=0x12, val=0x0, ovrd=0)
[   82.539727] lo: Disabled Privacy Extensions

[/QUOTE]

[QUOTE="cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients} said:**
> cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn;  sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|grep roduct; lsmod | egrep 'snd|usb|midi|udio'; aplay -l; sudo lshw -C sound
Advanced Linux Sound Architecture Driver Version 1.0.23.
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfbff4000 irq 50
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfb6fc000 irq 51
 2 [Generic_1      ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xfbefc000 irq 16
 3 [BUA200M        ]: USB-Audio - BUA-200M
                      Plantronics BUA-200M at usb-0000:00:1a.7-6.3, full speed
  2:        : timer
  3:        : sequencer
  4: [ 0- 2]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 1]: digital audio capture
  7: [ 0- 0]: digital audio playback
  8: [ 0- 0]: digital audio capture
  9: [ 0- 2]: hardware dependent
 10: [ 0]   : control
 11: [ 1- 3]: digital audio playback
 12: [ 1- 0]: hardware dependent
 13: [ 1]   : control
 14: [ 2- 1]: digital audio playback
 15: [ 2- 1]: digital audio capture
 16: [ 2- 0]: digital audio playback
 17: [ 2- 0]: digital audio capture
 18: [ 2- 1]: hardware dependent
 19: [ 2]   : control
 20: [ 3- 0]: digital audio playback
 21: [ 3- 0]: digital audio capture
 22: [ 3]   : control
00-02: HDA Codec 2
01-00: HDA Codec 0
02-01: HDA Codec 1
00-00: ALC889 Analog : ALC889 Analog : playback 1 : capture 1
00-01: ALC889 Digital : ALC889 Digital : playback 1 : capture 1
00-02: ALC889 Analog : ALC889 Analog : capture 2
01-03: ATI HDMI : ATI HDMI : playback 1
02-00: CA0110 Analog : CA0110 Analog : playback 1 : capture 2
02-01: CA0110 Digital : CA0110 Digital : playback 1 : capture 1
03-00: USB Audio : USB Audio : playback 1 : capture 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for brzhk: 
rm: ne peut enlever `/etc/asound.conf': Aucun fichier ou dossier de ce type
rm: ne peut enlever `/home/brzhk/.asound*': Aucun fichier ou dossier de ce type
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/loneowais/ppa/ubuntu/](http://ppa.launchpad.net/loneowais/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/loneowais/ppa/ubuntu/](http://ppa.launchpad.net/loneowais/ppa/ubuntu/) maverick/main Translation-fr
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg               
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en   
Atteint [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release.gpg                          
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-en              
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                          
Ign [http://ppa.launchpad.net/tiheum/equinox/ubuntu/](http://ppa.launchpad.net/tiheum/equinox/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tiheum/equinox/ubuntu/](http://ppa.launchpad.net/tiheum/equinox/ubuntu/) maverick/main Translation-fr
Réception de*: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg                          
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-fr
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick Release.gpg                      
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main Translation-en          
Atteint [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/main Translation-fr      
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                              
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-fr   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-fr
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-fr
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-fr
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-fr      
Ign [http://extras.ubuntu.com/ubuntu/](http://extras.ubuntu.com/ubuntu/) maverick/main Translation-fr              
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en    
Atteint [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-fr
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en    
Atteint [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-fr
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en      
Atteint [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/universe Translation-fr  
Atteint [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release                              
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                              
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release                              
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates Release.gpg              
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en  
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-fr  
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Réception de*: 2 [http://dl.google.com](http://dl.google.com) stable Release [1 338B]                  
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release                   
Atteint [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick/main amd64 Packages                  
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                         
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                  
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-fr
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-fr
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-fr
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick Release                          
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates Release                  
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources              
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                         
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                  
Atteint [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main amd64 Packages                  
Réception de*: 3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [630B]        
Atteint [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release.gpg                          
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-en              
Ign [http://linux.dropbox.com/ubuntu/](http://linux.dropbox.com/ubuntu/) maverick/main Translation-fr              
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/main Sources                     
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/restricted Sources       
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/universe Sources         
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/multiverse Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/main amd64 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/restricted amd64 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/universe amd64 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick/multiverse amd64 Packages
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources  
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/main Sources     
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/restricted Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/universe Sources 
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/multiverse Sources
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/main amd64 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Atteint [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Atteint [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
Atteint [http://linux.dropbox.com](http://linux.dropbox.com) maverick Release
Atteint [http://linux.dropbox.com](http://linux.dropbox.com) maverick/main amd64 Packages
2 157o réceptionnés en 0s (3 177o/s)
Lecture des listes de paquets... Fait
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
aptitude est déjà la plus récente version disponible.
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
Les NOUVEAUX paquets suivants vont être installés*:
  gnome-alsamixer 
0 paquets mis à jour, 1 nouvellement installés, 0 à enlever et 0 non mis à jour.
Il est nécessaire de télécharger 56,6ko d'archives. Après dépaquetage, 610ko seront utilisés.
Prendre*:1 [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) maverick/universe gnome-alsamixer amd64 0.9.7~cvs.20060916.ds.1-2 [56,6kB]
56,6ko téléchargés en 0s (215ko/s)   
Sélection du paquet gnome-alsamixer précédemment désélectionné.
(Lecture de la base de données... 160033 fichiers et répertoires déjà installés.)
Dépaquetage de gnome-alsamixer (à partir de .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-2_amd64.deb) ...
Traitement des actions différées («*triggers*») pour «*gconf2*»...
Traitement des actions différées («*triggers*») pour «*man-db*»...
Traitement des actions différées («*triggers*») pour «*python-gmenu*»...
Rebuilding /usr/share/applications/desktop.fr_FR.utf8.cache...
Traitement des actions différées («*triggers*») pour «*desktop-file-utils*»...
Traitement des actions différées («*triggers*») pour «*python-support*»...
Paramétrage de gnome-alsamixer (0.9.7~cvs.20060916.ds.1-2) ...
                                              
H/W path               Device       Class       Description
===========================================================
                                    system      X58A-UD3R
/0                                  bus         X58A-UD3R
/0/0                                memory      128KiB BIOS
/0/4                                processor   Intel(R) Core(TM) i7 CPU        
/0/4/c                              memory      64KiB L1 cache
/0/4/d                              memory      8MiB L2 cache
/0/16                               memory      6GiB System Memory
/0/16/0                             memory      2GiB DIMM 400 MHz (2.5 ns)
/0/16/1                             memory      DIMM [empty]
/0/16/2                             memory      2GiB DIMM 400 MHz (2.5 ns)
/0/16/3                             memory      DIMM [empty]
/0/16/4                             memory      2GiB DIMM 400 MHz (2.5 ns)
/0/16/5                             memory      DIMM [empty]
/0/100                              bridge      5520/5500/X58 I/O Hub to ESI Por
/0/100/1                            bridge      5520/5500/X58 I/O Hub PCI Expres
/0/100/1/0             scsi10       storage     Marvell Technology Group Ltd.
/0/100/1/0/0           /dev/sdc     disk        64GB C300-CTFDDAC064M
/0/100/1/0/0/1         /dev/sdc1    volume      100MiB Windows NTFS volume
/0/100/1/0/0/2         /dev/sdc2    volume      59GiB Windows NTFS volume
/0/100/1/0/1           /dev/sdd     disk        64GB C300-CTFDDAC064M
/0/100/1/0/1/1         /dev/sdd1    volume      59GiB EXT4 volume
/0/100/1/0/0.0.0                    processor   SCSI Processor
/0/100/2                            bridge      5520/5500/X58 I/O Hub PCI Expres
/0/100/2/0                          bus         uPD720200 USB 3.0 Host Controlle
/0/100/3                            bridge      5520/5500/X58 I/O Hub PCI Expres
/0/100/3/0                          display     Radeon HD 5870 (Cypress)
/0/100/3/0.1                        multimedia  Cypress HDMI Audio [Radeon HD 58
/0/100/10                           generic     5520/5500/X58 Physical and Link 
/0/100/10.1                         generic     5520/5500/X58 Routing and Protoc
/0/100/11                           generic     5520/5500 Physical and Link Laye
/0/100/11.1                         generic     5520/5500 Routing & Protocol Lay
/0/100/13                           generic     5520/5500/X58 I/O Hub I/OxAPIC I
/0/100/14                           generic     5520/5500/X58 I/O Hub System Man
/0/100/14.1                         generic     5520/5500/X58 I/O Hub GPIO and S
/0/100/14.2                         generic     5520/5500/X58 I/O Hub Control St
/0/100/15                           generic     5520/5500/X58 Trusted Execution 
/0/100/1a                           bus         82801JI (ICH10 Family) USB UHCI 
/0/100/1a.1                         bus         82801JI (ICH10 Family) USB UHCI 
/0/100/1a.2                         bus         82801JI (ICH10 Family) USB UHCI 
/0/100/1a.7                         bus         82801JI (ICH10 Family) USB2 EHCI
/0/100/1b                           multimedia  82801JI (ICH10 Family) HD Audio 
/0/100/1c                           bridge      82801JI (ICH10 Family) PCI Expre
/0/100/1c/0                         bridge      [SB X-Fi Xtreme Audio] CA0110-IB
/0/100/1c/0/0                       multimedia  [SB X-Fi Xtreme Audio] CA0110-IB
/0/100/1c.1                         bridge      82801JI (ICH10 Family) PCI Expre
/0/100/1c.1/0                       storage     JMB362/JMB363 Serial ATA Control
/0/100/1c.1/0.1        scsi0        storage     JMB362/JMB363 Serial ATA Control
/0/100/1c.1/0.1/0.0.0  /dev/cdrom1  disk        DVDRAM GSA-4040B
/0/100/1c.3                         bridge      82801JI (ICH10 Family) PCI Expre
/0/100/1c.3/0                       storage     JMB362/JMB363 Serial ATA Control
/0/100/1c.3/0.1                     storage     JMB362/JMB363 Serial ATA Control
/0/100/1c.4                         bridge      82801JI (ICH10 Family) PCI Expre
/0/100/1c.4/0          eth0         network     RTL8111/8168B PCI Express Gigabi
/0/100/1d                           bus         82801JI (ICH10 Family) USB UHCI 
/0/100/1d.1                         bus         82801JI (ICH10 Family) USB UHCI 
/0/100/1d.2                         bus         82801JI (ICH10 Family) USB UHCI 
/0/100/1d.7                         bus         82801JI (ICH10 Family) USB2 EHCI
/0/100/1e                           bridge      82801 PCI Bridge
/0/100/1e/6                         bus         TSB43AB23 IEEE-1394a-2000 Contro
/0/100/1f                           bridge      82801JIR (ICH10R) LPC Interface 
/0/100/1f.2            scsi4        storage     82801JI (ICH10 Family) SATA AHCI
/0/100/1f.2/0          /dev/sda     disk        1500GB WDC WD15EARS-00Z
/0/100/1f.2/0/1        /dev/sda1    volume      127MiB Windows reserved partitio
/0/100/1f.2/0/2        /dev/sda2    volume      1397GiB Windows NTFS volume
/0/100/1f.2/1          /dev/sdb     disk        1500GB WDC WD15EARS-00Z
/0/100/1f.2/1/1        /dev/sdb1    volume      9536MiB EXT4 volume
/0/100/1f.2/1/2        /dev/sdb2    volume      1387GiB Extended partition
/0/100/1f.2/1/2/5      /dev/sdb5    volume      46GiB Linux filesystem partition
/0/100/1f.2/1/2/6      /dev/sdb6    volume      1304GiB Linux filesystem partiti
/0/100/1f.2/1/2/7      /dev/sdb7    volume      37GiB Linux swap / Solaris parti
/0/100/1f.3                         bus         82801JI (ICH10 Family) SMBus Con
/0/1                   scsi22       storage     
/0/1/0.0.0             /dev/sde     disk        SCSI Disk
total 0
crw-rw----+  1 root audio 116,  2 2010-11-01 09:20 timer
crw-rw----+  1 root audio 116,  3 2010-11-01 09:20 seq
crw-rw----+  1 root audio 116, 12 2010-11-01 09:20 hwC1D0
crw-rw----+  1 root audio 116, 13 2010-11-01 09:20 controlC1
crw-rw----+  1 root audio 116,  4 2010-11-01 09:20 pcmC0D2c
crw-rw----+  1 root audio 116, 18 2010-11-01 09:20 hwC2D1
crw-rw----+  1 root audio 116,  9 2010-11-01 09:20 hwC0D2
crw-rw----+  1 root audio 116, 19 2010-11-01 09:20 controlC2
crw-rw----+  1 root audio 116, 10 2010-11-01 09:20 controlC0
crw-rw----+  1 root audio 116, 22 2010-11-01 09:20 controlC3
drwxr-xr-x   2 root root      120 2010-11-01 09:20 by-path
drwxr-xr-x   2 root root       60 2010-11-01 09:20 by-id
drwxr-xr-x   4 root root      500 2010-11-01 09:20 .
crw-rw----+  1 root audio 116, 11 2010-11-01 09:21 pcmC1D3p
crw-rw----+  1 root audio 116, 20 2010-11-01 09:21 pcmC3D0p
crw-rw----+  1 root audio 116, 21 2010-11-01 09:21 pcmC3D0c
crw-rw----+  1 root audio 116,  5 2010-11-01 09:21 pcmC0D1p
crw-rw----+  1 root audio 116,  6 2010-11-01 09:21 pcmC0D1c
crw-rw----+  1 root audio 116,  7 2010-11-01 09:21 pcmC0D0p
crw-rw----+  1 root audio 116, 16 2010-11-01 09:21 pcmC2D0p
crw-rw----+  1 root audio 116, 14 2010-11-01 09:21 pcmC2D1p
crw-rw----+  1 root audio 116, 17 2010-11-01 09:21 pcmC2D0c
crw-rw----+  1 root audio 116, 15 2010-11-01 09:21 pcmC2D1c
crw-rw----+  1 root audio 116,  8 2010-11-01 09:25 pcmC0D0c
drwxr-xr-x  19 root root     4180 2010-11-01 09:52 ..
cat: /dev/sndstat: Aucun fichier ou dossier de ce type
00:00.0 Host bridge [0600]: Intel Corporation 5520/5500/X58 I/O Hub to ESI Port [8086:3405] (rev 13)
00:01.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 [8086:3408] (rev 13)
00:02.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 2 [8086:3409] (rev 13)
00:03.0 PCI bridge [0604]: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 [8086:340a] (rev 13)
00:10.0 PIC [0800]: Intel Corporation 5520/5500/X58 Physical and Link Layer Registers Port 0 [8086:3425] (rev 13)
00:10.1 PIC [0800]: Intel Corporation 5520/5500/X58 Routing and Protocol Layer Registers Port 0 [8086:3426] (rev 13)
00:11.0 PIC [0800]: Intel Corporation 5520/5500 Physical and Link Layer Registers Port 1 [8086:3427] (rev 13)
00:11.1 PIC [0800]: Intel Corporation 5520/5500 Routing & Protocol Layer Register Port 1 [8086:3428] (rev 13)
00:13.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub I/OxAPIC Interrupt Controller [8086:342d] (rev 13)
00:14.0 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub System Management Registers [8086:342e] (rev 13)
00:14.1 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers [8086:3422] (rev 13)
00:14.2 PIC [0800]: Intel Corporation 5520/5500/X58 I/O Hub Control Status and RAS Registers [8086:3423] (rev 13)
00:15.0 PIC [0800]: Intel Corporation 5520/5500/X58 Trusted Execution Technology Registers [8086:342f] (rev 13)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4 [8086:3a37]
00:1a.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5 [8086:3a38]
00:1a.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6 [8086:3a39]
00:1a.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2 [8086:3a3c]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
00:1c.0 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1 [8086:3a40]
00:1c.1 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 2 [8086:3a42]
00:1c.3 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 4 [8086:3a46]
00:1c.4 PCI bridge [0604]: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 5 [8086:3a48]
00:1d.0 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1 [8086:3a34]
00:1d.1 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2 [8086:3a35]
00:1d.2 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3 [8086:3a36]
00:1d.7 USB Controller [0c03]: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1 [8086:3a3a]
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 90)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller [8086:3a16]
00:1f.2 SATA controller [0106]: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller [8086:3a22]
00:1f.3 SMBus [0c05]: Intel Corporation 82801JI (ICH10 Family) SMBus Controller [8086:3a30]
01:00.0 SATA controller [0106]: Marvell Technology Group Ltd. Device [1b4b:9128] (rev 11)
02:00.0 USB Controller [0c03]: NEC Corporation uPD720200 USB 3.0 Host Controller [1033:0194] (rev 03)
03:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 5870 (Cypress) [1002:6898]
03:00.1 Audio device [0403]: ATI Technologies Inc Cypress HDMI Audio [Radeon HD 5800 Series] [1002:aa50]
04:00.0 PCI bridge [0604]: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge [1102:7006]
05:00.0 Audio device [0403]: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG [1102:0009]
06:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
06:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 02)
07:00.0 SATA controller [0106]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
07:00.1 IDE interface [0101]: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller [197b:2363] (rev 03)
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
09:06.0 FireWire (IEEE 1394) [0c00]: Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link) [104c:8024]
/sbin/alsactl
Le nom de fichier /dev/dsp n'existe pas.
                     UTIL.       PID ACCÈS  COMMANDE
/dev/snd/controlC0:  brzhk      1967 F.... pulseaudio
dpkg*: *bin/slmodemd* introuvable.
[    0.000000] No AGP bridge found
[    0.000000] found SMP MP-table at [ffff8800000f5e70] f5e70
[    0.000000] No NUMA configuration found
[    0.000000] No AGP bridge found
[    1.525801] ACPI: No dock devices found.
[    1.635479] HEST: Table is not found!
[    1.685289] pnp: PnP ACPI: found 11 devices
[    1.746309] audit: initializing netlink socket (disabled)
[    1.746318] type=2000 audit(1288603228.570:1): initialized
[    1.772085] ERST: Table is not found!
[    1.774371] Fixed MDIO Bus: probed
[    1.797860] hub 1-0:1.0: USB hub found
[    1.817811] hub 2-0:1.0: USB hub found
[    1.818104] hub 3-0:1.0: USB hub found
[    1.818333] hub 4-0:1.0: USB hub found
[    1.818551] hub 5-0:1.0: USB hub found
[    1.818765] hub 6-0:1.0: USB hub found
[    1.818984] hub 7-0:1.0: USB hub found
[    1.819198] hub 8-0:1.0: USB hub found
[    1.819301] PNP: No PS/2 controller found. Probing ports directly.
[    1.820173] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.824422] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.405111] hub 1-6:1.0: USB hub found
[    6.150638] hub 9-0:1.0: USB hub found
[    6.173828] lp: driver loaded but no devices found
[    6.284503] type=1400 audit(1288599633.956:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=927 comm="apparmor_parser"
[    6.285166] type=1400 audit(1288599633.956:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=927 comm="apparmor_parser"
[    6.285560] type=1400 audit(1288599633.956:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=927 comm="apparmor_parser"
[    6.865306] type=1400 audit(1288599634.536:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=1226 comm="apparmor_parser"
[    6.865777] type=1400 audit(1288599634.536:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1231 comm="apparmor_parser"
[    6.866459] type=1400 audit(1288599634.536:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1227 comm="apparmor_parser"
[    6.866606] type=1400 audit(1288599634.536:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1230 comm="apparmor_parser"
[    6.867140] type=1400 audit(1288599634.536:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1227 comm="apparmor_parser"
[    6.867387] type=1400 audit(1288599634.536:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1230 comm="apparmor_parser"
[    6.867511] type=1400 audit(1288599634.536:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1227 comm="apparmor_parser"
[    6.868711] type=1400 audit(1288599634.546:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1228 comm="apparmor_parser"
[    6.875377] type=1400 audit(1288599634.546:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=1228 comm="apparmor_parser"
[    6.879573] type=1400 audit(1288599634.556:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=1228 comm="apparmor_parser"
[   20.499731] usbcore: registered new interface driver snd-usb-audio
[   26.590762] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
sudo: /etc/init.d/sl-modem-daemon: command not found
	Product Name: X58A-UD3R
	Product Name: X58A-UD3R
snd_seq_dummy           1806  0 
usb_storage            50372  0 
snd_hda_codec_ca0110     7434  1 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_realtek   299533  1 
snd_hda_intel          26019  2 
snd_hda_codec         100919  4 snd_hda_codec_ca0110,snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         105727  0 
snd_usbmidi_lib        21313  1 snd_usb_audio
snd_hwdep               6660  2 snd_usb_audio,snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_midi            5932  0 
snd_rawmidi            22207  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  3 snd_seq_dummy,snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  4 snd_seq_dummy,snd_seq_midi,snd_rawmidi,snd_seq
snd                    64117  16 snd_hda_codec_ca0110,snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
usbhid                 42062  1 hid_logitech
hid                    84678  2 hid_logitech,usbhid
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC889 Analog [ALC889 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC889 Digital [ALC889 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  1: Generic [HD-Audio Generic], périphérique 3 : ATI HDMI [ATI HDMI]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  2: Generic_1 [HD-Audio Generic], périphérique 0 : CA0110 Analog [CA0110 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  2: Generic_1 [HD-Audio Generic], périphérique 1 : CA0110 Digital [CA0110 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  3: BUA200M [BUA-200M], périphérique 0 : USB Audio [USB Audio]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
  *-multimedia            
       description: Audio device
       product: Cypress HDMI Audio [Radeon HD 5800 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:03:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:51 memory:fb6fc000-fb6fffff
  *-multimedia
       description: Audio device
       product: 82801JI (ICH10 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:50 memory:fbff4000-fbff7fff
  *-multimedia
       description: Audio device
       product: [SB X-Fi Xtreme Audio] CA0110-IBG
       vendor: Creative Labs
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=HDA Intel latency=32 maxlatency=20 mingnt=2
       resources: irq:16 memory:fbefc000-fbefffff


---

