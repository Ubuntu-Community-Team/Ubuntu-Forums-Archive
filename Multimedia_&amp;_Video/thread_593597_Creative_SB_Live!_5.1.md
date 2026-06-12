---
title: "Creative SB Live! 5.1"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by mike23 on 2007-10-27
Hey all... Id apreciate if someone could help.. 
My onboard sound card works perfectly. A friend of mine gave me (gift ;p) a creative sb live 5.1 pci card. Works fine in windows so i know that the card is not broken or something. I have dual boot with ubuntu 7.10.
So when i point to System->Preferences->sound i choose the SB live card, click on test and voala this continous beeep comes out of the speakers...
The thing is when i play a song the sound comes out from the onboard card :P 
How can i fix this?
Thanx guys!!

---

### Post by mike23 on 2007-10-29
anyone? ;p

---

### Post by kuroneko? on 2007-12-05
I'd appreciate it if this question could be answered as well. I have an SB Live 5.1 and can't get sound to work for the life of me.

Admittedly, I've only been using Ubuntu (Gutsy 64bit) for about 4 hours and am still feeling my way around. First time using anything Linux as well so...

When I do  lsmod | grep snd- this is what comes up:

snd_emu10k1_synth       9344  0 
snd_emux_synth         40064  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       9088  1 snd_emux_synth
snd_emu10k1           152864  1 snd_emu10k1_synth
snd_hda_intel         337192  1 
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_seq_midi_event      9984  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                62496  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_ac97_codec        122200  1 snd_emu10k1
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  4 snd_emu10k1,snd_hda_intel,snd_ac97_codec,snd_pcm_oss
snd_seq_device         10260  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_timer              27272  3 snd_emu10k1,snd_seq,snd_pcm
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd                    69288  16 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_hda_intel,snd_seq_oss,snd_seq,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
soundcore              10272  1 snd
snd_page_alloc         12560  3 snd_emu10k1,snd_hda_intel,snd_pcm

My motherboard has onboard sound but I am not sure which module would be it. It is this one [http://www.newegg.com/Product/Product.aspx?Item=N82E16813186115]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813186115")

I managed to get the video card and a whole lot of other things working...but having no sound is kind of discouraging. Any help would be appreciated. Thanks.

---

