---
title: "Audigy 2 being read as Audigy 1"
date: 2009-09-22
forum: Multimedia Software
---

### Post by noffle on 2009-09-22
Hello,
Previously, Windows was reading my sound card as Audigy 2 (I was given my computer second-hand so I don't know for sure), however Ubuntu is seeing it as an Audigy 1, however it still plays audio without any crackling or hissing.
a) Is this decreasing my sound quality?
b) Is there anyway I can find out what the card is for sure?
c) How could I go about fixing this problem if a) is applicable.
Thank you.

Edit: Silly billy, I got the title wrong.

---

### Post by noffle on 2009-09-23
Bring up my thread, si'l tu plait.

---

### Post by khelben1979 on 2009-09-23
What you can do is to test the [ASIO]("http://en.wikipedia.org/wiki/Audio_Stream_Input/Output") capability which the Sound Blaster Audigy 2 ZS can perform. The maximum which I've seen is 10 ms without any problems.

---

### Post by noffle on 2009-09-23
Can that compatibility test be run on Linux? I've uninstalled Windows, although I guess I could set-up a dual-boot but it seems a bit superfluous to test what card I have. Is there not a way to force Ubuntu to use a certain driver and see if it works?
This is the output of lsmod | grep snd if that's relevant as all.
snd_emu10k1_synth      14336  0 
snd_emux_synth         40832  1 snd_emu10k1_synth
snd_seq_virmidi        13440  1 snd_emux_synth
snd_seq_midi_emul      14592  1 snd_emux_synth
snd_emu10k1           144288  5 snd_emu10k1_synth
snd_intel8x0           37532  2 
snd_ac97_codec        112292  2 snd_emu10k1,snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  5 snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_util_mem           12288  2 snd_emux_synth,snd_emu10k1
snd_hwdep              15108  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event     15104  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                56880  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         14988  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62756  25 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  3 snd_emu10k1,snd_intel8x0,snd_pcm

---

### Post by khelben1979 on 2009-09-23
You can try it with FL Studio 9.0 ([FL Studio demo on download.com]("http://download.cnet.com/FL-Studio/3000-2170_4-10030774.html?tag=mncol")). Install it using Wine.

Other than that it should exist Linux native applications for this as well. Maybe [Ardour]("http://en.wikipedia.org/wiki/Ardour_%28audio_processor%29") is up to the task, I don't know.

---

