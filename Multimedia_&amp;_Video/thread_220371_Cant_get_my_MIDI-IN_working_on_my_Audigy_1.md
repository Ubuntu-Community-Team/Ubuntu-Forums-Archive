---
title: "Cant get my MIDI-IN working on my Audigy 1"
date: 2006-07-21
forum: Multimedia &amp; Video
---

### Post by lzap on 2006-07-21
Hello,

I cant get my MIDI-IN working. I have tested it under Windows - the midi master GM keyboard is properly connected. But MIDI applications do not work in Linux.

How can I test the MIDI connection? Here are my devices:

```
lzap@teevee:/dev/snd$ ls -1
controlC0
hwC0D0
hwC0D2
midiC0D0
midiC0D1
midiC0D2
midiC0D3
pcmC0D0c
pcmC0D0p
pcmC0D1c
pcmC0D2c
pcmC0D2p
pcmC0D3p
seq
timer
```

I have tried reading midi* devices (cat midi*) while playing the keyboard s - with no luck.

My card is Audigy 1 Platinum. The keyboards are connected to the front pannel. All MIDI modules seems to be loaded:

```
lzap@teevee:/dev/snd$ lsmod | grep midi
snd_seq_virmidi         8640  1 snd_emux_synth
snd_seq_midi_emul       8000  1 snd_emux_synth
snd_seq_midi            9888  0
snd_seq_midi_event      8064  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                58832  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_rawmidi            27552  3 snd_seq_virmidi,snd_seq_midi,snd_emu10k1
snd_seq_device          9548  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd                    60068  19 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_device,snd_timer,snd_hwdep
```

---

### Post by lzap on 2006-07-21
Midi Out works:

[HTML]lzap@teevee:~$ pmidi -l
 Port     Client name                       Port name
 62:0     Midi Through                      Midi Through Port-0
 64:0     Audigy MPU-401 (UART)             Audigy MPU-401 (UART)
 64:32    Audigy MPU-401 (UART)             Audigy MPU-401 #2
 65:0     Emu10k1 WaveTable                 Emu10k1 Port 0
 65:1     Emu10k1 WaveTable                 Emu10k1 Port 1
 65:2     Emu10k1 WaveTable                 Emu10k1 Port 2
 65:3     Emu10k1 WaveTable                 Emu10k1 Port 3

lzap@teevee:~$ pmidi -p 64:32 /mnt/win/windows/Media/town.mid
... playing...[/HTML]

---

