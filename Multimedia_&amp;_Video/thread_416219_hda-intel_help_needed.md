---
title: "hda-intel help needed"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by nullfactor on 2007-04-20
Hi all.

I followed the Comprehensive Sound Guide to the letter and met with some errors during compilation.  The errors are as follows:

make:
```
make dep
make[1]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13'
make[2]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore/ioctl32'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore/ioctl32'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore/oss'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore/oss'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore/seq'
make[4]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore/seq/instr'
make[4]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore/seq/instr'
make[4]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore/seq/oss'
make[4]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore/seq/oss'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore/seq'
make[2]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore'
make[2]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/i2c'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/i2c/other'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/i2c/other'
make[2]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/i2c'
make[2]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers/mpu401'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers/mpu401'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers/opl3'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers/opl3'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers/opl4'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers/opl4'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers/pcsp'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers/pcsp'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers/vx'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers/vx'
make[2]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/drivers'
make[2]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/ad1816a'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/ad1816a'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/ad1848'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/ad1848'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/cs423x'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/cs423x'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/es1688'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/es1688'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/gus'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/gus'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/msnd'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/msnd'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/opti9xx'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/opti9xx'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/sb'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/sb'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/wavefront'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa/wavefront'
make[2]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/isa'
make[2]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/synth'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/synth/emux'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/synth/emux'
make[2]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/synth'
make[2]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/ac97'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/ac97'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/ali5451'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/ali5451'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/asihpi'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/asihpi'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/au88x0'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/au88x0'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/ca0106'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/ca0106'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/cs46xx'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/cs46xx'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/cs5535audio'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/cs5535audio'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/echoaudio'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/echoaudio'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/emu10k1'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/emu10k1'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/hda'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/hda'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/ice1712'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/ice1712'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/korg1212'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/korg1212'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/mixart'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/mixart'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/nm256'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/nm256'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/pcxhr'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/pcxhr'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/pdplus'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/pdplus'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/riptide'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/riptide'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/rme9652'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/rme9652'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/trident'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/trident'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/vx222'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/vx222'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/ymfpci'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci/ymfpci'
make[2]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pci'
make[2]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa/codecs'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa/codecs'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa/core'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa/core'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa/fabrics'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa/fabrics'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa/soundbus'
make[4]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa/soundbus/i2sbus'
make[4]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa/soundbus/i2sbus'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa/soundbus'
make[2]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/aoa'
make[2]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/usb'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/usb/usx2y'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/usb/usx2y'
make[2]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/usb'
make[2]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pcmcia'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/pcmcia/vx'
make[3]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pcmcia/vx'
make[2]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/pcmcia'
make[1]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13'
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/home/dan/src/alsa/alsa-driver-1.0.13  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/dan/src/alsa/alsa-driver-1.0.13/acore/memalloc.o
In file included from /home/dan/src/alsa/alsa-driver-1.0.13/acore/memalloc.c:1:
/home/dan/src/alsa/alsa-driver-1.0.13/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /home/dan/src/alsa/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /home/dan/src/alsa/alsa-driver-1.0.13/acore/memalloc.c:1:
/home/dan/src/alsa/alsa-driver-1.0.13/include/adriver.h:742: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/home/dan/src/alsa/alsa-driver-1.0.13/include/adriver.h:761: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /home/dan/src/alsa/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /home/dan/src/alsa/alsa-driver-1.0.13/acore/memalloc.c:1:
/home/dan/src/alsa/alsa-driver-1.0.13/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/home/dan/src/alsa/alsa-driver-1.0.13/include/adriver.h:1099: error: too many arguments to function ‘pci_save_state’
/home/dan/src/alsa/alsa-driver-1.0.13/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/home/dan/src/alsa/alsa-driver-1.0.13/include/adriver.h:1103: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/home/dan/src/alsa/alsa-driver-1.0.13/acore/memalloc.o] Error 1
make[2]: *** [/home/dan/src/alsa/alsa-driver-1.0.13/acore] Error 2
make[1]: *** [_module_/home/dan/src/alsa/alsa-driver-1.0.13] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2
```

make install:
```
find /lib/modules/2.6.20-15-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
make[1]: Entering directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore'
mkdir -p /lib/modules/2.6.20-15-generic/kernel/sound/acore
cp snd-page-alloc.ko snd-pcm.ko snd-timer.ko snd.ko /lib/modules/2.6.20-15-generic/kernel/sound/acore
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/dan/src/alsa/alsa-driver-1.0.13/acore'
make: *** [install-modules] Error 1
```

If anybody can give me a hint as to what is going on, I would be grateful.

---

### Post by nullfactor on 2007-04-21
I repeated the steps on the comprehensive guide using the latest and greatest alsa releases.  The makes and make installs worked fine.  However, I am still without audio.  Following is some information that may be useful and relevant.  Any help anybody can provide would be awesome.  I'm attempting to ditch Windows... I can't ditch Windows if I don't have sound. ;)

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

