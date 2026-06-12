---
title: "no sound card found"
date: 2008-06-18
forum: Multimedia Software
---

### Post by smartLeprechaun on 2008-06-18
Q. I have loaded a fairly ancient machine with the latest ubuntu ( 8.04 ). The SB Live! card that was in the machine is not configured. If I use lspci, it shows me 
00:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)
00:0b.1 Input device controller: Creative Labs SB Live! Game Port (rev 08)
01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 04)

if I do lsmod | grep snd, I get


snd_emu10k1_synth       8064  0 
snd_emux_synth         36224  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7552  1 snd_emux_synth
snd_emu10k1           146880  1 snd_emu10k1_synth
snd_ac97_codec        101028  1 snd_emu10k1
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            5632  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10500  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8320  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                54224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  14 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

if I perform aplay --list-devices

I get 
aplay: device_list:205: no soundcards found...

SO please any help would be appreciated to get the card to work

---

### Post by Pjotr123 on 2008-06-18
Check this:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)
(possibly number 5 )

---

