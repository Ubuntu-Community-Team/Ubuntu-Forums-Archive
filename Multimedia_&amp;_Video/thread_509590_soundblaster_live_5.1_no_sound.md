---
title: "soundblaster live 5.1 no sound"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by Emul on 2007-07-25
Hi guys!

I used debian for a few years, but im really newbie in ubuntu. 
Not long ago i installed a feisty fawn. It worked well.
But sometimes the sound is just disappeared, but i was able to repair it.
The sound is just muted without any reason. I killed every process that could hold the device but helped nothing.
Then made a reboot, and change again the device priority with *asoundconf -set-default-card Live*
But now, i cant make it work.
Here are the parameters:
[I]
emul@huneyubu:~$ asoundconf list
Names of available sound cards:
Live
Bt878
V8237

emul@huneyubu:~$ aplay --list-device
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive 5.1 [SB0060]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SBLive 5.1 [SB0060]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive 5.1 [SB0060]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 2: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


 modinfo snd-emu10k1
filename:       /lib/modules/2.6.20-16-generic/kernel/sound/pci/emu10k1/snd-emu10k1.ko
license:        GPL
description:    EMU10K1
author:         Jaroslav Kysela <perex@suse.cz>
srcversion:     7223A272B5A86C9BA96DDB2
alias:          pci:v00001102d00000008sv*sd*bc*sc*i*
alias:          pci:v00001102d00000004sv*sd*bc*sc*i*
alias:          pci:v00001102d00000002sv*sd*bc*sc*i*
depends:        snd-pcm,snd-util-mem,snd-page-alloc,snd,snd-rawmidi,snd-timer,snd-hwdep,snd-ac97-codec,snd-seq-device
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           index:Index value for the EMU10K1 soundcard. (array of int)
parm:           id:ID string for the EMU10K1 soundcard. (array of charp)
parm:           enable:Enable the EMU10K1 soundcard. (array of bool)
parm:           extin:Available external inputs for FX8010. Zero=default. (array of int)
parm:           extout:Available external outputs for FX8010. Zero=default. (array of int)
parm:           seq_ports:Allocated sequencer ports for internal synthesizer. (array of int)
parm:           max_synth_voices:Maximum number of voices for WaveTable. (array of int)
parm:           max_buffer_size:Maximum sample buffer size in MB. (array of int)
parm:           enable_ir:Enable IR. (array of bool)
parm:           subsystem:Force card subsystem model. (array of uint)


lspci -v
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
        Subsystem: ASUSTeK Computer Inc. K8V Deluxe/K8V-X motherboard
        Flags: bus master, 66MHz, medium devsel, latency 8
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South] (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        Memory behind bridge: f9100000-fd2fffff
        Prefetchable memory behind bridge: cfb00000-efafffff
        Capabilities: <access denied>

00:08.0 RAID bus controller: Promise Technology, Inc. PDC20376 (FastTrak 376) (rev 02)
        Subsystem: ASUSTeK Computer Inc. A7V8X motherboard
        Flags: bus master, 66MHz, medium devsel, latency 240, IRQ 16
        I/O ports at ec00 [size=64]
        I/O ports at dc00 [size=16]
        I/O ports at cc00 [size=128]
        Memory at fdb00000 (32-bit, non-prefetchable) [size=4K]
        Memory at fda00000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <access denied>

00:09.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
        Subsystem: LeadTek Research Inc. WinFast TV 2000
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at efe00000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

00:09.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
        Subsystem: LeadTek Research Inc. Unknown device 6606
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at eff00000 (32-bit, prefetchable) [size=4K]
        Capabilities: <access denied>

00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fdd00000 (32-bit, non-prefetchable) [size=16K]
        I/O ports at a000 [size=256]
        Expansion ROM at fdc00000 [disabled] [size=128K]
        Capabilities: <access denied>

00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
        Subsystem: Creative Labs SBLive! Player 5.1
        Flags: bus master, medium devsel, latency 64, IRQ 16
        I/O ports at a400 [size=32]
        Capabilities: <access denied>

00:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at a800 [size=8]
        Capabilities: <access denied>

00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46) (prog-if 10 [OHCI])
        Subsystem: VIA Technologies, Inc. IEEE 1394 Host Controller
        Flags: bus master, medium devsel, latency 64, IRQ 18
        Memory at fde00000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at b000 [size=128]
        Capabilities: <access denied>

00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V Deluxe/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 19
        I/O ports at e400 [size=8]
        I/O ports at e000 [size=4]
        I/O ports at d800 [size=8]
        I/O ports at d400 [size=4]
        I/O ports at d000 [size=16]
        I/O ports at c800 [size=256]
        Capabilities: <access denied>

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 32, IRQ 19
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
        I/O ports at fc00 [size=16]
        Capabilities: <access denied>

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at b400 [size=32]
        Capabilities: <access denied>

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at b800 [size=32]
        Capabilities: <access denied>

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at c000 [size=32]
        Capabilities: <access denied>

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81) (prog-if 00 [UHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 20
        I/O ports at c400 [size=32]
        Capabilities: <access denied>

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at fdf00000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/A8V Deluxe motherboard
        Flags: bus master, stepping, medium devsel, latency 0
        Capabilities: <access denied>

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: ASUSTeK Computer Inc. A7V600/K8V-X/K8V Deluxe motherboard (ADI AD1980 codec [SoundMAX])
        Flags: medium devsel, IRQ 22
        I/O ports at 1000 [size=256]
        Capabilities: <access denied>

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
        Flags: medium devsel, IRQ 22
        I/O ports at 1400 [size=256]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 21
        Memory at fc000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fb000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fd200000 [disabled] [size=128K]
        Capabilities: <access denied>
[/I]
The system is Ubuntu Feisty Fawn, i'm using the spdif out on the Live 5.1.
Theres an onboard VIA soundcard in the computer, i turned it off in the BIOS, but the ubuntu is recognizeing it anyway.

The question is:
What musti do if i want sound?
Is  there a tutorial somewhere for live 5.1 and ubuntu?


PS: Sry for my bad english.

---

### Post by OffAxis on 2007-07-25
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")
Is the best sound guide I could find.

I was able to set my Soundblaster Live with the 
**asoundconf set-default-card Live**
and it stuck (previously, it kept switching back to the onboard audio as the primary).

---

### Post by Emul on 2007-07-25
yeah i know, is just dont know the reason.
And now the primary card is Live, and its still not working

---

### Post by gwoodard on 2007-07-25
Have you tried disabling the onboard sound through BIOS?

I had the same trouble with it, but now it works:)

---

### Post by Emul on 2007-07-26
*"Have you tried disabling the onboard sound through BIOS?"*

[I]"Theres an onboard VIA soundcard in the computer, i turned it off in the BIOS, but the ubuntu is recognizeing it anyway."
[/I]

But i'll check it again tonight, just for sure.

---

### Post by Emul on 2007-07-26
up!

---

### Post by gwoodard on 2007-08-07
up as in sound card is working or like up something else?

---

### Post by Emul on 2007-08-09
Yes its working, but i had to config with hand.
But theres no sound in flash.
I tried everything i found(example firefoxrc <- aoss), but didnt help.

So im searching a method to get the sound system back to the "industrial" default settings.

---

### Post by Emul on 2007-08-10
where can i find a place where i can find help?

---

