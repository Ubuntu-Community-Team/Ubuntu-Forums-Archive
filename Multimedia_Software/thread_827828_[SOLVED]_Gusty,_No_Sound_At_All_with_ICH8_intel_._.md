---
title: "[SOLVED] Gusty, No Sound At All with ICH8 intel . I need your help"
date: 2008-06-13
forum: Multimedia Software
---

### Post by ameyjah on 2008-06-13
I have Intel Corporation 82801H (ICH8 Family) HD Audio Controller sound card. And I don't know why there is no sound. I would be very happy if you help me.

Here is my lspci -v output:
```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: 90000000-91ffffff
        Prefetchable memory behind bridge: 0000000080000000-000000008fffffff
        Capabilities: <access denied>

00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 92225900 (64-bit, non-prefetchable) [size=16]
        Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 0001
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at 92200000 (32-bit, non-prefetchable) [size=128K]
        Memory at 92224000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 20c0 [size=32]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 20a0 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at 2080 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at 92225400 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 2113
        Flags: bus master, fast devsel, latency 0, IRQ 23
        Memory at 92220000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Capabilities: <access denied>

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        I/O behind bridge: 00001000-00001fff
        Memory behind bridge: 92100000-921fffff
        Capabilities: <access denied>

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
        Capabilities: <access denied>

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 22
        I/O ports at 2060 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at 2040 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 2020 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0, IRQ 22
        Memory at 92225000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=07, subordinate=07, sec-latency=32
        Memory behind bridge: 92000000-920fffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 2438 [size=8]
        I/O ports at 244c [size=4]
        I/O ports at 2430 [size=8]
        I/O ports at 2448 [size=4]
        I/O ports at 2410 [size=16]
        I/O ports at 2400 [size=16]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Intel Corporation Unknown device 514d
        Flags: medium devsel, IRQ 10
        Memory at 92225800 (32-bit, non-prefetchable) [size=256]
        I/O ports at 2000 [size=32]

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
        I/O ports at 2428 [size=8]
        I/O ports at 2444 [size=4]
        I/O ports at 2420 [size=8]
        I/O ports at 2440 [size=4]
        I/O ports at 20f0 [size=16]
        I/O ports at 20e0 [size=16]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at 91000000 (32-bit, non-prefetchable) [size=16M]
        Memory at 80000000 (64-bit, prefetchable) [size=256M]
        Memory at 90000000 (64-bit, non-prefetchable) [size=16M]
        Capabilities: <access denied>

03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface
        Flags: bus master, fast devsel, latency 0, IRQ 17
        I/O ports at 1018 [size=8]
        I/O ports at 1024 [size=4]
        I/O ports at 1010 [size=8]
        I/O ports at 1020 [size=4]
        I/O ports at 1000 [size=16]
        Memory at 92100000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10 [OHCI])
        Subsystem: Intel Corporation Unknown device 514d
        Flags: bus master, medium devsel, latency 32, IRQ 19
        Memory at 92004000 (32-bit, non-prefetchable) [size=2K]
        Memory at 92000000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

More Info:
```
amey@amey-desktop:~$ lsmod | grep snd
snd_hda_intel         296352  1 
snd_pcm_oss            43136  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                80388  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10372  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            34944  0 
snd_seq_midi            9600  0 
snd_rawmidi            25984  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                54000  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24452  2 snd_pcm,snd_seq
snd_seq_device          9484  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56068  13 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

```
I know that Gusty has some problem with ICH8 series. I have also tried to recompile my alsa. but still no success.

Can you help me

---

### Post by ameyjah on 2008-06-13
solved.
I have followed OSS guide and removed ALSA.
it worked for me
```
http://ubuntuforums.org/showthread.php?p=4874981
```

---

