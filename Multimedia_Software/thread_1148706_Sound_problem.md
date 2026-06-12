---
title: "Sound problem"
date: 2009-05-04
forum: Multimedia Software
---

### Post by Ganji57 on 2009-05-04
Hello everybody :),
I'd like to say that I'm sorry for my bad english, but I made this thread here because I can't find the solution on French forums. I'm very new with Ubuntu, I've just installed Ubuntu 9.04 on my PC.
Here is my problem : I don't hear anything.
I'm sorry but I can't read all the thread because I don't understand.
Here's my CPU specs : :popcorn:
Sound card : Intel Corporation 82801I (ICH9 Family)
I've got speakers and they are linked with screen. Screen is linked with HDMI with my PC.
I don't use a laptop.
I tried various thing but I can't make sound works. :confused:
(It works 100% on Windows)

> louis@ORDI-LOUIS:~$ aplay -l  
**** Liste des PLAYBACK périphériques ****
carte  0: Intel [HDA Intel], périphérique 0 : ALC1200 Analog [ALC1200 Analog]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0
carte  0: Intel [HDA Intel], périphérique 1 : ALC1200 Digital [ALC1200 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique: #0: subdevice #0> louis@ORDI-LOUIS:~$ lspci -v  
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 0000d000-0000dfff
    Memory behind bridge: fa000000-feafffff
    Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at b400 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at b480 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at f9efec00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f9ef4000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 00000000f8f00000-00000000f8ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at b800 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at b880 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at bc00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at c000 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f9eff800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
    Memory behind bridge: f9f00000-f9ffffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 2300
    I/O ports at c880 [size=8]
    I/O ports at c800 [size=4]
    I/O ports at c480 [size=8]
    I/O ports at c400 [size=4]
    I/O ports at c080 [size=32]
    Memory at f9eff000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: medium devsel, IRQ 10
    Memory at f9effc00 (64-bit, non-prefetchable) [size=256]
    I/O ports at 0400 [size=32]
    Kernel modules: i2c-i801

01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, medium devsel, latency 64, IRQ 20
    Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a6f
    Flags: bus master, fast devsel, latency 0, IRQ 2299
    I/O ports at e800 [size=256]
    Memory at febff000 (64-bit, non-prefetchable) [size=4K]
    Memory at f8ff0000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at febc0000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

04:00.0 VGA compatible controller: nVidia Corporation Device 0644 (rev a1)
    Subsystem: Micro-Star International Co., Ltd. Device 1330
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    [virtual] Expansion ROM at fea80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia, nvidiafbAnd my alpha-base.conf file (that I tried to fix :()
> 
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2I really hope someone can help me.

Thank you 

Have a nice day :guitar:

---

### Post by Ganji57 on 2009-05-04
Up please fix it :(

---

