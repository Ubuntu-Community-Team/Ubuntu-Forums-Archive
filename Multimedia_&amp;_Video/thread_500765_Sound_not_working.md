---
title: "Sound not working"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by jasonlfunk on 2007-07-14
I cannot get my sound to work.

```
aplay -l
aplay: device_list:222: no soundcards found...

```

```
lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8371 [KX133] (rev 02)
        Flags: bus master, medium devsel, latency 0
        Memory at d8000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8371 [KX133 AGP] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: dc000000-ddffffff
        Prefetchable memory behind bridge: d0000000-d7ffffff
        Capabilities: <access denied>

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
        Subsystem: VIA Technologies, Inc. VT82C686/A PCI to ISA Bridge
        Flags: bus master, stepping, medium devsel, latency 0

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
        Flags: bus master, medium devsel, latency 32
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at d000 [size=16]
        Capabilities: <access denied>

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at d400 [size=32]
        Capabilities: <access denied>

00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10) (prog-if 00 [UHCI])
        Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
        Flags: bus master, medium devsel, latency 32, IRQ 5
        I/O ports at d800 [size=32]
        Capabilities: <access denied>

00:07.4 Host bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 30)
        Flags: medium devsel, IRQ 9
        Capabilities: <access denied>

00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
        Subsystem: VIA Technologies, Inc. Onboard Audio on EP7KXA
        Flags: medium devsel, IRQ 11
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=4]
        I/O ports at e400 [size=4]
        Capabilities: <access denied>

00:0a.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 02)
        Subsystem: Silicon Integrated Systems [SiS] SiS900 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 32, IRQ 11
        I/O ports at ec00 [size=256]
        Memory at df000000 (32-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at 10000000 [disabled] [size=128K]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX 100 DDR/200 DDR] (rev b2) (prog-if 00 [VGA])
        Subsystem: VISIONTEK Unknown device 002c
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 10
        Memory at dc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at dd000000 [disabled] [size=64K]
        Capabilities: <access denied>

```

I tired installing the drivers with apt-get. I also tried installing the drivers from source but I got an error in the make.
I configured with 
```

sudo ./configure  --with-kernel=/usr/src/linux-headers-$(uname -r) --with-cards=via82xx --with-oss=yes

```

