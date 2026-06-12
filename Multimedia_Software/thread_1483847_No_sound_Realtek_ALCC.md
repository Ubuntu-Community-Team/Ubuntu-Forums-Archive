---
title: "No sound Realtek ALCC"
date: 2010-05-15
forum: Multimedia Software
---

### Post by rmcazorla on 2010-05-15
Hi friends, I'm trying to solve the problem with my sound that doesn't works in Ubuntu 10.04, I followed many threads on this forum and nothing worked, here are some information about the output of some commands:

rmcazorla@pc:~$ aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: SB [HDA ATI SB], dispositivo 0: ALC888 Analog [ALC888 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: SB [HDA ATI SB], dispositivo 1: ALC888 Digital [ALC888 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

---------------------------------------------------------------------------------------------------------
rmcazorla@pc:~$ lspci -v
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, 66MHz, medium devsel, latency 64
    Memory at <ignored> (64-bit, non-prefetchable)
    Kernel modules: ati-agp

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 0000a000-0000afff
    Memory behind bridge: f8900000-fe9fffff
    Prefetchable memory behind bridge: 00000000bff00000-00000000dfefffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
    I/O ports at e800 [size=8]
    I/O ports at e400 [size=4]
    I/O ports at e000 [size=8]
    I/O ports at dc00 [size=4]
    I/O ports at d800 [size=16]
    Memory at febffc00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    Memory at febfe000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at febfd000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at febfc000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
    Memory at febfb000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
    Memory at febfa000 (32-bit, non-prefetchable) [size=4K]
    Kernel driver in use: ohci_hcd

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
    Memory at febff800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 13)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: 66MHz, medium devsel
    I/O ports at 0b00 [size=16]
    Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 8a [Master SecP PriP])
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at ff00 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: pata_atiixp
    Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at febf4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (prog-if 01)
    Flags: bus master, 66MHz, medium devsel, latency 64
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
    I/O behind bridge: 0000b000-0000bfff
    Memory behind bridge: fea00000-feafffff

01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8400 GS] (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 1230
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at ac00 [size=128]
    [virtual] Expansion ROM at fe9e0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia-173, nvidia-current, nvidiafb, nouveau

02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
    Subsystem: Packard Bell B.V. Device e02d
    Flags: bus master, medium devsel, latency 64, IRQ 20
    I/O ports at b800 [size=256]
    Memory at feaffc00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: 8139too
    Kernel modules: 8139too, 8139cp


---------------------------------------------------------------------------------------------------------------------------------

rmcazorla@pc:~$ sudo lshw -C multimedia
[sudo] password for rmcazorla: 
  *-multimedia            
       description: Audio device
       product: SBx00 Azalia (Intel HDA)
       vendor: ATI Technologies Inc
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=HDA Intel latency=64
       resources: irq:16 memory:febf4000-febf7fff

------------------------------------------------------------------------------------------------------------------------------

I uninstalled pulseaudio to use alsamixer and everything is ok there, no silenced or anything, can anyon help me? Thank you in advice friends!

---