lspci -v
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Aud
io Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 
Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (r
ev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 
Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown devic
e ff31
        Capabilities: [a0] Power Management version 2

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (r
ev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: 54000000-540fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 
Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown devic
e ff31
        Capabilities: [a0] Power Management version 2

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (r
ev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 
Enable-
        Capabilities: [90] Subsystem: Toshiba America Info Systems Unknown devic
e ff31
        Capabilities: [a0] Power Management version 2

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 
02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 
02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 
02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 
02) (prog-if 00 [UHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Control
ler (rev 02) (prog-if 20 [EHCI])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 
01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Capabilities: [50] Subsystem: Toshiba America Info Systems Unknown devic
e ff31

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (re
v 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA S
torage Controller IDE (rev 02) (prog-if 80 [Master])
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]
```

lspci -nv
```
00:1b.0 0403: 8086:27d8 (rev 02)
        Subsystem: 1179:ff31
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 
Enable-
        Capabilities: [70] Express Unknown type IRQ 0

00:1c.0 0604: 8086:27d0 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 
Enable-
        Capabilities: [90] Subsystem: 1179:ff31
        Capabilities: [a0] Power Management version 2

00:1c.1 0604: 8086:27d2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: 54000000-540fffff
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 
Enable-
        Capabilities: [90] Subsystem: 1179:ff31
        Capabilities: [a0] Power Management version 2

00:1c.2 0604: 8086:27d4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: [40] Express Root Port (Slot+) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 
Enable-
        Capabilities: [90] Subsystem: 1179:ff31
        Capabilities: [a0] Power Management version 2

00:1d.0 0c03: 8086:27c8 (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1179:ff31
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.1 0c03: 8086:27c9 (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1179:ff31
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1840 [size=32]

00:1d.2 0c03: 8086:27ca (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1179:ff31
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 1860 [size=32]

00:1d.3 0c03: 8086:27cb (rev 02) (prog-if 00 [UHCI])
        Subsystem: 1179:ff31
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 1880 [size=32]

00:1d.7 0c03: 8086:27cc (rev 02) (prog-if 20 [EHCI])
        Subsystem: 1179:ff31
        Flags: bus master, medium devsel, latency 0, IRQ 19
        Memory at d0544000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [50] Power Management version 2
        Capabilities: [58] Debug port

00:1e.0 0604: 8086:2448 (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=0a, subordinate=0e, sec-latency=32
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d0100000-d01fffff
        Prefetchable memory behind bridge: 0000000050000000-0000000053ffffff
        Capabilities: [50] Subsystem: 1179:ff31

00:1f.0 0601: 8086:27b9 (rev 02)
        Subsystem: 1179:ff31
        Flags: bus master, medium devsel, latency 0
        Capabilities: [e0] Vendor Specific Information

00:1f.2 0101: 8086:27c4 (rev 02) (prog-if 80 [Master])
        Subsystem: 1179:ff31
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 20
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 18b0 [size=16]
        Capabilities: [70] Power Management version 2

00:1f.3 0c05: 8086:27da (rev 02)
        Subsystem: 1179:ff31
        Flags: medium devsel, IRQ 11
        I/O ports at 18c0 [size=32]


```

sudo modprobe snd-hda-intel

```
Returns nothing
```

Hopefully, this is enough information to help you help me.  Thank you in advance.

---

### Post by fotzlapen on 2007-04-21
Heya Guys,

I've just spent the last 4 or 5 hours screwing around with the same sound card.  I managed to get it working properly about an hour ago.  I have it in an asus a8jr laptop that I bought a week or two ago.  If you've been googling like mad like I have you may have seen some of the following before, I was actually surprised when it worked for me.

My problem was that my sound would work until I tried to change the master volume control, then all my sound would die until I rebooted.  It also happened using the laptop's in built sound buttons.

To fix it I added this line to my /etc/modprobe.d/alsa-base file:
```

sudo nano /etc/modprobe.d/alsa-base

options snd-hda-intel position_fix=1 model=3stack
```

After this it still wasn't working and I found I also had to create a file /etc/modules.conf and add the same line to it:

```
sudo nano /etc/modprobe.d/alsa-base

options snd-hda-intel position_fix=1 model=3stack

```

Hope this may help.  But if you can't even load the module then you probably have bigger issues!  :)

Cheers!

Damo

---

### Post by nullfactor on 2007-04-21
Hi... thanks for the response.  I attempted to add that line into the files specified.  Unfortunately, still no sound.  Not even a peep.  I've ready some crazy stuff about the hda-intel piping sound through the microphone, so I attempted to plug in some headphones into the mic jack... hoping.  Unfortunately, nothing.

Any other ideas would be most appreciated!

---

### Post by tturrisi on 2007-04-21
In dapper there was a similar issue.
You had to use ESD or Alsa, but not both.
Thus, turn off ESD by going to Preferences>Sounds & disabble esd & system sounds, then multimedia audio works.

---

### Post by nullfactor on 2007-04-22
Hmmm... something tells me this hda-intel thing is going to be a pain in the keester.  I just disabled ESD and still no multimedia.  Interestingly enough, I did a test of the multimedia pipe and the test just sat there.  Even though I ran through the comprehensive guide, perhaps something isn't installed properly (or at all)???

---

### Post by mattgeldard on 2007-04-22
Same problem On my LG Laptop Running Intel Sound The progress bar never finishes have you tryed plugging in Headphones as this gives me sound not ideal i no but a quick fix but not sure what to do next to get  sound from speakers

---

### Post by nullfactor on 2007-04-22
MATT - Yeah... I tried plugging headphones into the line out jack, as well as line-in and microphone jacks.  I've heard hda-intel tends to send sound through some pretty unpredictable routes, so... I thought I'd give it a shot. :)

If you figure out how to get Intel to work properly, could you please post it, here.  I'll do the same if I stumble upon a fix.

Thanks!

---

### Post by tturrisi on 2007-04-22
do:
lsmod | grep snd
cat /proc/asound/oss/sndstat
and eventually
alsaconf

make sure sound is not muted in any config anywhere (alsa mixer).

lspci | grep audio
lsmod | grep snd
If nothing shows up on the lspci query, you have hardware problems. If nothing shows up on the lsmod query, you have driver problems.

---

### Post by nullfactor on 2007-04-22
TTURRISI -

lsmod |grep snd:
```

snd_hda_intel          21912  1 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  12 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm
```

cat /proc/asound/oss/sndstat:
```
Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux dan-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xd0340000 irq 22

Audio devices:
0: CONEXANT Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Conexant CX20549 (Venice)
```

lsmod brought up some stuff, so driver seems cool.

lspci brought up nothing.  This sound card works in Windows, so I know the hardware, itself is alright.  Something must have broke in the Linux install.  Any suggestions on how to fix the broken lspci?

I'm bound to learn something, yet!!! :)

---

### Post by mattgeldard on 2007-04-23
I Get the same results when i cat /proc/asound/oss/sndstat

Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux matt-laptop 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xb0000000 irq 18

Audio devices:
0: CMI9880 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: C-Media CMI9880

but no closer to a fix

---

### Post by nullfactor on 2007-04-23
Same here.  I see that this bug has been reported a number of times and that there are several potential solutions.  So far, none of them have worked for me.  So... if anybody has some ideas... :)

---

### Post by nullfactor on 2007-04-23
UPDATE -  Out of curiosity, I typed:
```
/etc/init.d/alsasound status
```
and was told that alsa drivers were not installed.  Hmmm.  So I installed them.  Now, it says that alsa-drivers ARE installed... but still no sound.  

Also, I still have nothing when I type:
```
lspci |grep snd
```

Anybody have any idears on this?

Thanks.

---

### Post by nullfactor on 2007-04-23
Okay... dumb questions:

I have a folder called /etc/group.  In which, there is a line:  audio : x : 29 : dan

I also have a folder called /etc/group-.  In which, there is the same line:  audio : x : 29 : dan

What exactly is the /etc/group- folder?

---

### Post by arrizaba on 2007-04-24
I have exactly the same problem and I am happy to have found this forum.
What puzzles me is that I get sound in the GDM screen, but no sound in the desktop. Does anyone experience the same?

---

### Post by nullfactor on 2007-04-24
ARRIZABA - You're better off than me, then.  I do not get sound anywhere.  Since I do not have anything listed in my lspci |grep snd, it's been said that it's a hardware issue.  I've verified that the hardware works under Windoze, so the hardware is physically fine.  

If you find any solution to the problem, please feel free to post it here.  It would help tremendously.

---

### Post by nullfactor on 2007-04-25
Man... how hard could it be to get something as basic as sound going?  I've found a ton of resources on the web, each with some pretty good ideas.  None of them are working.

I'm open for ANY suggestions that might get my audio working.  Certainly there's something I can do, right?

I'm desperate.  Please help me clutch as straws (or better yet, if anybody knows a sure-fire fix, that would be cool, too).

Thanks, everybody!

---

### Post by zielak on 2007-04-25
> **arrizaba said:**
> What puzzles me is that I get sound in the GDM screen, but no sound in the desktop.

Maybe the user You are logging in isn't allowed to use audio devices? Check user properties in System->Administration->Users & Groups

---

### Post by angrylittleman on 2007-04-25
I am in the same boat as everyone else in this thread.  While it is not a deal breaker, it is pretty frustrating.  I really like to work and listen to music at the same time.  I have tried the fixes in this thread and I am still without sound.  If someone has any other ideas, I am all for making this work.  Other than sound, Feisty is great!

---

### Post by arrizaba on 2007-04-25
> **zielak said:**
> Maybe the user You are logging in isn't allowed to use audio devices? Check user properties in System->Administration->Users & Groups

Yes, it seems my problem was this. After I changed the permissions the sound worked again. However, I applied many of the advices on this and other forums, so I may have fixed both hardware and permissions problems.
Thanx!

---

### Post by nullfactor on 2007-04-25
What I would like to know is... when I do a lspci |grep snd, I do not get anything in return.  I hear this means my hardware is not working.  It DOES work in Windows, so I know that the hardware is fine.  Any thoughts?

---

### Post by nullfactor on 2007-04-25
Don't know if this will help anybody help me, but here is the output of dmesg:

```
[    0.000000] Linux version 2.6.20-15-generic (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:36:31 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000dc000 size: 0000000000008000 end: 00000000000e4000 type: 2
[    0.000000] copy_e820_map() start: 00000000000e8000 size: 0000000000018000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f590000 end: 000000003f690000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f690000 size: 000000000000c000 end: 000000003f69c000 type: 3
[    0.000000] copy_e820_map() start: 000000003f69c000 size: 0000000000064000 end: 000000003f700000 type: 4
[    0.000000] copy_e820_map() start: 000000003f700000 size: 0000000000900000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010000000 end: 00000000f0000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000010000 end: 00000000fec10000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed00000 size: 0000000000000400 end: 00000000fed00400 type: 2
[    0.000000] copy_e820_map() start: 00000000fed14000 size: 0000000000006000 end: 00000000fed1a000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed1c000 size: 0000000000074000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f690000 (usable)
[    0.000000]  BIOS-e820: 000000003f690000 - 000000003f69c000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f69c000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f7690
[    0.000000] Entering add_active_range(0, 0, 259728) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259728
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259728
[    0.000000] On node 0 totalpages: 259728
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30115 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v002 TOSQCI                                ) @ 0x000f75d0
[    0.000000] ACPI: XSDT (v001 TOSQCI TOSQCI00 0x06040000  LTP 0x00000000) @ 0x3f692072
[    0.000000] ACPI: FADT (v003 TOSQCI TOSQCI00 0x06040000 ALAN 0x00000001) @ 0x3f69bc2a
[    0.000000] ACPI: MADT (v001 TOSQCI TOSQCI00 0x06040000 LOHR 0x0000005a) @ 0x3f69bd1e
[    0.000000] ACPI: HPET (v001 TOSQCI TOSQCI00 0x06040000 LOHR 0x0000005a) @ 0x3f69bd86
[    0.000000] ACPI: MCFG (v001 TOSQCI TOSQCI00 0x06040000 LOHR 0x0000005a) @ 0x3f69bdbe
[    0.000000] ACPI: MADT (v001 PTLTD  	 APIC   0x06040000  LTP 0x00000000) @ 0x3f69bdfa
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3f69be62
[    0.000000] ACPI: SLIC (v001 TOSQCI TOSQCI00 0x06040000  LTP 0x00000000) @ 0x3f69be8a
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Tst 0x00003000 INTL 0x20060912) @ 0x3f692672
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu1Tst 0x00003000 INTL 0x20060912) @ 0x3f6925cc
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20060912) @ 0x3f6920e6
[    0.000000] ACPI: DSDT (v001 TOSQCI   Denver 0x06040000 MSFT 0x03000001) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: 2 duplicate APIC table ignored.
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 20
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1600.229 MHz processor.
[   16.362981] Built 1 zonelists.  Total pages: 257699
[   16.362985] Kernel command line: root=UUID=03ec3b18-ce61-49e1-98f8-3f904879ebec ro quiet splash
[   16.363152] mapped APIC to ffffd000 (fee00000)
[   16.363155] mapped IOAPIC to ffffc000 (fec00000)
[   16.363158] Enabling fast FPU save and restore... done.
[   16.363161] Enabling unmasked SIMD FPU exception support... done.
[   16.363169] Initializing CPU#0
[   16.363244] PID hash table entries: 4096 (order: 12, 16384 bytes)
[   16.365101] Console: colour VGA+ 80x25
[   16.365390] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   16.365789] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   16.397390] Memory: 1018484k/1038912k available (1992k kernel code, 19644k reserved, 893k data, 328k init, 121408k highmem)
[   16.397400] virtual kernel memory layout:
[   16.397401]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   16.397403]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   16.397404]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   16.397406]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   16.397407]       .init : 0xc03d7000 - 0xc0429000   ( 328 kB)
[   16.397408]       .data : 0xc02f2264 - 0xc03d16d4   ( 893 kB)
[   16.397410]       .text : 0xc0100000 - 0xc02f2264   (1992 kB)
[   16.397413] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   16.397590] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.397597] hpet0: 3 64-bit timers, 14318180 Hz
[   16.398602] Using HPET for base-timer
[   16.477471] Calibrating delay using timer specific routine.. 3203.74 BogoMIPS (lpj=6407493)
[   16.477515] Security Framework v1.0.0 initialized
[   16.477523] SELinux:  Disabled at boot.
[   16.477540] Mount-cache hash table entries: 512
[   16.477687] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[   16.477696] monitor/mwait feature present.
[   16.477698] using mwait in idle threads.
[   16.477702] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.477705] CPU: L2 cache: 1024K
[   16.477708] CPU: Physical Processor ID: 0
[   16.477710] CPU: Processor Core ID: 0
[   16.477712] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[   16.477722] Compat vDSO mapped to ffffe000.
[   16.477727] Remapping vsyscall page to ffffe000
[   16.477740] Checking 'hlt' instruction... OK.
[   16.493569] SMP alternatives: switching to UP code
[   16.493970] Early unpacking initramfs... done
[   16.853253] ACPI: Core revision 20060707
[   16.879039] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   16.896081] CPU0: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[   16.896104] SMP alternatives: switching to SMP code
[   16.896239] Booting processor 1/1 eip 3000
[   16.906542] Initializing CPU#1
[   16.984696] Calibrating delay using timer specific routine.. 3200.21 BogoMIPS (lpj=6400422)
[   16.984705] CPU: After generic identify, caps: bfe9fbff 00000000 00000000 00000000 0000c189 00000000 00000000
[   16.984710] monitor/mwait feature present.
[   16.984714] CPU: L1 I cache: 32K, L1 D cache: 32K
[   16.984716] CPU: L2 cache: 1024K
[   16.984719] CPU: Physical Processor ID: 0
[   16.984720] CPU: Processor Core ID: 1
[   16.984722] CPU: After all inits, caps: bfe9fbff 00000000 00000000 00002940 0000c189 00000000 00000000
[   16.985096] CPU1: Intel Genuine Intel(R) CPU           T2060  @ 1.60GHz stepping 0c
[   16.985122] Total of 2 processors activated (6403.95 BogoMIPS).
[   16.985322] ENABLING IO-APIC IRQs
[   16.985534] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   17.132473] checking TSC synchronization across 2 CPUs: passed.
[    0.003994] Brought up 2 CPUs
[    0.108507] migration_cost=77
[    0.108809] Booting paravirtualized kernel on bare hardware
[    0.108913] Time: 23:50:37  Date: 03/25/107
[    0.108943] NET: Registered protocol family 16
[    0.109039] EISA bus registered
[    0.109047] ACPI: bus type pci registered
[    0.134140] PCI: PCI BIOS revision 2.10 entry at 0xfd704, last bus=11
[    0.134143] PCI: Using configuration type 1
[    0.134145] Setting up standard PCI resources
[    0.141376] ACPI: Interpreter enabled
[    0.141380] ACPI: Using IOAPIC for interrupt routing
[    0.141887] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.141892] PCI: Probing PCI hardware (bus 00)
[    0.142731] Boot video device is 0000:00:02.0
[    0.143404] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    0.143409] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    0.144309] PCI: Firmware left 0000:0a:08.0 e100 interrupts enabled, disabling
[    0.144405] PCI: Transparent bridge - 0000:00:1e.0
[    0.144482] PCI: Bus #0b (-#0e) is hidden behind transparent bridge #0a (-#0b) (try 'pci=assign-busses')
[    0.144485] Please report the result to linux-kernel to fix this permanently
[    0.144553] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.156016] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.156302] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.156582] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    0.158063] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    0.158707] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.158990] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.159275] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.159555] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.159845] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.160124] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.160407] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.160691] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.234347] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.234358] pnp: PnP ACPI init
[    0.237141] pnp: PnP ACPI: found 9 devices
[    0.237145] PnPBIOS: Disabled by ACPI PNP
[    0.237193] PCI: Using ACPI for IRQ routing
[    0.237196] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    0.237201] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[    0.237203] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[    0.237206] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[    0.237209] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[    0.237211] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[    0.237214] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[    0.237216] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[    0.237219] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[    0.237221] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[    0.269967] NET: Registered protocol family 8
[    0.269969] NET: Registered protocol family 20
[    0.270558] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    0.270565] PCI: Bridge: 0000:00:1c.0
[    0.270566]   IO window: disabled.
[    0.270573]   MEM window: disabled.
[    0.270578]   PREFETCH window: disabled.
[    0.270593] PCI: Bridge: 0000:00:1c.1
[    0.270595]   IO window: disabled.
[    0.270601]   MEM window: 54000000-540fffff
[    0.270606]   PREFETCH window: disabled.
[    0.270612] PCI: Bridge: 0000:00:1c.2
[    0.270613]   IO window: disabled.
[    0.270619]   MEM window: disabled.
[    0.270623]   PREFETCH window: disabled.
[    0.270632] PCI: Bus 11, cardbus bridge: 0000:0a:04.0
[    0.270635]   IO window: 00002400-000024ff
[    0.270640]   IO window: 00002800-000028ff
[    0.270646]   PREFETCH window: 50000000-53ffffff
[    0.270652]   MEM window: 58000000-5bffffff
[    0.270657] PCI: Bridge: 0000:00:1e.0
[    0.270660]   IO window: 2000-2fff
[    0.270667]   MEM window: d0100000-d01fffff
[    0.270672]   PREFETCH window: 50000000-53ffffff
[    0.270706] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.270715] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    0.270738] PCI: Enabling device 0000:00:1c.1 (0000 -> 0002)
[    0.270744] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[    0.270751] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    0.270776] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[    0.270784] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    0.270796] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[    0.270803] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    0.270820] PCI: Enabling device 0000:0a:04.0 (0000 -> 0003)
[    0.270825] ACPI: PCI Interrupt 0000:0a:04.0[A] -> GSI 17 (level, low) -> IRQ 16
[    0.270834] PCI: Setting latency timer of device 0000:0a:04.0 to 64
[    0.270867] NET: Registered protocol family 2
[    0.323553] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.323676] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.324463] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.324880] TCP: Hash tables configured (established 131072 bind 65536)
[    0.324883] TCP reno registered
[    0.339621] checking if image is initramfs... it is
[    1.049874] Freeing initrd memory: 6993k freed
[    1.050066] Simple Boot Flag at 0x36 set to 0x1
[    1.050582] audit: initializing netlink socket (disabled)
[    1.050601] audit(1177545037.864:1): initialized
[    1.050707] highmem bounce pool size: 64 pages
[    1.050806] VFS: Disk quotas dquot_6.5.1
[    1.050829] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.050882] io scheduler noop registered
[    1.050885] io scheduler anticipatory registered
[    1.050888] io scheduler deadline registered
[    1.050900] io scheduler cfq registered (default)
[    9.042019] 0000:00:1d.7 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[    9.042309] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[    9.042372] assign_interrupt_mode Found MSI capability
[    9.042376] Allocate Port Service[0000:00:1c.0:pcie00]
[    9.042414] Allocate Port Service[0000:00:1c.0:pcie02]
[    9.042538] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[    9.042596] assign_interrupt_mode Found MSI capability
[    9.042599] Allocate Port Service[0000:00:1c.1:pcie00]
[    9.042630] Allocate Port Service[0000:00:1c.1:pcie02]
[    9.042754] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[    9.042812] assign_interrupt_mode Found MSI capability
[    9.042815] Allocate Port Service[0000:00:1c.2:pcie00]
[    9.042847] Allocate Port Service[0000:00:1c.2:pcie02]
[    9.043031] isapnp: Scanning for PnP cards...
[    9.396560] isapnp: No Plug & Play device found
[    9.424560] Real Time Clock Driver v1.12ac
[    9.424622] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.425398] mice: PS/2 mouse device common for all mice
[    9.426000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.426251] input: Macintosh mouse button emulation as /class/input/input0
[    9.426286] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.426290] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.426591] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.429590] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.429595] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.429737] EISA: Probing bus 0 at eisa.0
[    9.429745] Cannot allocate resource for EISA slot 1
[    9.429749] Cannot allocate resource for EISA slot 2
[    9.429777] EISA: Detected 0 cards.
[    9.459840] TCP cubic registered
[    9.459850] NET: Registered protocol family 1
[    9.459876] Starting balanced_irq
[    9.459883] Using IPI No-Shortcut mode
[    9.459994] ACPI: (supports S0 S3 S4 S5)
[    9.460044]   Magic number: 3:96:859
[    9.460148]   hash matches device ptyse
[    9.460348] Freeing unused kernel memory: 328k freed
[    9.461571] Time: tsc clocksource has been installed.
[    9.465414] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.690030] Capability LSM initialized
[   10.728650] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Ist] [20060707]
[   10.728937] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu0Cst] [20060707]
[   10.729598] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   10.730143] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Ist] [20060707]
[   10.730373] ACPI (exconfig-0455): Dynamic SSDT Load - OemId [ PmRef] OemTableId [ Cpu1Cst] [20060707]
[   10.731090] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   10.741811] ACPI: Thermal Zone [THRM] (46 C)
[   11.396000] Time: hpet clocksource has been installed.
[   11.808000] usbcore: registered new interface driver usbfs
[   11.808000] usbcore: registered new interface driver hub
[   11.808000] usbcore: registered new device driver usb
[   11.808000] USB Universal Host Controller Interface driver v3.0
[   11.808000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[   11.808000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.808000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.808000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.808000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[   11.808000] usb usb1: configuration #1 chosen from 1 choice
[   11.808000] hub 1-0:1.0: USB hub found
[   11.808000] hub 1-0:1.0: 2 ports detected
[   11.828000] SCSI subsystem initialized
[   11.832000] libata version 2.20 loaded.
[   11.896000] ieee1394: Initialized config rom entry `ip1394'
[   11.896000] e100: Intel(R) PRO/100 Network Driver, 3.5.17-k2-NAPI
[   11.896000] e100: Copyright(c) 1999-2006 Intel Corporation
[   11.912000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 20
[   11.912000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.912000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.916000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.916000] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00001840
[   11.916000] usb usb2: configuration #1 chosen from 1 choice
[   11.916000] hub 2-0:1.0: USB hub found
[   11.916000] hub 2-0:1.0: 2 ports detected
[   12.020000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   12.020000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   12.020000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   12.020000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   12.024000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[   12.024000] usb usb3: configuration #1 chosen from 1 choice
[   12.024000] hub 3-0:1.0: USB hub found
[   12.024000] hub 3-0:1.0: 2 ports detected
[   12.128000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 17
[   12.128000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   12.128000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   12.128000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   12.128000] uhci_hcd 0000:00:1d.3: irq 17, io base 0x00001880
[   12.132000] usb usb4: configuration #1 chosen from 1 choice
[   12.132000] hub 4-0:1.0: USB hub found
[   12.132000] hub 4-0:1.0: 2 ports detected
[   12.236000] ata_piix 0000:00:1f.2: version 2.10ac1
[   12.236000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   12.260000] usb 2-2: new low speed USB device using uhci_hcd and address 2
[   12.392000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[   12.392000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   12.392000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x000118b0 irq 14
[   12.392000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x000118b8 irq 15
[   12.392000] scsi0 : ata_piix
[   12.468000] usb 2-2: configuration #1 chosen from 1 choice
[   12.488000] usbcore: registered new interface driver hiddev
[   12.528000] input: HID 1241:1177 as /class/input/input2
[   12.528000] input: USB HID v1.10 Mouse [HID 1241:1177] on usb-0000:00:1d.1-2
[   12.528000] usbcore: registered new interface driver usbhid
[   12.528000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   12.564000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   12.564000] ata1.00: ATA-7: TOSHIBA MK1234GSX, AH001M, max UDMA/100
[   12.564000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   12.576000] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
[   12.576000] ata1.00: configured for UDMA/100
[   12.576000] scsi1 : ata_piix
[   12.900000] ata2.00: ATAPI, max UDMA/33
[   13.068000] ata2.00: configured for UDMA/33
[   13.068000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1234GS AH00 PQ: 0 ANSI: 5
[   13.068000] scsi 1:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.10 PQ: 0 ANSI: 5
[   13.068000] PCI: Enabling device 0000:0a:04.1 (0000 -> 0002)
[   13.068000] ACPI: PCI Interrupt 0000:0a:04.1[A] -> GSI 17 (level, low) -> IRQ 16
[   13.068000] PCI: Setting latency timer of device 0000:0a:04.1 to 64
[   13.072000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[   13.072000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   13.072000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   13.072000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   13.072000] ehci_hcd 0000:00:1d.7: debug port 1
[   13.072000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   13.072000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xd0544000
[   13.076000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   13.076000] usb usb5: configuration #1 chosen from 1 choice
[   13.076000] hub 5-0:1.0: USB hub found
[   13.076000] hub 5-0:1.0: 8 ports detected
[   13.120000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[d0103000-d01037ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   13.180000] ACPI: PCI Interrupt 0000:0a:08.0[A] -> GSI 20 (level, low) -> IRQ 21
[   13.180000] PCI: Setting latency timer of device 0000:0a:08.0 to 64
[   13.208000] e100: eth0: e100_probe: addr 0xd0102000, irq 21, MAC addr 00:16:36:DE:66:AA
[   13.232000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   13.232000] sda: Write Protect is off
[   13.232000] sda: Mode Sense: 00 3a 00 00
[   13.232000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.232000] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
[   13.232000] sda: Write Protect is off
[   13.232000] sda: Mode Sense: 00 3a 00 00
[   13.232000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   13.232000]  sda: sda1 sda2 < sda5 >
[   13.288000] sd 0:0:0:0: Attached scsi disk sda
[   13.292000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   13.292000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   13.300000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   13.300000] Uniform CD-ROM driver Revision: 3.20
[   13.300000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   13.364000] usb 2-2: USB disconnect, address 2
[   13.492000] Attempting manual resume
[   13.492000] swsusp: Resume From Partition 8:5
[   13.492000] PM: Checking swsusp image.
[   13.492000] PM: Resume from disk failed.
[   13.532000] kjournald starting.  Commit interval 5 seconds
[   13.532000] EXT3-fs: mounted filesystem with ordered data mode.
[   13.612000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[   13.820000] usb 2-2: configuration #1 chosen from 1 choice
[   13.868000] input: HID 1241:1177 as /class/input/input3
[   13.868000] input: USB HID v1.10 Mouse [HID 1241:1177] on usb-0000:00:1d.1-2
[   24.172000] iTCO_vendor_support: vendor-support=0
[   24.176000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   24.176000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   24.176000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   24.212000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   24.216000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.252000] Linux agpgart interface v0.102 (c) Dave Jones
[   24.252000] agpgart: Detected an Intel 945GM Chipset.
[   24.252000] agpgart: Detected 7932K stolen memory.
[   24.288000] agpgart: AGP aperture is 256M @ 0xc0000000
[   24.312000] NET: Registered protocol family 17
[   24.324000] intel_rng: FWH not detected
[   24.700000] Yenta: CardBus bridge found at 0000:0a:04.0 [1179:ff31]
[   24.700000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   24.700000] Yenta: Routing CardBus interrupts to PCI
[   24.700000] Yenta TI: socket 0000:0a:04.0, mfunc 0x01a21b22, devctl 0x66
[   24.800000] ath_hal: module license 'Proprietary' taints kernel.
[   24.800000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   24.888000] wlan: 0.8.4.2 (0.9.3)
[   24.928000] ath_pci: 0.9.4.5 (0.9.3)
[   24.936000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   24.936000] Socket status: 30000006
[   24.936000] Yenta: Raising subordinate bus# of parent bus (#0a) from #0b to #0e
[   24.936000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   24.936000] cs: IO port probe 0x2000-0x2fff: clean.
[   24.936000] pcmcia: parent PCI bridge Memory window: 0xd0100000 - 0xd01fffff
[   24.936000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   24.936000] PCI: Enabling device 0000:0a:04.2 (0000 -> 0002)
[   24.936000] ACPI: PCI Interrupt 0000:0a:04.2[A] -> GSI 17 (level, low) -> IRQ 16
[   24.936000] PCI: Setting latency timer of device 0000:0a:04.2 to 64
[   24.936000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[   24.936000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   24.936000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   25.224000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x25a0b1, caps: 0xa04713/0x0
[   25.224000] synaptics: Toshiba Satellite P105 detected, limiting rate to 40pps.
[   25.260000] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   25.456000] sdhci: Secure Digital Host Controller Interface driver
[   25.456000] sdhci: Copyright(c) Pierre Ossman
[   25.536000] ath_rate_sample: 1.2 (0.9.3)
[   25.536000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   25.536000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   25.536000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   25.536000] wifi0: mac 10.0 phy 6.1 radio 10.2
[   25.536000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   25.536000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   25.536000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   25.536000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   25.536000] wifi0: Use hw queue 8 for CAB traffic
[   25.536000] wifi0: Use hw queue 9 for beacons
[   25.584000] wifi0: Atheros 5424/2424: mem=0x54000000, irq=16
[   25.584000] sdhci: SDHCI controller found at 0000:0a:04.3 [104c:803c] (rev 0)
[   25.584000] PCI: Enabling device 0000:0a:04.3 (0000 -> 0002)
[   25.584000] ACPI: PCI Interrupt 0000:0a:04.3[A] -> GSI 17 (level, low) -> IRQ 16
[   25.584000] PCI: Setting latency timer of device 0000:0a:04.3 to 64
[   25.584000] mmc0: SDHCI at 0xd0103800 irq 16 DMA
[   25.956000] cs: IO port probe 0x100-0x3af: clean.
[   25.960000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   25.960000] cs: IO port probe 0x820-0x8ff: clean.
[   25.960000] cs: IO port probe 0xc00-0xcf7: clean.
[   25.960000] cs: IO port probe 0xa00-0xaff: clean.
[   26.276000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   26.276000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   26.636000] fuse init (API version 7.8)
[   26.720000] lp: driver loaded but no devices found
[   26.836000] Adding 3004112k swap on /dev/disk/by-uuid/477e2ad1-0d1d-4caf-a65a-a25524b62697.  Priority:-1 extents:1 across:3004112k
[   26.976000] EXT3 FS on sda1, internal journal
[   29.248000] NET: Registered protocol family 10
[   29.248000] lo: Disabled Privacy Extensions
[   29.248000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.372000] No dock devices found.
[   31.388000] input: Power Button (FF) as /class/input/input5
[   31.388000] ACPI: Power Button (FF) [PWRF]
[   31.388000] input: Lid Switch as /class/input/input6
[   31.388000] ACPI: Lid Switch [LID]
[   31.392000] input: Power Button (CM) as /class/input/input7
[   31.392000] ACPI: Power Button (CM) [PWRB]
[   31.444000] ACPI: AC Adapter [ACAD] (on-line)
[   31.464000] Using specific hotkey driver
[   31.552000] ibm_acpi: ec object not found
[   31.664000] ACPI: Battery Slot [BAT1] (battery present)
[   31.776000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   31.784000] pcc_acpi: loading...
[   31.804000] wmi_add device=c1992800
[   31.804000] calling WQBA
[   31.804000] wmi_add device=c1992400
[   31.804000] calling WQBA
[   38.484000] [drm] Initialized drm 1.1.0 20060810
[   38.484000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   38.488000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   39.176000] ppdev: user-space parallel port driver
[   39.764000] ath0: no IPv6 routers present
[   39.964000] apm: BIOS not found.
[   40.392000] Bluetooth: Core ver 2.11
[   40.396000] NET: Registered protocol family 31
[   40.396000] Bluetooth: HCI device and connection manager initialized
[   40.396000] Bluetooth: HCI socket layer initialized
[   40.500000] Bluetooth: L2CAP ver 2.8
[   40.500000] Bluetooth: L2CAP socket layer initialized
[   40.524000] Bluetooth: RFCOMM socket layer initialized
[   40.524000] Bluetooth: RFCOMM TTY layer initialized
[   40.524000] Bluetooth: RFCOMM ver 1.8
```

---

### Post by nullfactor on 2007-04-26
I have just done exhaustive research on the Internet.  What I have found is disheartening.  Basically, the answer I have received about my sound problem is that it is unable to be fixed at this time.  I have tried every /etc/modprobe.d/alsa-base, /etc/modprobe.d/sound, etc. change that I have found.  I have tried disabling certain other features in case it was interfering with the sound.  That didn't help.  

I have a hard time believing that this is unable to be fixed, but that seems to be the general opinion, out there.

If there are any fellow nay-sayers, come join me.  Hopefully, this laptop will soon have some sound.  Until then... :( :( :( :( :( :( :( :(

---

### Post by ysse on 2007-04-29
> **nullfactor said:**
> Man... how hard could it be to get something as basic as sound going?  I've found a ton of resources on the web, each with some pretty good ideas.  None of them are working.

I'm open for ANY suggestions that might get my audio working.  Certainly there's something I can do, right?

I'm desperate.  Please help me clutch as straws (or better yet, if anybody knows a sure-fire fix, that would be cool, too).

Thanks, everybody!

OK, nullfactor, it seems we have the same sound hardware, only thing is mine worked out of the box. Still have some recording issues, but playback is fine.

lspci -nn | grep Audio gives me
```
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)

```
Looks very similar.

This may sound harsh, but have you considered a clean install? It seems you're on Feisty Fawn, but in your first post you were trying to build alsa version 1.0.13, and Feisty comes with 1.0.14rc1. Some posts later you have 1.0.14rc1 again (probably you never got 1.0.13 installed). But I don't have any alsasound file in my /etc/init.d, only alsa-utils. So, something is definitely different there. 

I don't know about the "Comprehensive sound guide", but it may very well be out of date, and not immediately applicable to Ubuntu 7.04.

A good place to look is [http://www.alsa-project.org]("http://www.alsa-project.org"), the mailing list shows a bit of work going on with the Conexant drivers.

And things **have** been getting better. In Dapper and Edgy, support for this sound board was playback only, but now recording from the built-in mic actually is possible!

And, of course, after reinstalling alsa, all the volume sliders go down to zero, but you **have** checked that, right?

Cheers
/Anders

---

### Post by barthel on 2007-05-01
I have exactly the same audio chipset (82801G, ICH7 family, 8086:27d8, rev 02) and have no sound either.

This is a clean feisty install, and even though I just did a repository refresh, the latest alsa packages are 1.0.13-3-ubuntu1. Where are you finding 1.0.14-rc1 packages for ALSA? (My other system was a feisty upgrade from dapper and it also shows 1.0.13-3-ubutnu1 as the latest package, even though I have the medibuntu repositories enabled on that system.)

---

### Post by nullfactor on 2007-05-01
YSSE -  Yeah... I've tried (several) clean installs and meet with the same result.  Your settings may help me out, here.  I'm going to give them a try.  For now, in my quest to find a fix, I've managed to lose complete sight of my sound card (aplay -l shows that it can't find a sound device).  Oops. :P  

I'm going to attempt to go through the comprehensive guide to get my hardware back, then I'll try your settings.  Thanks for the pointers!  

Oh yeah... and I'm completely green with envy that yours worked out of the box.  That goes to show what kind of luck I have with these things! ;)

---

### Post by nullfactor on 2007-05-01
BARTHEL - Actually, I've graduated to the alsa-*-rc3 packages.  Still same results.  The good news is, I just installed Feisty on my desktop unit (HP) and everything worked great, first time.  Woo hoo! :guitar:

---

### Post by barthel on 2007-05-02
Good news--I've solved my sound problem without compiling the latest ALSA drivers. The problem was a buggy DSDT in my BIOS--but the fix is simple.

1. Go to [http://acpi.sourceforge.net]("http://acpi.sourceforge.net") and choose view under the DSDT item in the side bar.
2. Select your system model and BIOS version. (In my case, Toshiba Satellite P105-S9339, BIOS v3.30. I had previously verified that this was the latest BIOS at Toshiba's customer support site.)
3. Move the DL'd DSDT file to /etc/initramfs-tools/ and execute the following (substituting the correct DSDT filename, of course):
```
sudo gunzip Toshiba-Satellite_P105-S9339-3.3-custom.asl.gz
sudo ln -s Toshiba-Satellite_P105-S9339-3.3-custom.asl DSDT.aml
```
4. Make a backup of /boot/initrd.img-$(uname -r) 
5. Update initramfs like so:
```
sudo update-initramfs -u -k $(uname -r)
```
6. Reboot. And the sysop said "Let there be sound..." :guitar: 

No muss, no fuss, no mucking about with module configuration options. The only downside is that you'll need to perform steps 4-6 whenever the kernel is updated for feisty. (But it's a *lot* easier then recompiling the kernel from scratch!)

TTFN

Barthel

---

### Post by mostholy on 2007-05-02
Okay, this sounds promising (sorry for the pun), but what if your laptop model is not listed on the DSDT view page?  I've got a Toshiba Satellite A135-S4527, with the same lack of sound that dominates these discussion groups.  Feisty Fawn.

BTW this was one of the better threads for my situation (hardware match).

Cheers!

---

### Post by nullfactor on 2007-05-02
BARTHEL - This sounds like an amazingly plausible fix!!!  Unfortunately, I won't have the time to muck around with it for a few days (busy rest of the week coming up).  I can't wait to try it and *hopefully* get some sound running.

Thanks for the tips!!!

---

### Post by nullfactor on 2007-05-02
MOSTHOLY - Your model is remarkably close to mine (but not exact).  I am glad to hear that this thread has been interesting.  I post here for two reasons... 1 - to get help and 2 - if a solution is found, then I consider that my contribution to the community. :)  Hope we (meaning you) can find a solution to get that sound up and running!  Best to you.

---

### Post by nullfactor on 2007-05-03
BARTHEL - Just tried your suggestion... still no sound. :(  Thanks for the idea, though.  It was well worth a stab.

---

### Post by ronaldo1 on 2007-05-07
my laptop is not listed
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
on a Acer Aspire 9805WKHi (which has the worst keyboard in creation)
does not work
even if you turn the surround on
headphones work ok
but there are lots of crackles in any sound and its never loud enough
using Edgy Eft

i downloaded, compiled and installed the latest alsa drivers with all the modprobe modifications
still no dice

any help would be appreciated as i am trying to get this working in iraq my download rates are REAL slow
and windows sucks in a combat environment ;

---

### Post by Arry on 2007-05-08
I have the same problem as most of you, no sound what-so-ever. I was going to try theDSTD thing, but I'm not sure of the exact model, I know it's a toshiba satellite pro p100 - but I don't know specifically what it is. When I audit in windows it just tells me p100.

This is so frustrating, I really like ubuntu (I'm a linux noob, first isntall 3 days ago) but this sound thing is keeping me from using it as my main OS and really enjoying it. I've tried many many guides I found, re-intalled fiesty - but still no joy.

Anybody got a sure fire fix yet? Or at least tell me how to know what exact mosdel my computer is? Even the manual just says p100.

---

### Post by theooftheoretic on 2007-05-08
Hello, all. Audio is not working at all on a new laptop I was just given as a birthday gift. It is a Toshiba Satellite a135-S2386. It has a 

The volume control applet shows it to be muted, and I receive an error dialog when I attempt to adjust the volume saying an appropriate hardware device cannot be detected. When I open up the volume control window, there are no channel adjustment sliders and the title of the window says "
Volume Control: HDA ATI SB (Alsa Mixer)".

This laptop came with Windows Vista Home Basic edition, and sound worked perfectly fine under that.

I have attempted the "soundstartfix" hack from another post, as well as entering the lines "options snd-hda-intel model=3stack" or the variation  "options snd-hda-intel model=auto" in the /etc/modprobe.d/alsa-base file. Neither one have worked.

Here are some debug outputs.

adamtheo@laptop-satellite:~$ /etc/init.d/alsasound status
bash: /etc/init.d/alsasound: No such file or directory

I am in the 'audio' group according to '/etc/group', and also I am checked as being able to use audio devices under the 'User Priveledges' tab of the 'Users & Groups' administration center.
> 
audio:x:29:adamtheo
> 
adamtheo@laptop-satellite:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc SB450 HDA Audio (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01)
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

But nothing is returned using the below 'lspci' command filtered through grep:
> 
adamtheo@laptop-satellite:~$ lspci | grep audio

> 
adamtheo@laptop-satellite:~$ lsmod | grep snd
snd_hda_intel          21912  0 
snd_hda_codec         205440  1 snd_hda_intel
snd_pcm_oss            44544  0 
snd_mixer_oss          17408  1 snd_pcm_oss
snd_pcm                79876  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            32896  0 
snd_seq_midi            9600  0 
snd_rawmidi            25472  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                52592  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23684  2 snd_pcm,snd_seq
snd_seq_device          9100  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54020  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         10888  2 snd_hda_intel,snd_pcm

> adamtheo@laptop-satellite:~$ cat /proc/asound/oss/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux laptop-satellite 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA ATI SB at 0xc0500000 irq 19

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Generic 11c1 Si3054

> adamtheo@laptop-satellite:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by Arry on 2007-05-09
Apparently the lastest version of the alsa drivers in the cvs fixes these problems. I tried to get them and install them, but it was too advanced stuff for me, maybe some of you with the same problems could give it a shot?

---

### Post by nullfactor on 2007-05-09
I tried the latest ALSA drivers and still nothing.  As for your issue, theooftheoretic, you may want to do a complete clean install of the ALSA drivers.  Have you looked at the comprehensive sound troubleshooting guide on the ubuntu forums?  If not, do a search for "comprehensive audio" and you'll find it.

To be fair, I've tried the comprehensive audio troubleshooting guide and it didn't help me a bit.  Still no sound... Frustrating!!!

---

### Post by dermanus on 2007-05-09
My own experience is that if I recompile the ALSA drivers, I get sound working again, but only until I plug in my headphones.

Since I had a three year-old, and a penchant for loud music, I plug in my headphones often.

There's got to be an easier way.

---

### Post by penvzila on 2007-05-09
xxxx

not 20 mintues later, I install alsa rc4 and......

it freaking worked!

---

### Post by EndPerform on 2007-05-09
For you Toshiba guys, have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=349491](http://ubuntuforums.org/showthread.php?t=349491)

I followed the instructions and got things working on my P105-S6227.  It's an ACPI issue, not an ALSA issue.

---

### Post by theooftheoretic on 2007-05-09
nullfactor: Thanks, I just tried the comprehensive audio guide, but it also did not work for me. I received build errors when trying to compile the driver.

> 
make -C /usr/src/linux-headers-2.6.20-15-generic SUBDIRS=/home/adamtheo/alsa-driver-1.0.13  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/adamtheo/alsa-driver-1.0.13/acore/memalloc.o
In file included from /home/adamtheo/alsa-driver-1.0.13/acore/memalloc.c:1:
/home/adamtheo/alsa-driver-1.0.13/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /home/adamtheo/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /home/adamtheo/alsa-driver-1.0.13/acore/memalloc.c:1:
/home/adamtheo/alsa-driver-1.0.13/include/adriver.h:742: error: redefinition of &#8216;jiffies_to_msecs&#8217;
include/linux/jiffies.h:268: error: previous definition of &#8216;jiffies_to_msecs&#8217; was here
/home/adamtheo/alsa-driver-1.0.13/include/adriver.h:761: error: redefinition of &#8216;msecs_to_jiffies&#8217;
include/linux/jiffies.h:290: error: previous definition of &#8216;msecs_to_jiffies&#8217; was here
In file included from /home/adamtheo/alsa-driver-1.0.13/acore/memalloc.inc:13,
                 from /home/adamtheo/alsa-driver-1.0.13/acore/memalloc.c:1:
/home/adamtheo/alsa-driver-1.0.13/include/adriver.h: In function &#8216;snd_pci_orig_save_state&#8217;:
/home/adamtheo/alsa-driver-1.0.13/include/adriver.h:1099: error: too many arguments to function &#8216;pci_save_state&#8217;
/home/adamtheo/alsa-driver-1.0.13/include/adriver.h: In function &#8216;snd_pci_orig_restore_state&#8217;:
/home/adamtheo/alsa-driver-1.0.13/include/adriver.h:1103: error: too many arguments to function &#8216;pci_restore_state&#8217;
/home/adamtheo/alsa-driver-1.0.13/acore/memalloc.c: At top level:
/home/adamtheo/alsa-driver-1.0.13/acore/memalloc.c:750: fatal error: opening dependency file /home/adamtheo/alsa-driver-1.0.13/acore/.memalloc.o.d: Permission denied
compilation terminated.
make[3]: *** [/home/adamtheo/alsa-driver-1.0.13/acore/memalloc.o] Error 1
make[2]: *** [/home/adamtheo/alsa-driver-1.0.13/acore] Error 2
make[1]: *** [_module_/home/adamtheo/alsa-driver-1.0.13] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [compile] Error 2


> 
adamtheo@laptop-satellite:~/alsa-driver-1.0.13$ sudo ./configure --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=hda-intel
Password:
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /home/adamtheo/alsa-driver-1.0.13
checking cross compile... 
checking for directory with kernel source... /usr/src/linux-headers-2.6.20-15-generic
checking for directory with kernel build... 
checking for kernel linux/version.h... yes
checking for kernel linux/autoconf.h... yes
checking for kernel version... 2.6.20-15-generic
checking for GCC version... Kernel compiler: gcc 4.1.2 (Ubuntu 4.1.2-0ubuntu4) Used compiler: gcc (GCC) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)
checking for built-in ALSA... no
checking for existing ALSA module... yes
checking for Red Hat kernel... auto
checking for Red Hat kernel... no
checking for SUSE kernel... auto
checking for SUSE kernel... no
checking for CONFIG_EXPERIMENTAL... yes
checking to modify of kernel linux/kmod.h... no
checking for kernel linux/utsrelease.h... yes
checking for kernel linux/compiler.h... yes
checking for kernel linux/pm.h... yes
checking for kernel linux/spinlock.h... yes
checking for kernel linux/irq.h... yes
checking for kernel linux/threads.h... yes
checking for kernel linux/rwsem.h... yes
checking for kernel linux/gameport.h... yes
checking for kernel media/v4l2-dev.h... yes
checking for kernel linux/devfs_fs_kernel.h... no
Creating a dummy <linux/devfs_fs_kernel.h>...
checking for kernel linux/highmem.h... yes
checking for kernel linux/workqueue.h... yes
checking for kernel linux/dma-mapping.h... yes
checking for kernel asm/hw_irq.h... yes
checking for kernel linux/device.h... yes
checking for kernel linux/platform_device.h... yes
checking for kernel linux/jiffies.h... yes
checking for kernel linux/compat.h... yes
checking for kernel linux/adb.h... yes
checking for kernel linux/cuda.h... yes
checking for kernel linux/pmu.h... yes
checking for kernel linux/moduleparam.h... yes
checking for kernel linux/syscalls.h... yes
checking for kernel linux/firmware.h... yes
checking for kernel linux/err.h... yes
checking for kernel linux/bitmap.h... yes
checking for kernel linux/mutex.h... yes
checking for kernel module symbol versions... yes
checking for PCI support in kernel... yes
checking for I2C driver in kernel... module
checking for I2C_POWERMAC in kernel... unknown
checking for firmware loader... yes
checking for input subsystem in kernel... yes
checking for directory to store kernel modules... /lib/modules/2.6.20-15-generic/kernel/sound
checking for verbose procfs... on
checking for verbose printk... on
checking for debug level... none
checking for ISA support in kernel... yes
checking for processor type... i586
checking for i386 machine type... default
checking for ISA DMA API... yes
checking for SMP... yes
checking for Video device support in kernel... yes
checking for ISA PnP driver in kernel... yes
checking for PnP driver in kernel... yes
checking for Kernel ISA-PnP support... yes
checking for strlcpy... no
checking for snprintf... no
checking for vsnprintf... no
checking for scnprintf... no
checking for sscanf... no
checking for vmalloc_to_page... no
checking for old kmod... yes
checking for PDE... no
checking for pci_set_consistent_dma_mask... no
checking for pci_dev_present... no
checking for msleep... no
checking for msecs_to_jiffies... no
checking for tty->count is the atomic type... no
checking for video_get_drvdata... no
checking for V4L1 layer... yes
checking for io_remap_pfn_range... no
checking for new io_remap_page_range... no
checking for kcalloc... no
checking for kstrdup... no
checking for kzalloc... no
checking for create_workqueue with flags... no
checking for saved_config_space in pci_dev... no
checking for register_sound_special_device... no
checking for driver version... 1.0.13
checking for sequencer support... yes
checking for OSS/Free emulation... yes
checking for OSS PCM plugin system inclusion... yes
checking for RTC callback support in kernel... no
checking for HPET support... yes
checking for dynamic minor numbers... no
checking for support of old API... yes
checking for Procfs support... yes
checking for USB support... yes
checking for class_simple... no
checking for old driver suspend/resume callbacks... no
checking for removal of page-reservation for nopage/mmap... no
checking for nested class_device... no
checking for PnP suspend/resume... no
checking for new unlocked/compat_ioctl... no
checking for PC-Speaker hook... no
checking for kernel PCMCIA
checking for PCMCIA support... yes
checking for PC9800 support in kernel... no
checking for parallel port support... yes
checking for power management... yes
checking for which soundcards to compile driver for... hda-intel
configure: creating ./config.status
config.status: creating version
config.status: creating Makefile.conf
config.status: creating snddevices
config.status: creating utils/alsa-driver.spec
config.status: creating utils/buildrpm
config.status: creating toplevel.config
config.status: creating utils/alsasound
config.status: creating utils/alsasound.posix
config.status: creating include/pci_ids_compat.h
config.status: creating include/config.h
config.status: include/config.h is unchanged
config.status: creating include/config1.h
config.status: include/config1.h is unchanged
config.status: creating include/version.h
config.status: include/version.h is unchanged
config.status: creating include/autoconf-extra.h
config.status: include/autoconf-extra.h is unchanged
Hacking autoconf.h...


---

### Post by theooftheoretic on 2007-05-09
EndPerform: thanks, but it seems there is not a DSDT for my Toshiba laptop: a135-s2386. Oh, well  :(

---

### Post by nullfactor on 2007-05-10
MY SOUND WORKS!!!!!!!

Add acpi=off to your boot kernel.

The whole line will look similar to the following:
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sda5 ro quiet splash [COLOR="Blue"]acpi=off[/COLOR]

The change is in blue.

Good luck!!!

---

### Post by nullfactor on 2007-05-10
Sorry, more specifically, the file you want to edit is:

/boot/grub/menu.lst.

Do a search for "kernel" until you find the line that boots your favorite kernel.  Make the change listed above.  For me, that worked.  Hopefully it will for everybody else. ;)

---

### Post by nullfactor on 2007-05-12
As an addition to the fix listed above, make sure you have the latest and greatest alsa-driver release (I believe it's 1.0.14rc4).  I did a clean install after getting things to work (stupid of me) and sound did not work even after adding the apci=off line as stated above.  It seems to be a combination of the apci=off fix as well as requiring some new drivers from alsa.  Once those are put in place, the sound is amazing!

:guitar:

---

### Post by Jad on 2007-05-13
I have same problem and I have tried all suggested solution in forums/wiki/docs and google
now I feel like there is no solution for this problem , so lets pray! heh

[have a look at generated result by Alsa-info.sh script ]("http://syntux.net/sound.txt")

---

### Post by theooftheoretic on 2007-05-23
Just to let everyone know that I have solved my audio problems on my Toshiba Satellite a135-s2386 with an SB450

I made the following change after a fresh install (no other changes to the system made), as per a post I found somewhere in this site.

At the bottom of /etc/modules.d/alsa-base:
```

options snd-hda-intel probe_mask=8 model=3stack

```

Before this change, the output of "aplay -l" was this:
```
adamtheo@laptop-satellite:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

After a couple of reboots, the output now reads:
```
adamtheo@laptop-a135:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So it seems the problem was that Linux was thinking my dial-up modem was the soundcard, and therefore couldn't use it to produce sound. It had to be told to ignore the modem and go on to another device (I'm guessing?). And although I had tried a similar fix that didn't work, the key part of this fix seemed to be the "probe_mask=8" part of the alsa-base line.

Now sound works perfectly, although perhaps a little low (in Vista the sound was excellent, even the volume at 20% was enough to clearly hear from the next room over, now I have to crank it up to 80%).

---

### Post by ronaldo1 on 2007-05-24
i downloaded make'd and installed rc 14
now my machine wont boot with the acpi=off
so i editid it back out and the sound is back to where it was
headphones only, staticy and low
but it "works"
if i could only play sound out of my acer laptop speakers
sigh

---

### Post by Jad on 2007-05-24
I'm not fan of turning ACPI off with laptops.

---

