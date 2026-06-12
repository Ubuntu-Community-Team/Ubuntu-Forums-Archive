---
title: "5 Channel Sound Issue Sound Blaster Audigy"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by bedem on 2007-05-09
Hi All,

Running Kubuntu Edgy Eft (6.10) with a Sound Blaster Audigy LS 5.1. To confirm the correct setup, I have a sub-woofer, a Left & Right Front speaker pair, a Left & Right Rear speaker pair and a Front Centre speaker.

I have sound from the two front speakers & the sub-woofer, and they play to a very good volume however I am unable to access the other three speakers.

Here are some systems outputs:

<code>sudo lspci -vv</code>

00:0a.0 Multimedia audio controller: Creative Labs SB Audigy LS
        Subsystem: Creative Labs Unknown device 100a
        Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32 (500ns min, 5000ns max)
        Interrupt: pin A routed to IRQ 185
        Region 0: I/O ports at d000 [size=32]
        Capabilities: [dc] Power Management version 2
        Flags: PMEClk- DSI+ D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=0 PME-

<code>sudo asoundconf list</code>

Names of available sound cards:
CA0106
UART

<code>sudo lsmod | grep snd</code>

snd_ca0106             36228  4
snd_mpu401              9640  1
snd_mpu401_uart        10240  1 snd_mpu401
snd_ac97_codec         97696  1 snd_ca0106
snd_pcm_oss            47360  0
snd_mixer_oss          19584  3 snd_pcm_oss
snd_rawmidi            27264  2 snd_ca0106,snd_mpu401_uart
snd_seq_device          9868  1 snd_rawmidi
snd_pcm                84612  4 snd_ca0106,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  2 snd_pcm
snd_ac97_bus            3456  1 snd_ac97_codec
snd                    58372  14 snd_ca0106,snd_mpu401,snd_mpu401_uart,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
snd_page_alloc         11400  2 snd

<code>cat /proc/asound/modules</code>

0 snd_ca0106
1 snd_mpu401

<code>aplay -l</code>

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Using Alsamixer, I am able to increase the volume levels for the Center, Front, Rear and Side speakers however it makes no difference in relation to actual output.

It would be nice to have full surround 5.1 functionality so any comments welcome.

cheers, bedem.

---

### Post by r4e on 2007-05-19
It could be that your other speakers are muted. You can check in alsamixer. There are tons of switches hidden off screen to the right, so make sure you scroll over.

To get my rear speakers working I had to unmute Duplicate and External. I also had to switch Surround to Shared, although you may have to just tinker around with the settings as you have a different setup than me.

---

### Post by r4e on 2007-05-19
Sorry--I missed the last two sentences of your post, so this probably doesn't help.

---

### Post by pbw on 2007-05-19
I have the same setup, if you'd like me to upload my asound.state file for you i can.

---

### Post by icantdothatdave on 2007-05-21
@bedem: Are you using the digital output of your card? Are you trying to use all of the speakers for any output such as music, or for Dolby/DTS?

@pbw: please link to your asound.state

---

### Post by Yellowbelly on 2007-05-24
I have logitech z560's 4.1 analog and my rear speakers don't work either. They work fine in windows and they'll work being set as front speakers but they won't work as rear surround speakers. I don't really know what alsa mixer is either or anything about linux sounds stuff.

edit: nvm. fixed with the newly found alsa mixer by adjusting rear speaker volumes/surround

---

### Post by swapnil_bhartiya on 2008-05-04
I got a new HP a6340in desktop and installed Ubuntu 8.04. I have 2 issues:

1. Audio is working fine, but I cannt configure 5.1 audio, also when I insert a headphone in the front headphone jack, it continues to deliver audio through backfront speakers.
2. My SK 2960 keyboard's multimedia keys are not working, where as these both things work well with Fedora....could you please help?

---

