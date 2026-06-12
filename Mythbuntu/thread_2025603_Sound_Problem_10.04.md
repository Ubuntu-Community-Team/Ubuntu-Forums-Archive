---
title: "Sound Problem 10.04"
date: 2012-07-14
forum: Mythbuntu
---

### Post by Mad_Professor on 2012-07-14
I have my backend setup to power on from a Wake-on-Lan event. Which is great and I have cron power down the machine in the hours I don't use it.

Well everytime it boots up, I'll randomly get reversed audio, meaning tuner 1 audio is being heard on tuner 0 and sometimes tuner 1 doesn't work because of that or no audio at all. Restarting several times to correct the issue fixes it for the time being.

I already have the sound device index order setup in alsa-base.conf and it boots correctly every time and yet my audio is reversing sources on the tuners or not working. I don't know if this a mythtv problem, configuration issue or a hardware problem.

```

pvr@pvr1:~$ cat /proc/asound/modules
 0 snd_emu10k1
 1 saa7134_alsa

```

```

pvr@pvr1:~$ cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - SB Audigy 2 Value [SB0400]
                      SB Audigy 2 Value [SB0400] (rev.0, serial:0x10011102) at 0xd400, irq 19
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xee001000 irq 17

```alsa-base.conf
```

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
#options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

# Sound Card order
options  snd_emu10k1 index=0
options  saa7134_alsa index=1

``````

 lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
        Subsystem: Giga-byte Technology Device 5000
        Flags: bus master, 66MHz, medium devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-via
        Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e8000000-eaffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Et                                                                             hernet (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at d000 [size=256]
        Memory at ee000000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 60000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

00:0b.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Device 1001
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at d400 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: EMU10K1_Audigy
        Kernel modules: snd-emu10k1

00:0c.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Vi                                                                             deo and Audio Decoder (rev 05)
        Subsystem: ASUSTeK Computer Inc. Device 4823
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
        Kernel driver in use: cx8800
        Kernel modules: cx8800

00:0c.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video an                                                                             d Audio Decoder [MPEG Port] (rev 05)
        Subsystem: ASUSTeK Computer Inc. Device 4823
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at ed000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
        Kernel driver in use: cx88-mpeg driver manager
        Kernel modules: cx8802

00:0d.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Vi                                                                             deo Broadcast Decoder (rev 10)
        Subsystem: ASUSTeK Computer Inc. Device 4843
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at ee001000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: saa7134
        Kernel modules: saa7134

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                              (rev 80)
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at d800 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                              (rev 80)
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                              (rev 80)
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at e000 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20)
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at ee002000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: Giga-byte Technology Device 5001
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: i2c-viapro, via-ircc

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/                                                                             C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Device 5002
        Flags: bus master, medium devsel, latency 32, IRQ 20
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at e400 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: pata_via
        Kernel modules: pata_via

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev                                                                              a2)
        Subsystem: eVga.com. Corp. Device a506
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-173, nvidia-current, nvidia-96, nvidiafb, nouveau


```I couldn't get the audio to work on the Conexant so I passed the audio via a cable to the audigy2 "aux" in pins.

The setup works great except for the audio problem.
What would cause the audio sources to randomly reverse or stop working on boot and reboots?

---

### Post by nickrout on 2012-07-15
> **Mad_Professor said:**
> I have my backend setup to power on from a Wake-on-Lan event. Which is great and I have cron power down the machine in the hours I don't use it.

Well everytime it boots up, I'll randomly get reversed audio, meaning tuner 1 audio is being heard on tuner 0 and sometimes tuner 1 doesn't work because of that or no audio at all. Restarting several times to correct the issue fixes it for the time being.

I already have the sound device index order setup in alsa-base.conf and it boots correctly every time and yet my audio is reversing sources on the tuners or not working. I don't know if this a mythtv problem, configuration issue or a hardware problem.

```

pvr@pvr1:~$ cat /proc/asound/modules
 0 snd_emu10k1
 1 saa7134_alsa

```

