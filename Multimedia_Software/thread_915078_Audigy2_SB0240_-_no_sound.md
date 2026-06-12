---
title: "Audigy2 SB0240 - no sound"
date: 2008-09-09
forum: Multimedia Software
---

### Post by obley on 2008-09-09
Hello all, I've got a fresh install of 8.04 Hardy Heron that I can not get the sound to work with my SB Audigy2 [SB02040].

steps taken:
First, I made sure I wasn't using the digital output, that seems to be the common problem, no matter if I have it checked or not there is no difference.

Second, I made sure my onboard audio was disabled in the BIOS. For testing I enabled it and removed the Audigy. I got sound, no problem. I've reinstalled the Audigy and re-disabled the onboard in the BIOS and back to square one.

Any other ideas? I'm not sure where else to look.

here is some info I've seen others ask for with similar problems:
```

**obley@tv:~$ asoundconf list**
Names of available sound cards:
Audigy2

**obley@tv:~$ aplay -l | grep card**
card 0: Audigy2 [Audigy 2 [SB0240]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
card 0: Audigy2 [Audigy 2 [SB0240]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
card 0: Audigy2 [Audigy 2 [SB0240]], device 3: emu10k1 [Multichannel Playback]
card 0: Audigy2 [Audigy 2 [SB0240]], device 4: p16v [p16v]

**obley@tv:~$ lspci**
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
02:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
02:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 01)

**obley@tv:~$ sudo lspci -vs 02:04**
02:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
[INDENT]Subsystem: Creative Labs SB0240 Audigy 2 Platinum 6.1
Flags: bus master, medium devsel, latency 32, IRQ 18
I/O ports at b800 [size=64]
Capabilities: [dc] Power Management version 2[/INDENT]

02:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
[INDENT]Subsystem: Creative Labs Unknown device 0060
Flags: bus master, medium devsel, latency 32
I/O ports at bc00 [size=8]
Capabilities: [dc] Power Management version 2[/INDENT]

02:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10 [OHCI])
[INDENT]Subsystem: Creative Labs SB Audigy FireWire Port
Flags: bus master, medium devsel, latency 32, IRQ 19
Memory at ff905000 (32-bit, non-prefetchable) [size=2K]
Memory at ff900000 (32-bit, non-prefetchable) [size=16K]
Capabilities: [44] Power Management version 2[/INDENT]

**obley@tv:~$ lsmod | grep snd**
snd_emu10k1_synth 8064 0
snd_emux_synth 36224 1 snd_emu10k1_synth
snd_seq_virmidi 8192 1 snd_emux_synth
snd_seq_midi_emul 7552 1 snd_emux_synth
snd_emu10k1 146880 4 snd_emu10k1_synth
snd_ac97_codec 101028 1 snd_emu10k1
ac97_bus 3072 1 snd_ac97_codec
snd_pcm_oss 42144 0
snd_mixer_oss 17920 1 snd_pcm_oss
snd_pcm 78596 3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc 11400 2 snd_emu10k1,snd_pcm
snd_util_mem 5632 2 snd_emux_synth,snd_emu10k1
snd_hwdep 10500 2 snd_emux_synth,snd_emu10k1
snd_seq_dummy 4868 0
snd_seq_oss 35584 0
snd_seq_midi 9376 0
snd_rawmidi 25760 3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event 8320 3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq 54224 9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 24836 3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device 9612 8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd 56996 20 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore 8800 1 snd

**obley@tv:~$ sudo modprobe -l | grep snd-emu10k1**
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1-synth.ko
/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/emu10k1/snd-emu10k1x.ko


```

---

### Post by obley on 2008-09-15
I'm not sure what all my problem was. I tried this and wrote that and finally started to format for one last try.

got it now.... alsamixer

alsamixer
alsamixer
alsamixer

---

