---
title: "Creative Labs SB Live! EMU10k1 NOT WORKING"
date: 2007-06-21
forum: Multimedia &amp; Video
---

### Post by SLA_leandrin on 2007-06-21
Hi guys.

I'm having trouble configuring my sound card Creative Labs SB Live!. When I first installed Ubuntu Feisty it seems to work. But after I made some upgrades now it doesn't... I've already updated my ALSA drivers, but still not working.

When I type "sudo lspci -v" in the terminal I get this:

> 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
        Flags: bus master, medium devsel, latency 32
        Memory at d0000000 (32-bit, non-prefetchable) [size=64M]
        Capabilities: [c0] AGP version 2.0

00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0) (prog-if 80 [Master])
        Subsystem: Silicon Integrated Systems [SiS] SiS5513 EIDE Controller (A,B step)
        Flags: bus master, fast devsel, latency 128
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at ff00 [size=16]

00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
        Flags: bus master, medium devsel, latency 0

00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
        Subsystem: Silicon Integrated Systems [SiS] SiS900 10/100 Ethernet Adapter
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at c400 [size=256]
        Memory at cfffb000 (32-bit, non-prefetchable) [size=4K]
        Expansion ROM at cffc0000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2

00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] USB 1.0 Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at cfffc000 (32-bit, non-prefetchable) [size=4K]

00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07) (prog-if 10 [OHCI])
        Subsystem: Silicon Integrated Systems [SiS] Onboard USB Controller
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at cfffd000 (32-bit, non-prefetchable) [size=4K]

00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
        Subsystem: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at c800 [size=256]
        Memory at cfffe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2

00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
        Subsystem: Silicon Integrated Systems [SiS] AC'97 Modem Controller
        Flags: medium devsel, IRQ 5
        I/O ports at d000 [size=256]
        I/O ports at cc00 [size=128]
        Capabilities: [48] Power Management version 2

00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP) (prog-if 00 [Normal decode])
        Flags: bus master, VGA palette snoop, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 00009000-00009fff
        Memory behind bridge: cde00000-cfefffff
        Prefetchable memory behind bridge: bdc00000-cdcfffff

00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs Unknown device 8066
        Flags: bus master, medium devsel, latency 64, IRQ 5
        I/O ports at c000 [size=32]
        Capabilities: [dc] Power Management version 1

00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at d400 [size=8]
        Capabilities: [dc] Power Management version 1

01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 3
        Memory at ce000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (32-bit, prefetchable) [size=128M]
        [virtual] Expansion ROM at cfef0000 [disabled] [size=64K]
        Capabilities: [60] Power Management version 2
        Capabilities: [44] AGP version 2.0

But "sudo asoundconf list" returns this:

> Names of available sound cards:
SI7018
UART

and "lspci |grep Live"

> 00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)


"lsmod |grep emu"
> 
snd_seq_midi_emul       7680  1 snd_trident_synth
emu10k1_gp              4736  0
gameport               16520  5 snd_trident,analog,emu10k1_gp
snd_seq                52592  10 snd_trident_synth,snd_seq_instr,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event


"aplay --list-devices"

> **** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: SI7018 [SiS SI7018], dispositivo 0: trident_dx_nx [Trident 4DWave]
  Subdispositivos: 31/32
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1
  Subdispositivo #2: subdevice #2
  Subdispositivo #3: subdevice #3
  Subdispositivo #4: subdevice #4
  Subdispositivo #5: subdevice #5
  Subdispositivo #6: subdevice #6
  Subdispositivo #7: subdevice #7
  Subdispositivo #8: subdevice #8
  Subdispositivo #9: subdevice #9
  Subdispositivo #10: subdevice #10
  Subdispositivo #11: subdevice #11
  Subdispositivo #12: subdevice #12
  Subdispositivo #13: subdevice #13
  Subdispositivo #14: subdevice #14
  Subdispositivo #15: subdevice #15
  Subdispositivo #16: subdevice #16
  Subdispositivo #17: subdevice #17
  Subdispositivo #18: subdevice #18
  Subdispositivo #19: subdevice #19
  Subdispositivo #20: subdevice #20
  Subdispositivo #21: subdevice #21
  Subdispositivo #22: subdevice #22
  Subdispositivo #23: subdevice #23
  Subdispositivo #24: subdevice #24
  Subdispositivo #25: subdevice #25
  Subdispositivo #26: subdevice #26
  Subdispositivo #27: subdevice #27
  Subdispositivo #28: subdevice #28
  Subdispositivo #29: subdevice #29
  Subdispositivo #30: subdevice #30
  Subdispositivo #31: subdevice #31
tarjeta 0: SI7018 [SiS SI7018], dispositivo 1: trident_dx_nx IEC958 [Trident 4DWave IEC958]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0



I really don't know what I have to do now... please help!!

Thanks.
LS

---

### Post by freshmeatz on 2007-06-21
do you really need two sound cards?

---

### Post by SLA_leandrin on 2007-06-21
No i don't... but I don't really know how to set SB Live! as the default card, the other one is on board...

---

### Post by fredj on 2007-06-22
Can you disable the onboard sound in the BIOS?

---

### Post by wrongo on 2007-07-09
Um, any followup on this would be appreciated. It's really important that the soundcard work. The on-board sound sux. Thx.

---

### Post by slimjim8094 on 2007-07-19
I don't have an answer, but at least I have the same problem. The problem is that emu10k1-gp (the only one you would find if you typed modprobe emu10k<tab>. The -gp is the gameport driver (if you have a PCI Live! card). We don't have the regular emu10k1 driver.

If you use the External (USB) one, I bet your Power light isn't on either

---

### Post by perstromgren on 2007-08-12
I have also problems with the SB Live! EMU10k1 , but only for input. Output is working fine, and has been all the time.

Could someone enlighten me as to the use of the Windows original driver for use under Ubuntu? I suppose there is nice description at a clicks reach,. Cold the problem be solved by using the Windows driver?

Per.

---

### Post by perstromgren on 2007-08-20
For the benefit of anyone surfing around looking for a solution to a problem similar to mine, I can tell that my problem is solved.

The solution was simple: I removed ~/.audacity

i don't know what was wrong with the file, but I don't care right now; everything works as intended.

Per.

---

