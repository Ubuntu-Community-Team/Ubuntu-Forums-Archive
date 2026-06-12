---
title: "Sound not working in firefox (in dailymotion/youtube)"
date: 2010-01-08
forum: Multimedia Software
---

### Post by abrazafi on 2010-01-08
Hi,

Running desktop kubuntu 9.10. Spent a lot of time to figure out why youtube/dailymotion does not have any sound coming out of my headset.
Tried many instructions from:
        [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
without any success. So I need help.

Herewith my sound devices

> cat /proc/asound/modules
 1 snd_usb_audio
 2 saa7134_alsa
 3 snd_hda_intel

I want to use the above "snd_usb_audio" which is working fine with amarok and skype (separatly or at the same time).
I am using firefox version 3.5.6
Adobe Flash player version 10,0,42,34
Samething happened with the browser konqueror
   
any suggestion will be welcomed and many thanks,

Abdon.

====================== herewith some outputs from my system

> uname -a
Linux antec 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

> aplay -l

**** List of PLAYBACK Hardware Devices ****
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 3: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> cat /proc/asound/modules
 1 snd_usb_audio
 2 saa7134_alsa
 3 snd_hda_intel


> lspci -v

00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
   Subsystem: ASUSTeK Computer Inc. Device 8178
   Flags: bus master, fast devsel, latency 0
   Capabilities: <access denied>
   Kernel modules: i82975x_edac

00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
   I/O behind bridge: 0000c000-0000cfff
   Memory behind bridge: ff900000-ff9fffff
   Prefetchable memory behind bridge: 00000000cff00000-00000000efefffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 81d8
   Flags: bus master, fast devsel, latency 0, IRQ 19
   Memory at ffafc000 (64-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>
   Kernel driver in use: HDA Intel
   Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
   Prefetchable memory behind bridge: 00000000cfe00000-00000000cfefffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
   I/O behind bridge: 0000b000-0000bfff
   Memory behind bridge: ff800000-ff8fffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
   I/O behind bridge: 0000a000-0000afff
   Memory behind bridge: ff700000-ff7fffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
   I/O behind bridge: 00009000-00009fff
   Memory behind bridge: ff600000-ff6fffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 20
   I/O ports at e480 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 17
   I/O ports at e800 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 18
   I/O ports at e880 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 19
   I/O ports at ec00 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 20
   Memory at ffafbc00 (32-bit, non-prefetchable) [size=1K]
   Capabilities: <access denied>
   Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
   Memory behind bridge: ff500000-ff5fffff
   Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0
   Capabilities: <access denied>
   Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 22
   I/O ports at 01f0
   I/O ports at 03f4
   I/O ports at 0170
   I/O ports at 0374
   I/O ports at ffa0 [size=16]
   Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
   Subsystem: ASUSTeK Computer Inc. Device 2601
   Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23
   I/O ports at e400
   I/O ports at e080
   I/O ports at e000
   I/O ports at dc00
   I/O ports at d880 [size=16]
   Memory at ffafb800 (32-bit, non-prefetchable) [size=1K]
   Capabilities: <access denied>
   Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: medium devsel
   I/O ports at 0400 [size=32]
   Kernel modules: i2c-i801

01:00.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
   Subsystem: ASUSTeK Computer Inc. Device 4845
   Flags: bus master, medium devsel, latency 64, IRQ 21
   Memory at ff5ff800 (32-bit, non-prefetchable) [size=2K]
   Capabilities: <access denied>
   Kernel driver in use: saa7134
   Kernel modules: saa7134

01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
   Subsystem: ASUSTeK Computer Inc. Device 815b
   Flags: bus master, medium devsel, latency 64, IRQ 21
   Memory at ff5ff000 (32-bit, non-prefetchable) [size=2K]
   Memory at ff5f8000 (32-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>
   Kernel driver in use: ohci1394
   Kernel modules: firewire-ohci, ohci1394

02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03) (prog-if 01)
   Subsystem: ASUSTeK Computer Inc. Device 81e4
   Flags: bus master, fast devsel, latency 0, IRQ 17
   Memory at ff6fe000 (32-bit, non-prefetchable) [size=8K]
   Expansion ROM at ff6e0000 [disabled] [size=64K]
   Capabilities: <access denied>
   Kernel driver in use: ahci

02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
   Subsystem: ASUSTeK Computer Inc. Device 81e4
   Flags: bus master, fast devsel, latency 0, IRQ 18
   I/O ports at 9c00
   I/O ports at 9880
   I/O ports at 9800
   I/O ports at 9480
   I/O ports at 9400 [size=16]
   Capabilities: <access denied>
   Kernel driver in use: pata_jmicron

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
   Subsystem: ASUSTeK Computer Inc. Device 8142
   Flags: bus master, fast devsel, latency 0, IRQ 30
   Memory at ff7fc000 (64-bit, non-prefetchable) [size=16K]
   I/O ports at a800 [size=256]
   Expansion ROM at ff7c0000 [disabled] [size=128K]
   Capabilities: <access denied>
   Kernel driver in use: sky2
   Kernel modules: sky2

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
   Subsystem: ASUSTeK Computer Inc. Device 8142
   Flags: bus master, fast devsel, latency 0, IRQ 29
   Memory at ff8fc000 (64-bit, non-prefetchable) [size=16K]
   I/O ports at b800 [size=256]
   Expansion ROM at ff8c0000 [disabled] [size=128K]
   Capabilities: <access denied>
   Kernel driver in use: sky2
   Kernel modules: sky2

06:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
   Subsystem: PC Partner Limited Device 0840
   Flags: bus master, fast devsel, latency 0, IRQ 16
   Memory at d0000000 (64-bit, prefetchable) [size=256M]
   Memory at ff9f0000 (64-bit, non-prefetchable) [size=64K]
   I/O ports at c800 [size=256]
   Expansion ROM at ff9c0000 [disabled] [size=128K]
   Capabilities: <access denied>
   Kernel modules: radeon

06:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
   Subsystem: PC Partner Limited Device 0841
   Flags: bus master, fast devsel, latency 0
   Memory at ff9e0000 (64-bit, non-prefetchable) [size=64K]
   Capabilities: <access denied>

---

### Post by rand()m on 2010-01-08
> **abrazafi said:**
> Hi,

Running desktop kubuntu 9.10. Spent a lot of time to figure out why youtube/dailymotion does not have any sound coming out of my headset.
Tried many instructions from:
        [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
without any success. So I need help.

Herewith my sound devices

> cat /proc/asound/modules
 1 snd_usb_audio
 2 saa7134_alsa
 3 snd_hda_intel

I want to use the above "snd_usb_audio" which is working fine with amarok and skype (separatly or at the same time).
I am using firefox version 3.5.6
Adobe Flash player version 10,0,42,34
Samething happened with the browser konqueror
   
any suggestion will be welcomed and many thanks,

Abdon.

====================== herewith some outputs from my system

```
> uname -a
Linux antec 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

> aplay -l

**** List of PLAYBACK Hardware Devices ****
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 3: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> cat /proc/asound/modules
 1 snd_usb_audio
 2 saa7134_alsa
 3 snd_hda_intel


> lspci -v

00:00.0 Host bridge: Intel Corporation 82975X Memory Controller Hub (rev c0)
   Subsystem: ASUSTeK Computer Inc. Device 8178
   Flags: bus master, fast devsel, latency 0
   Capabilities: <access denied>
   Kernel modules: i82975x_edac

00:01.0 PCI bridge: Intel Corporation 82975X PCI Express Root Port (rev c0)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
   I/O behind bridge: 0000c000-0000cfff
   Memory behind bridge: ff900000-ff9fffff
   Prefetchable memory behind bridge: 00000000cff00000-00000000efefffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 81d8
   Flags: bus master, fast devsel, latency 0, IRQ 19
   Memory at ffafc000 (64-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>
   Kernel driver in use: HDA Intel
   Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
   Prefetchable memory behind bridge: 00000000cfe00000-00000000cfefffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
   I/O behind bridge: 0000b000-0000bfff
   Memory behind bridge: ff800000-ff8fffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
   I/O behind bridge: 0000a000-0000afff
   Memory behind bridge: ff700000-ff7fffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
   I/O behind bridge: 00009000-00009fff
   Memory behind bridge: ff600000-ff6fffff
   Capabilities: <access denied>
   Kernel driver in use: pcieport-driver
   Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 20
   I/O ports at e480 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 17
   I/O ports at e800 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 18
   I/O ports at e880 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 19
   I/O ports at ec00 [size=32]
   Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 20
   Memory at ffafbc00 (32-bit, non-prefetchable) [size=1K]
   Capabilities: <access denied>
   Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
   Flags: bus master, fast devsel, latency 0
   Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
   Memory behind bridge: ff500000-ff5fffff
   Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0
   Capabilities: <access denied>
   Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: bus master, medium devsel, latency 0, IRQ 22
   I/O ports at 01f0
   I/O ports at 03f4
   I/O ports at 0170
   I/O ports at 0374
   I/O ports at ffa0 [size=16]
   Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
   Subsystem: ASUSTeK Computer Inc. Device 2601
   Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 23
   I/O ports at e400
   I/O ports at e080
   I/O ports at e000
   I/O ports at dc00
   I/O ports at d880 [size=16]
   Memory at ffafb800 (32-bit, non-prefetchable) [size=1K]
   Capabilities: <access denied>
   Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
   Subsystem: ASUSTeK Computer Inc. Device 8179
   Flags: medium devsel
   I/O ports at 0400 [size=32]
   Kernel modules: i2c-i801

01:00.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
   Subsystem: ASUSTeK Computer Inc. Device 4845
   Flags: bus master, medium devsel, latency 64, IRQ 21
   Memory at ff5ff800 (32-bit, non-prefetchable) [size=2K]
   Capabilities: <access denied>
   Kernel driver in use: saa7134
   Kernel modules: saa7134

01:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
   Subsystem: ASUSTeK Computer Inc. Device 815b
   Flags: bus master, medium devsel, latency 64, IRQ 21
   Memory at ff5ff000 (32-bit, non-prefetchable) [size=2K]
   Memory at ff5f8000 (32-bit, non-prefetchable) [size=16K]
   Capabilities: <access denied>
   Kernel driver in use: ohci1394
   Kernel modules: firewire-ohci, ohci1394

02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03) (prog-if 01)
   Subsystem: ASUSTeK Computer Inc. Device 81e4
   Flags: bus master, fast devsel, latency 0, IRQ 17
   Memory at ff6fe000 (32-bit, non-prefetchable) [size=8K]
   Expansion ROM at ff6e0000 [disabled] [size=64K]
   Capabilities: <access denied>
   Kernel driver in use: ahci

02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03) (prog-if 85 [Master SecO PriO])
   Subsystem: ASUSTeK Computer Inc. Device 81e4
   Flags: bus master, fast devsel, latency 0, IRQ 18
   I/O ports at 9c00
   I/O ports at 9880
   I/O ports at 9800
   I/O ports at 9480
   I/O ports at 9400 [size=16]
   Capabilities: <access denied>
   Kernel driver in use: pata_jmicron

03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
   Subsystem: ASUSTeK Computer Inc. Device 8142
   Flags: bus master, fast devsel, latency 0, IRQ 30
   Memory at ff7fc000 (64-bit, non-prefetchable) [size=16K]
   I/O ports at a800 [size=256]
   Expansion ROM at ff7c0000 [disabled] [size=128K]
   Capabilities: <access denied>
   Kernel driver in use: sky2
   Kernel modules: sky2

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20)
   Subsystem: ASUSTeK Computer Inc. Device 8142
   Flags: bus master, fast devsel, latency 0, IRQ 29
   Memory at ff8fc000 (64-bit, non-prefetchable) [size=16K]
   I/O ports at b800 [size=256]
   Expansion ROM at ff8c0000 [disabled] [size=128K]
   Capabilities: <access denied>
   Kernel driver in use: sky2
   Kernel modules: sky2

06:00.0 VGA compatible controller: ATI Technologies Inc RV515 [Radeon X1300]
   Subsystem: PC Partner Limited Device 0840
   Flags: bus master, fast devsel, latency 0, IRQ 16
   Memory at d0000000 (64-bit, prefetchable) [size=256M]
   Memory at ff9f0000 (64-bit, non-prefetchable) [size=64K]
   I/O ports at c800 [size=256]
   Expansion ROM at ff9c0000 [disabled] [size=128K]
   Capabilities: <access denied>
   Kernel modules: radeon

06:00.1 Display controller: ATI Technologies Inc RV515 [Radeon X1300] (Secondary)
   Subsystem: PC Partner Limited Device 0841
   Flags: bus master, fast devsel, latency 0
   Memory at ff9e0000 (64-bit, non-prefetchable) [size=64K]
   Capabilities: <access denied>
```

I had some similarish sound problems. I'm now running XP again....

---

