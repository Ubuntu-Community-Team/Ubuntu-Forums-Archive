---
title: "T42 Sound problem"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by jram on 2007-01-15
Hi, 

I installed ubuntu edgy today on my IBM T42 Laptop. The sound was working properly.  I was able to play videos on video.google.com and DVDs using Totem after I installed some codecs. Then I started installed JRE and other software tools. After sometime I realized that the sound stopped working. I wen thru a "Comprehensive.." sticky on Multimedia issues and these are the result of the commands I executed as per the sticky. Please help me figure out how to resolve the sound issue? Thanks in advace!

I executed this command.
aplay -l

This was the output.

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
-----------------------------------------------------------

I executed this command.
lspci -v

This was the output.
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
        Subsystem: IBM Unknown device 0529
        Flags: bus master, fast devsel, latency 0
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 96
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
        I/O behind bridge: 00003000-00003fff
        Memory behind bridge: c0100000-c01fffff
        Prefetchable memory behind bridge: e0000000-e7ffffff

00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 052d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1800 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 052d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1820 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])
        Subsystem: IBM Unknown device 052d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1840 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])
        Subsystem: IBM Unknown device 052e
        Flags: bus master, medium devsel, latency 0, IRQ 11
        Memory at c0000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=08, sec-latency=64
        I/O behind bridge: 00004000-00008fff
        Memory behind bridge: c0200000-cfffffff
        Prefetchable memory behind bridge: e8000000-efffffff

00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
        Subsystem: IBM Unknown device 052d
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at <unassigned>
        I/O ports at 1860 [size=16]
        Memory at 70000000 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
        Subsystem: IBM Unknown device 052d
        Flags: medium devsel, IRQ 11
        I/O ports at 1880 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
        Subsystem: IBM Unknown device 0554
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 1c00 [size=256]
        I/O ports at 18c0 [size=64]
        Memory at c0000c00 (32-bit, non-prefetchable) [size=512]
        Memory at c0000800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
        Subsystem: IBM Unknown device 055a
        Flags: medium devsel, IRQ 11
        I/O ports at 2400 [size=256]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] (prog-if 00 [VGA])
        Subsystem: IBM Unknown device 0530
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>

02:00.0 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
        Subsystem: IBM Unknown device 0552
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at b0000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=03, subordinate=06, sec-latency=176
        Memory window 0: e8000000-e9fff000 (prefetchable)
        Memory window 1: c2000000-c3fff000
        I/O window 0: 00004000-000040ff
        I/O window 1: 00004400-000044ff
        16-bit legacy interface ports at 0001

02:00.1 CardBus bridge: Texas Instruments PCI4520 PC card Cardbus Controller (rev 01)
        Subsystem: IBM Unknown device 0552
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at b1000000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=02, secondary=07, subordinate=07, sec-latency=176
        Memory window 0: ea000000-ebfff000 (prefetchable)
        Memory window 1: c4000000-c5fff000
        I/O window 0: 00004800-000048ff
        I/O window 1: 00004c00-00004cff
        16-bit legacy interface ports at 0001

02:01.0 Ethernet controller: Intel Corporation 82540EP Gigabit Ethernet Controller (Mobile) (rev 03)
        Subsystem: IBM PRO/1000 MT Mobile Connection
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 11
        Memory at c0220000 (32-bit, non-prefetchable) [size=128K]
        Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at 8000 [size=64]
        [virtual] Expansion ROM at ec000000 [disabled] [size=64K]
        Capabilities: <access denied>

02:02.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
        Subsystem: Intel Corporation Unknown device 2711
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at c0210000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
-------------------------------------------------------

Checked website for alsa available chipsets. Found that ICH4 is unavailable.

------------------------------------------------------

Executed this command.

sudo modprobe snd-

The output was.
:~$ sudo modprobe snd-
Display all 151 possibilities? (y or n)
snd-ac97-bus        snd-bt87x           snd-es1688          snd-intel8x0        snd-pcm             snd-serial-u16550
snd-ac97-codec      snd-bt-sco          snd-es1688-lib      snd-intel8x0m       snd-pcm-oss         snd-sgalaxy
snd-ad1816a         snd-ca0106          snd-es18xx          snd-interwave       snd-pcxhr           snd-sonicvibes
snd-ad1848          snd-cmi8330         snd-es1938          snd-interwave-stb   snd-pdaudiocf       snd-sscape
snd-ad1848-lib      snd-cmipci          snd-es1968          snd-korg1212        snd-rawmidi         snd-tea575x-tuner
snd-ad1889          snd-cs4231          snd-es968           snd-layla20         snd-riptide         snd-tea6330t
snd-adlib           snd-cs4231-lib      snd-fm801           snd-layla24         snd-rme32           snd-timer
snd-ainstr-fm       snd-cs4232          snd-gina20          snd-maestro3        snd-rme96           snd-trident
snd-ainstr-gf1      snd-cs4236          snd-gina24          snd-mia             snd-rme9652         snd-trident-synth
snd-ainstr-iw       snd-cs4236-lib      snd-gusclassic      snd-miro            snd-rtctimer        snd-usb-audio
snd-ainstr-simple   snd-cs4281          snd-gusextreme      snd-mixart          snd-sb16            snd-usb-lib
snd-ak4114          snd-cs46xx          snd-gus-lib         snd-mixer-oss       snd-sb16-csp        snd-usb-usx2y
snd-ak4117          snd-cs5535audio     snd-gusmax          snd-mona            snd-sb16-dsp        snd-util-mem
snd-ak4531-codec    snd-cs8427          snd-gus-synth       snd-mpu401          snd-sb8             snd-via82xx
snd-ak4xxx-adda     snd-darla20         snd-hda-codec       snd-mpu401-uart     snd-sb8-dsp         snd-via82xx-modem
snd-ali5451         snd-darla24         snd-hda-intel       snd-mtpav           snd-sbawe           snd-virmidi
snd-als100          snd-dt019x          snd-hdsp            snd-nm256           snd-sb-common       snd-vx222
snd-als300          snd-dummy           snd-hdspm           snd-opl3-lib        snd-seq             snd-vx-lib
snd-als4000         snd-echo3g          snd-hwdep           snd-opl3sa2         snd-seq-device      snd-vxpocket
snd-atiixp          snd-emu10k1         snd-i2c             snd-opl3-synth      snd-seq-dummy       snd-wavefront
snd-atiixp-modem    snd-emu10k1-synth   snd-ice1712         snd-opl4-lib        snd-seq-instr       snd-ymfpci
snd-au8810          snd-emu10k1x        snd-ice1724         snd-opl4-synth      snd-seq-midi        
snd-au8820          snd-emu8000-synth   snd-ice17xx-ak4xxx  snd-opti92x-ad1848  snd-seq-midi-emul   
snd-au8830          snd-emux-synth      snd-indigo          snd-opti92x-cs4231  snd-seq-midi-event  
snd-azt2320         snd-ens1370         snd-indigodj        snd-opti93x         snd-seq-oss         
snd-azt3328         snd-ens1371         snd-indigoio        snd-page-alloc      snd-seq-virmidi
-----------------------------------------------------

---

