---
title: "Sound card initialisation problem"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by Symmetric on 2007-05-22
Hi there,

I am having some problems getting sound to work. I have two sound cards, a Audigy and a SB Live, and neither of them are working. I want the Live to be my main soundcard, as the Audigy is half broken.

I've been through all of the troubleshooting guides that I can find, in particular the Comprehensive Sound Problems Solutions Guide, but nothing seems to cover my situation.

aplay -l   gives me "no soundcards found".

****$cat /proc/asound/cards
 0 [Audigy2        ]: Audigy2 - Audigy 2 Platinum [SB0240P]
                      Audigy 2 Platinum [SB0240P] (rev.4, serial:0x10021102) at 0xa800, irq 20
 1 [Live           ]: EMU10K1 - SBLive! Value [CT4832]
                      SBLive! Value [CT4832] (rev.6, serial:0x80271102) at 0x8400, irq 21


****$cat  /proc/asound/oss/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.14rc1 emulation code)
Kernel: Linux Muted 2.6.20-muted #1 PREEMPT Sat Feb 10 15:44:12 GMT 2007 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
Audigy 2 Platinum [SB0240P] (rev.4, serial:0x10021102) at 0xa800, irq 20
SBLive! Value [CT4832] (rev.6, serial:0x80271102) at 0x8400, irq 21

Audio devices:
0: ADC Capture/Standard PCM Playback (DUPLEX)
1: ADC Capture/Standard PCM Playback (DUPLEX)

Synth devices:
0: Emu10k1
1: Emu10k1

Midi devices:
0: Audigy MPU-401 (UART)
1: EMU10K1 MPU-401 (UART)

Timers:
31: system timer

Mixers:
0: SigmaTel STAC9721,23
1: TriTech TR28602


I have tried loading the emu10k1 drivers with modprobe, this makes no difference. I'm pretty sure I'm missing something simple, but I can't figure out what.

Any help on this issue would be much appreciated.

P

---

### Post by Symmetric on 2007-06-07
(bump)
Anyone?

---

