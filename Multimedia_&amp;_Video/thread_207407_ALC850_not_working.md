---
title: "ALC850 not working"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by c2483 on 2006-07-01
I know this has been posted before but I just can't make any sense out of it.
motherboard: ga-k8nxp-sli
sound: Realtek ALC850 (detected as CK804), I also have an X-Fi in my comp but that obviously doesn't work. 

I have tried muting and unmuting every channel in alsamixer doesn't help, however now wherever there is supposed to be a sound, I hear a click or popping noise.

I am using ubuntu 6.06 64-bit; I had the same problem with 32-bit.

Is this just a problem with 6.06?  Anything I can do?

---

### Post by LordRaiden on 2006-07-02
Have read of my guide in my signature. Go through the steps until it works (then hurray) or post back if you hit a roadblock.

---

### Post by c2483 on 2006-07-02
```

charles@charles-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

charles@charles-desktop:~$ lspci -v
0000:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
        Subsystem: Giga-byte Technology: Unknown device 5000
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <available only to root>

0000:00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0

0000:00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
        Subsystem: Giga-byte Technology: Unknown device 0c11
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at e000 [size=32]
        I/O ports at 1c00 [size=64]
        I/O ports at 1c40 [size=64]
        Capabilities: <available only to root>

0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 50
        Memory at fd001000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology: Unknown device 5004
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 233
        Memory at feb00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <available only to root>

0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: Giga-byte Technology: Unknown device ae01
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at b000 [size=256]
        I/O ports at b400 [size=256]
        Memory at fd004000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology: Unknown device 5002
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at f000 [size=16]
        Capabilities: <available only to root>

0000:00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology: Unknown device b003
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at c800 [size=16]
        Memory at fd005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
        Subsystem: Giga-byte Technology: Unknown device b003
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 225
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at dc00 [size=16]
        Memory at fd000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <available only to root>

0000:00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 00008000-00008fff
        Memory behind bridge: f0000000-f7ffffff

0000:00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
        Subsystem: Giga-byte Technology: Unknown device e000
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        Memory at fd002000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at e400 [size=8]
        Capabilities: <available only to root>

0000:00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: fb000000-fcffffff
        Prefetchable memory behind bridge: 0000000088000000-0000000088000000
        Capabilities: <available only to root>

0000:00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00006000-00006fff
        Capabilities: <available only to root>

0000:00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        I/O behind bridge: 00007000-00007fff
        Capabilities: <available only to root>

0000:00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: f8000000-faffffff
        Prefetchable memory behind bridge: 00000000e0000000-00000000eff00000
        Capabilities: <available only to root>

0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <available only to root>

0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

0000:01:07.0 Multimedia audio controller: Creative Labs: Unknown device 0005
        Subsystem: Creative Labs: Unknown device 0021
        Flags: bus master, medium devsel, latency 32, IRQ 12
        I/O ports at 8000 [size=32]
        Memory at f4000000 (64-bit, non-prefetchable) [size=2M]
        Memory at f0000000 (64-bit, non-prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01) (prog-if 10 [OHCI])
        Subsystem: Giga-byte Technology: Unknown device 1000
        Flags: bus master, medium devsel, latency 32, IRQ 58
        Memory at f4204000 (32-bit, non-prefetchable) [size=2K]
        Memory at f4200000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 19)
        Subsystem: Giga-byte Technology Marvell 88E8053 Gigabit Ethernet Controller (Gigabyte)
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at fc000000 (64-bit, non-prefetchable) [size=16K]
        I/O ports at 9000 [size=256]
        Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <available only to root>

0000:05:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0391 (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp.: Unknown device c553
        Flags: bus master, fast devsel, latency 0, IRQ 58
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (64-bit, prefetchable) [size=256M]
        Memory at f9000000 (64-bit, non-prefetchable) [size=16M]
        I/O ports at a000 [size=128]
        Expansion ROM at fa000000 [disabled] [size=128K]
        Capabilities: <available only to root>

```

```

charles@charles-desktop:~$ sudo modprobe snd-
snd-ac97-bus        snd-es1938          snd-rme9652
snd-ac97-codec      snd-es1968          snd-rtctimer
snd-ad1889          snd-fm801           snd-sb-common
snd-ainstr-fm       snd-hda-codec       snd-seq
snd-ainstr-simple   snd-hda-intel       snd-seq-device
snd-ak4114          snd-hdsp            snd-seq-dummy
snd-ak4117          snd-hdspm           snd-seq-instr
snd-ak4531-codec    snd-hwdep           snd-seq-midi
snd-ak4xxx-adda     snd-i2c             snd-seq-midi-emul
snd-ali5451         snd-ice1712         snd-seq-midi-event
snd-als4000         snd-ice1724         snd-seq-oss
snd-atiixp          snd-ice17xx-ak4xxx  snd-seq-virmidi
snd-atiixp-modem    snd-intel8x0        snd-serial-u16550
snd-au8810          snd-intel8x0m       snd-sonicvibes
snd-au8820          snd-korg1212        snd-tea575x-tuner
snd-au8830          snd-maestro3        snd-timer
snd-azt3328         snd-mixart          snd-trident
snd-bt87x           snd-mixer-oss       snd-trident-synth
snd-bt-sco          snd-mpu401          snd-usb-audio
snd-ca0106          snd-mpu401-uart     snd-usb-lib
snd-cmipci          snd-mtpav           snd-usb-usx2y
snd-cs4281          snd-nm256           snd-util-mem
snd-cs46xx          snd-opl3-lib        snd-via82xx
charles@charles-desktop:~$ sudo modprobe snd-intel8x0
Password:

```

i didn't see realtek anything on the matrix, so i'm not sure i have the right driver but i thought people have got the alc850 working.

i verified it was connected correctly to my speakers and like i said, i get a click or pop when i try to play sound.

---

### Post by LordRaiden on 2006-07-02
I think you got the right driver, but you'll need to tinker around in alsamixer I think (muting/unmuting, changing volumes, make sure pcm is not muted and around 80).

---