```

pvr@pvr1:~$ cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - SB Audigy 2 Value [SB0400]
                      SB Audigy 2 Value [SB0400] (rev.0, serial:0x10011102) at 0xd400, irq 19
 1 [SAA7134        ]: SAA7134 - SAA7134
                      saa7133[0] at 0xee001000 irq 17

```alsa-base.conf
```

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
#options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

# Sound Card order
options  snd_emu10k1 index=0
options  saa7134_alsa index=1

``````

 lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
        Subsystem: Giga-byte Technology Device 5000
        Flags: bus master, 66MHz, medium devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-via
        Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: e8000000-eaffffff
        Prefetchable memory behind bridge: d0000000-dfffffff
        Capabilities: <access denied>
        Kernel modules: shpchp

00:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Et                                                                             hernet (rev 10)
        Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at d000 [size=256]
        Memory at ee000000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 60000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: r8169
        Kernel modules: r8169

00:0b.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Device 1001
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at d400 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: EMU10K1_Audigy
        Kernel modules: snd-emu10k1

00:0c.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Vi                                                                             deo and Audio Decoder (rev 05)
        Subsystem: ASUSTeK Computer Inc. Device 4823
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at ec000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
        Kernel driver in use: cx8800
        Kernel modules: cx8800

00:0c.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video an                                                                             d Audio Decoder [MPEG Port] (rev 05)
        Subsystem: ASUSTeK Computer Inc. Device 4823
        Flags: bus master, medium devsel, latency 32, IRQ 16
        Memory at ed000000 (32-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>
        Kernel driver in use: cx88-mpeg driver manager
        Kernel modules: cx8802

00:0d.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Vi                                                                             deo Broadcast Decoder (rev 10)
        Subsystem: ASUSTeK Computer Inc. Device 4843
        Flags: bus master, medium devsel, latency 32, IRQ 17
        Memory at ee001000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
        Kernel driver in use: saa7134
        Kernel modules: saa7134

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                              (rev 80)
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at d800 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                              (rev 80)
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at dc00 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller                                                                              (rev 80)
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 32, IRQ 21
        I/O ports at e000 [size=32]
        Capabilities: <access denied>
        Kernel driver in use: uhci_hcd

00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82) (prog-if 20)
        Subsystem: Giga-byte Technology Device 5004
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at ee002000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
        Subsystem: Giga-byte Technology Device 5001
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>
        Kernel modules: i2c-viapro, via-ircc

00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/                                                                             C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology Device 5002
        Flags: bus master, medium devsel, latency 32, IRQ 20
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at e400 [size=16]
        Capabilities: <access denied>
        Kernel driver in use: pata_via
        Kernel modules: pata_via

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7800 GS] (rev                                                                              a2)
        Subsystem: eVga.com. Corp. Device a506
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 16
        Memory at e8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at e9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at ea000000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia-173, nvidia-current, nvidia-96, nvidiafb, nouveau


```I couldn't get the audio to work on the Conexant so I passed the audio via a cable to the audigy2 "aux" in pins.

The setup works great except for the audio problem.
What would cause the audio sources to randomly reverse or stop working on boot and reboots?

You need to set udev rules.

---

### Post by Mad_Professor on 2012-07-15
> **nickrout said:**
> You need to set udev rules.

Went right over my head.

Read up on it, I think I understand it, here is what I wrote but I want to make sure this is correct before I try it.

/etc/udev/rules.d/10-mythsound.rules
```

KERNEL=="card0", SUBSYSTEM=="sound", ATTRS{id}=="Audigy2", SYMLINK+="dsp"

KERNEL=="card1", SUBSYSTEM=="sound", ATTRS{id}=="SAA7134", SYMLINK+="dsp1"

```
```

pvr@pvr1:~$ udevadm info -a -p $(udevadm info -q path -n /dev/dsp)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:0b.0/sound/card0/dsp':
    KERNEL=="dsp"
    SUBSYSTEM=="sound"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:0b.0/sound/card0':
    KERNELS=="card0"
    SUBSYSTEMS=="sound"
    DRIVERS==""
    ATTRS{id}=="Audigy2"
    ATTRS{number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:0b.0':
    KERNELS=="0000:00:0b.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="EMU10K1_Audigy"
    ATTRS{vendor}=="0x1102"
    ATTRS{device}=="0x0008"
    ATTRS{subsystem_vendor}=="0x1102"
    ATTRS{subsystem_device}=="0x1001"
    ATTRS{class}=="0x040100"
    ATTRS{irq}=="19"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00001102d00000008sv00001102sd00001001bc04sc01i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

pvr@pvr1:~$ udevadm info -a -p $(udevadm info -q path -n /dev/dsp1)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:0d.0/sound/card1/dsp1':
    KERNEL=="dsp1"
    SUBSYSTEM=="sound"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:0d.0/sound/card1':
    KERNELS=="card1"
    SUBSYSTEMS=="sound"
    DRIVERS==""
    ATTRS{id}=="SAA7134"
    ATTRS{number}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:0d.0':
    KERNELS=="0000:00:0d.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="saa7134"
    ATTRS{vendor}=="0x1131"
    ATTRS{device}=="0x7133"
    ATTRS{subsystem_vendor}=="0x1043"
    ATTRS{subsystem_device}=="0x4843"
    ATTRS{class}=="0x048000"
    ATTRS{irq}=="17"
    ATTRS{local_cpus}=="ff"
    ATTRS{local_cpulist}=="0-7"
    ATTRS{modalias}=="pci:v00001131d00007133sv00001043sd00004843bc04sc80i00"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""

```

---

### Post by Mad_Professor on 2012-07-17
bump

---

### Post by Mad_Professor on 2012-07-22
udev rules aren't working, I can't find anything on setting up audio devices.

Can anyone help me?

---

### Post by faginbagin on 2012-07-26
I think you didn't quite get how udev rules work. The rules you've written are trying to create symlinks to device names that the drivers will create automatically. And those rules assume that the audigy is always card0 and the SAA7134 is always card1. But that can change each time you reboot. Plus, you should not be trying to create symlinks to the same device names created by the kernel drivers, namely /dev/dsp and /dev/dsp1. Leave those alone and use udev rules to create a new /dev entry.

I think something like this should work:
```
KERNEL=="card[0-9]", SUBSYSTEM=="sound", ATTRS{id}=="Audigy2", SYMLINK+="dsp-audigy"
```
This should create /dev/dsp-audigy. You don't care what the name is of the SAA7134 device, so you don't need a rule for it. Once you get the udev rule to create /dev/dsp-audigy, you'll need to go into mythtv-setup and change the name of the audio device for the tuner from /dev/dsp to /dev/dsp-audigy.

HTH,
Helen (who is not a udev expert)

---

