---
title: "Sound card showing in lspci but not available"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by skenmy on 2006-12-26
Hi all,

I have a Creative Audigy 2, and this shows up properly in lspci:
```
02:15.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs Unknown device 1002
        Flags: bus master, medium devsel, latency 32, IRQ 201
        I/O ports at e800 [size=64]
        Capabilities: [dc] Power Management version 2
```

However it does not and will not show up in aplay -l:
```
**** List of PLAYBACK Hardware Devices ****
card 0: M5461 [HDA ULI M5461], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Phone [VoIPVoice USB Phone], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I have followed the "Comprehensive sound card problems guide" that is stickied at the top of this forum and I still cannot get it to show up and be available for use. I have recompiled the drivers, purged them, and emu10k1 is loaded.

Any help would be much appreciated!

---

### Post by esmail on 2006-12-28
Hello all,

I have the same problem with getting my *Creative Labs SB Live!* card to work
with Ubuntu 6.06 (Dapper).

I too followed the above mentioned guide and looked around the forum & net
w/o much luck.

I feel that I am missing some very easy simple step, but I can't figure
out what. Very frustrating. One of the reasons I like Ubuntu is that it
has shielded me from this silliness. I did my share of this with shareware,
and RH, Ubuntu has just been a dream in terms of detecting & setting up
hardware (with this exception).

root@europa:/home/bonak # **aplay -l**

aplay: device_list:221: no soundcards found...


root@europa:/home/bonak # **lspci -v**

0000:02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08 )
        Subsystem: Creative Labs: Unknown device 8032
        Flags: medium devsel, IRQ 169
        I/O ports at e8e0 [size=32]
        Capabilities: [dc] Power Management version 2

0000:02:02.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08 )
        Subsystem: Creative Labs Gameport Joystick
        Flags: bus master, medium devsel, latency 64
        I/O ports at e8d8 [size=8]
        Capabilities: [dc] Power Management version 2

root@europa:/home/bonak # **cat /proc/asound/cards**

--- no soundcards ---

root@europa:/home/bonak # **alsamixer**

alsamixer: function snd_ctl_open failed for default: No such device


and **dmesg **shows the correct drivers.

[17179588.856000] gameport: EMU10K1 is pci0000:02:02.1/gameport0, io 0xe8d8, speed 1065kHz
[17179589.148000] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emu10k1_main.c:941: vendor=0x1102, device=0x2, subsystem_vendor_id=0x80321102, subsystem_id=0x8032
[17179589.148000] ALSA /usr/src/modules/alsa-driver/pci/emu10k1/../../alsa-kernel/pci/emu10k1/emu10k1_main.c:966: Sound card name=SBLive! Value [CT4871]


root@europa:/home/bonak # **lsmod | grep snd**

snd_emu10k1_synth       9408  0
snd_emux_synth         44160  1 snd_emu10k1_synth
snd_seq_virmidi         8352  1 snd_emux_synth
snd_seq_midi_emul       7872  1 snd_emux_synth
snd_seq_oss            39680  0
snd_seq_midi           11008  0
snd_seq_midi_event      7552  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                63472  8 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           136196  1 snd_emu10k1_synth
snd_rawmidi            28288  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          9644  7 snd_emu10k1_synth,snd_emux_synth,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidisnd_ac97_codec        101024  1 snd_emu10k1
snd_pcm_oss            65312  0
snd_mixer_oss          20768  1 snd_pcm_oss
snd_pcm               108388  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              28516  3 snd_seq,snd_emu10k1,snd_pcm
snd_ac97_bus            2400  1 snd_ac97_codec
snd_page_alloc         11912  2 snd_emu10k1,snd_pcm
snd_util_mem            5536  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10464  2 snd_emux_synth,snd_emu10k1
snd                    69324  18 snd_emu10k1_synth,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_oss,snd_seq_midi,snd_seq_midi_event,snd_seq,snd_emu10k1,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_util_mem,snd_hwdep
soundcore              10784  1 snd


Any ideas??

This is on a Dell Dimension 4550.

Thanks,
Esmail

ps: I can supply the complete output of dmesg and lspci -v if that is helpfu.

---