### Post by TBerk on 2009-04-07
Well, I too have the SB0240 card, and it worked in Intrepid (8.10) just fine.  Here in 9.04 beta it's broken.

Here is my very similar code to yours.  

I'm hoping someone can help with a fix.

TBerk

Btw- I've tried adding and removing channels & checking for MUTE On.

```

$** cat /proc/asound/cards **
 0 [Audigy2        ]: Audigy2 - Audigy 2 [Unknown]
                      Audigy 2 [Unknown] (rev.4, serial:0x10061102) at 0xdc00, irq 21

$** asoundconf list**
Names of available sound cards:
Audigy2


$ ** aplay -l | grep card**
card 0: Audigy2 [Audigy 2 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
card 0: Audigy2 [Audigy 2 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
card 0: Audigy2 [Audigy 2 [Unknown]], device 3: emu10k1 [Multichannel Playback]
card 0: Audigy2 [Audigy 2 [Unknown]], device 4: p16v [p16v]

$ **lspci**
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:02.0 Network controller: RaLink RT2800 802.11n PCI
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)


$** sudo lspci -vs 02:00**
02:00.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Device 1006
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at dc00 [size=64]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

02:00.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10)
	Subsystem: Creative Labs Device 0010
	Flags: bus master, medium devsel, latency 32, IRQ 22
	Memory at feaff800 (32-bit, non-prefetchable) [size=2K]
	Memory at feaf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

$** lsmod | grep snd**
snd_emu10k1_synth      14336  0 
snd_emux_synth         40832  1 snd_emu10k1_synth
snd_seq_virmidi        13440  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           144288  6 snd_emu10k1_synth
snd_ac97_codec        112292  1 snd_emu10k1
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  4 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         16904  2 snd_emu10k1,snd_pcm
snd_util_mem           12288  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15108  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15104  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                56880  10 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14988  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62628  23 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd

$** sudo modprobe -l | grep snd-emu10k1**
kernel/sound/pci/emu10k1/snd-emu10k1.ko
kernel/sound/pci/emu10k1/snd-emu10k1-synth.ko
kernel/sound/pci/emu10k1/snd-emu10k1x.ko

 

```

---

### Post by TBerk on 2009-04-08
I enabled and un-enabled the output jack button and it worked (finally) for me too.

TBerk



> 

**Alsa doesn't work on Debian (snd_emu10k1) **
[http://www.linuxquestions.org/questions/linux-hardware-18/alsa-doesnt-work-on-debian-sndemu10k1-716321/?highlight=audigy](http://www.linuxquestions.org/questions/linux-hardware-18/alsa-doesnt-work-on-debian-sndemu10k1-716321/?highlight=audigy)


**wet-willy**

I have SB Audigy 2ZS, I was troubleshooting another member's 'no sound' issue with the same card and suggested playing with mixer settings, like mute things you don't use etc. The next day I found I had no sound also, didn't know that when I was troubleshooting buddies issues.
Anyway, he was talking about the Audigy output jack channel in his mixer, he had Gnome and I was in Mandriva with KDE and noticed I did not have that channel in kmix. Through kmix settings I enabled it, but still no sound like him, then I muted it and VOILA!, I had sound. But disabling the Audigy output jack again rendered Mandriva soundless. It had to be enabled but muted if not used...I guess.


---

### Post by ratdude747 on 2010-01-10
same here on 10.04 alpha 1. did the same in 9.10. 

help?

---

### Post by fauzie on 2010-02-26
I managed to get audio to work with Audigy in Karmic by unmuting the "Audigy Analog/Digital Output Jack" in the [Playback] tab of Alsamixer. (It is listed as <Audigy A>. You can unmute it by pressing "m". Off course, make sure the other appropriate channels are on as well.

P.S. just type in alsamixer in a terminal

---

### Post by joctee on 2010-04-07
Thank you fauzie. That solution worked for me. I am using Ubuntu 10.04 beta and SB Audigy 2 [SB0240].

---

