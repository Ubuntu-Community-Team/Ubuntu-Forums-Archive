---
title: "No sound tried everything emu10k1"
date: 2008-08-16
forum: Multimedia Software
---

### Post by gladys on 2008-08-16
Hallo

I have kubuntu 8.04 with a SB Live. I have tried everything to get my sound working to no avail.

First the speakers works. The sound card works. It is unmuted in alsamixer.

I have reinstalled the drivers. Checked the kernel. Everything

Here is all my output.

manus@manus:/$ lspci -vv

01:05.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
        Subsystem: Creative Labs SBLive! 5.1 Model SB0100
        Flags: bus master, medium devsel, latency 32, IRQ 20
        I/O ports at ac00 [size=32]
        Capabilities: <access denied>

manus@manus:/$ cat /proc/asound/cards

 0 [Live           ]: EMU10K1 - SB Live 5.1
                      SB Live 5.1 (rev.10, serial:0x80641102) at 0xac00, irq 20

manus@manus:/$ modprobe snd-emu10k1 (it works)

manus@manus:/$ lsmod | grep snd
snd_rtctimer            4768  0
snd_emu10k1_synth       8448  0
snd_emux_synth         36352  1 snd_emu10k1_synth
snd_seq_virmidi         8192  1 snd_emux_synth
snd_seq_midi_emul       7808  1 snd_emux_synth
snd_emu10k1           147008  1 snd_emu10k1_synth
snd_pcm_oss            42528  0
snd_ac97_codec        101156  1 snd_emu10k1
snd_mixer_oss          18048  1 snd_pcm_oss
ac97_bus                3200  1 snd_ac97_codec
snd_util_mem            5888  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10628  2 snd_emux_synth,snd_emu10k1
snd_pcm                78852  3 snd_emu10k1,snd_pcm_oss,snd_ac97_codec
snd_seq_dummy           4996  0
snd_seq_oss            35456  0
snd_seq_midi            9504  0
snd_rawmidi            25888  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      8576  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                54096  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24964  4 snd_rtctimer,snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          9612  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    57124  15 snd_rtctimer,snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_pcm_oss,snd_ac97_codec,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11656  2 snd_emu10k1,snd_pcm


manus@manus:/$ modprobe -l | grep sound
/lib/modules/2.6.24-19-generic/kernel/sound/soundcore.ko


Sorry for the long post. I have tried everything I can think of and still no sound.

Can anybody help please.

---