```

jason@PC-3:~/src/alsa/alsa-driver-1.0.12$ sudo make
make dep
make[1]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12'
make[2]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore/ioctl32'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore/ioctl32'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore/oss'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore/oss'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore/seq'
make[4]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore/seq/instr'
make[4]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore/seq/instr'
make[4]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore/seq/oss'
make[4]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore/seq/oss'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore/seq'
make[2]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/acore'
make[2]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/i2c'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/i2c/other'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/i2c/other'
make[2]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/i2c'
make[2]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers/mpu401'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers/mpu401'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers/opl3'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers/opl3'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers/opl4'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers/opl4'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers/pcsp'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers/pcsp'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers/vx'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers/vx'
make[2]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/drivers'
make[2]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/ad1816a'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/ad1816a'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/ad1848'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/ad1848'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/cs423x'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/cs423x'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/es1688'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/es1688'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/gus'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/gus'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/msnd'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/msnd'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/opti9xx'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/opti9xx'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/sb'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/sb'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/wavefront'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa/wavefront'
make[2]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/isa'
make[2]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/synth'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/synth/emux'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/synth/emux'
make[2]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/synth'
make[2]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/ac97'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/ac97'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/ali5451'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/ali5451'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/asihpi'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/asihpi'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/au88x0'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/au88x0'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/ca0106'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/ca0106'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/cs46xx'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/cs46xx'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/cs5535audio'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/cs5535audio'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/echoaudio'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/echoaudio'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/emu10k1'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/emu10k1'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/hda'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/hda'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/ice1712'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/ice1712'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/korg1212'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/korg1212'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/mixart'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/mixart'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/nm256'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/nm256'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/pcxhr'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/pcxhr'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/pdplus'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/pdplus'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/riptide'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/riptide'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/rme9652'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/rme9652'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/trident'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/trident'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/vx222'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/vx222'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/ymfpci'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci/ymfpci'
make[2]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pci'
make[2]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/usb'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/usb/usx2y'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/usb/usx2y'
make[2]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/usb'
make[2]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pcmcia'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pcmcia/pdaudiocf'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pcmcia/pdaudiocf'
make[3]: Entering directory `/home/jason/src/alsa/alsa-driver-1.0.12/pcmcia/vx'
make[3]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pcmcia/vx'
make[2]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12/pcmcia'
make[1]: Leaving directory `/home/jason/src/alsa/alsa-driver-1.0.12'
make -C /usr/src/linux-headers-2.6.20-16-generic SUBDIRS=/home/jason/src/alsa/alsa-driver-1.0.12  CPP="gcc -E" CC="gcc" modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/jason/src/alsa/alsa-driver-1.0.12/acore/memalloc.o
In file included from /home/jason/src/alsa/alsa-driver-1.0.12/acore/memalloc.c:1:
/home/jason/src/alsa/alsa-driver-1.0.12/acore/memalloc.inc:1:26: error: linux/config.h: No such file or directory
In file included from /home/jason/src/alsa/alsa-driver-1.0.12/acore/memalloc.inc:13,
                 from /home/jason/src/alsa/alsa-driver-1.0.12/acore/memalloc.c:1:
/home/jason/src/alsa/alsa-driver-1.0.12/include/adriver.h:726: error: redefinition of ‘jiffies_to_msecs’
include/linux/jiffies.h:268: error: previous definition of ‘jiffies_to_msecs’ was here
/home/jason/src/alsa/alsa-driver-1.0.12/include/adriver.h:745: error: redefinition of ‘msecs_to_jiffies’
include/linux/jiffies.h:290: error: previous definition of ‘msecs_to_jiffies’ was here
In file included from /home/jason/src/alsa/alsa-driver-1.0.12/acore/memalloc.inc:13,
                 from /home/jason/src/alsa/alsa-driver-1.0.12/acore/memalloc.c:1:
/home/jason/src/alsa/alsa-driver-1.0.12/include/adriver.h: In function ‘snd_pci_orig_save_state’:
/home/jason/src/alsa/alsa-driver-1.0.12/include/adriver.h:1083: error: too many arguments to function ‘pci_save_state’
/home/jason/src/alsa/alsa-driver-1.0.12/include/adriver.h: In function ‘snd_pci_orig_restore_state’:
/home/jason/src/alsa/alsa-driver-1.0.12/include/adriver.h:1087: error: too many arguments to function ‘pci_restore_state’
make[3]: *** [/home/jason/src/alsa/alsa-driver-1.0.12/acore/memalloc.o] Error 1
make[2]: *** [/home/jason/src/alsa/alsa-driver-1.0.12/acore] Error 2
make[1]: *** [_module_/home/jason/src/alsa/alsa-driver-1.0.12] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [compile] Error 2

```

Ideas?

---

### Post by linuxwizard on 2007-07-14
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by jasonlfunk on 2007-07-14
> **linuxwizard said:**
> [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Yes Yes, I went through that and got to the part where it says:

*Failure - Start a new thread in this thread of the forum. Paste the error message that you get and state that you were following instructions on this page.

Guess I forgot to do that last part. :-)

---

### Post by hessiess on 2007-07-14
my sound dusent work eather, but it workes perfectily with the live cd, halp plz:)

need output of any commands?

heres the outpoot of the command in furst post of this thred

```
a@a-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
a@a-laptop:~$
```

```
a@a-laptop:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: d4000000-d5ffffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at d6400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
        I/O behind bridge: 00002000-00002fff
        Memory behind bridge: d2000000-d3ffffff
        Prefetchable memory behind bridge: 00000000d0000000-00000000d1ffffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Memory behind bridge: d6000000-d60fffff
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 20
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 1840 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 1860 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at d6404000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=08, subordinate=08, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: d6100000-d61fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at 1880 [size=16]

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 18c8 [size=8]
        I/O ports at 18ac [size=4]
        I/O ports at 18c0 [size=8]
        I/O ports at 18a8 [size=4]
        I/O ports at 18b0 [size=16]
        Memory at d6404400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: medium devsel, IRQ 10
        I/O ports at 18e0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7200 (rev a1) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at d5000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=128M]
        Memory at d4000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at c8000000 [disabled] [size=128K]
        Capabilities: <access denied>

05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 135c
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at d6000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 66, IRQ 21
        Memory at d6100000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at d6101000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

08:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 32, IRQ 18
        Memory at d6101800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, medium devsel, latency 0, IRQ 10
        Memory at d6101c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: medium devsel, IRQ 10
        Memory at d6102000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: medium devsel, IRQ 10
        Memory at d6102400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

a@a-laptop:~$ 

```

---

