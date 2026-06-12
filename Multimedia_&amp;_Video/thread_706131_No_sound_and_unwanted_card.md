---
title: "No sound and unwanted card"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by freshman89 on 2008-02-24
Hello,
I'm fresh to Ubuntu, and get in troubles with setting sound on it. So I have:
cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.14 emulation code)
Kernel: Linux ghost-ubuntu 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
VIA 8237 with AD1980 at 0x1000, irq 19
SBLive! Value [CT4670] (rev.4, serial:0x201102) at 0xc000, irq 20

Audio devices:
0: VIA 8237 (DUPLEX)
1: ADC Capture/Standard PCM Playback (DUPLEX)

Synth devices:
0: Emu10k1

Midi devices:
1: EMU10K1 MPU-401 (UART)

Timers:
31: system timer

Mixers:
0: Analog Devices AD1980
1: TriTech id 3

And problem is that I disabled VIA 8237 onboard soundcard in BIOS, but Ubuntu found it anyway, and use it as my default card - I can switch to SB Live and get XMMS playing, but still have problems with Flash in Firefox, so I decided ask you how to disable permanently  VIA onboard soundcard in Ubuntu and use only SB Live. How can I do this?
Also do I really need OSS when using Flash, because as I understand ALSA works similar now?

---

