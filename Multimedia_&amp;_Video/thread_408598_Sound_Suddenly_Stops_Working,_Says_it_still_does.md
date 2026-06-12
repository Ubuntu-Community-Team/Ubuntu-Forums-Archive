---
title: "Sound Suddenly Stops Working, Says it still does"
date: 2007-04-13
forum: Multimedia &amp; Video
---

### Post by Bondolon on 2007-04-13
I have an Audigy 4, configured for surround sound.  Up until today, it was working perfectly, no problems at all.  I installed a replacement monitor, and, next thing I knew, sound stopped working.  

lspci -v says it's there
```
05:07.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs Unknown device 1021
        Flags: bus master, medium devsel, latency 32, IRQ 66
        I/O ports at a000 [size=64]
        Capabilities: [dc] Power Management version 2
```

And everything suggests that it's working fine.  I've checked every cord, every connection, reseated the card, unplugged, replugged, reverted back to one monitor and put everything back the way it was before I did this.  There is no seeming reason that it shouldn't be working.

Here's my lsmod, grepped to sound
```
snd_emu10k1_synth       8960  0 
snd_emux_synth         39296  1 snd_emu10k1_synth
snd_seq_virmidi         8576  1 snd_emux_synth
snd_seq_midi_emul       8192  1 snd_emux_synth
snd_seq_dummy           4996  0 
snd_seq_oss            36480  0 
snd_seq_midi            9984  0 
snd_seq_midi_event      8960  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                59120  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_emu10k1           128288  2 snd_emu10k1_synth
snd_ac97_codec         97696  1 snd_emu10k1
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  3 snd_seq,snd_emu10k1,snd_pcm
snd_page_alloc         11400  2 snd_emu10k1,snd_pcm
snd_util_mem            6016  2 snd_emux_synth,snd_emu10k1
snd_hwdep              10756  2 snd_emux_synth,snd_emu10k1
snd_mpu401              9640  0 
snd_mpu401_uart        10240  1 snd_mpu401
snd_rawmidi            27264  4 snd_seq_virmidi,snd_seq_midi,snd_emu10k1,snd_mpu401_uart
snd_seq_device          9868  8 snd_emu10k1_synth,snd_emux_synth,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_emu10k1,snd_rawmidi
snd                    58372  17 snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_raw

```

and here's what happens when I speaker test to 5.1
```
tim@timmay:~$ /usr/bin/speaker-test -c 5.1

speaker-test 1.0.11

Playback device is default
Stream parameters are 48000Hz, S16_LE, 5 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 16384
Period size range from 16 to 16384
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
 1 - Front Right
 2 - Rear Left
 3 - Rear Right
 4 - Center
Time per period = 14.594301

```

No errors, no problems, no sound.  I've modprobed and everything else I can think of, and still no sound.

Has anyone encountered this problem, or a similar problem?

---

### Post by Bondolon on 2007-04-13
Update: I booted into my ridiculously broken Windows installation, and the sound card definitely works.  I am now booted into the previous kernel (not the most recent one) and I've still got no sound.

---

### Post by Bondolon on 2007-04-13
Fixed it by deleting /var/lib/alsa/asound.state and then enabling (not disabling) the 'Audigy Analog/Digital Output Jack' check box

---

