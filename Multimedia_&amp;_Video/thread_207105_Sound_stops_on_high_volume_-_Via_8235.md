---
title: "Sound stops on high volume - Via 8235"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by young_dazza on 2006-07-01
Hi

I have just installed a new Asrock K7VM3 motherboard which uses the VT8235 integrated sound device.

The problem is that if i turn the volume up in alsa above about 70, the audio device simply stops outputting sound whenever a loud noise is played. It gets more sensitive to this problem the louder I set the mixer volume.

I am using mplayer to ourput directly to alsa using: mplayer -ao alsa <mp3file>. Mplayer doesnt report any errors - **mplayer continues playing the file however no sound is heard**. Nothing is output to syslog.
Xwindows is not running and I am not running esd. I am not even near the keyboard when the sound stops. I had no sound problems when I was running with my old SiS-based motherboard.

The only way to restore sound is to shutdown and turn the computer back on. Rebooting does not fix it. The problem does not happen on Windows XP.

Any ideas?

I am using ubuntu dapper. ie
Linux stb 2.6.15-23-k7 #1 SMP PREEMPT Tue May 23 14:20:54 UTC 2006 i686 GNU/Linux

lspci | grep audio shows this:
```
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
```

lsmod | grep snd shows this:
```

snd_seq_dummy           4164  0
snd_seq_oss            37696  0
snd_seq_midi            9888  0
snd_seq_midi_event      8064  2 snd_seq_oss,snd_seq_midi
snd_seq                58832  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            31192  1
snd_ac97_codec         98912  1 snd_via82xx
snd_ac97_bus            2688  1 snd_ac97_codec
snd_pcm_oss            56352  0
snd_mixer_oss          20800  2 snd_pcm_oss
snd_pcm                96772  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_mpu401              7112  0
snd_timer              27204  2 snd_seq,snd_pcm
snd_page_alloc         11592  2 snd_via82xx,snd_pcm
snd_mpu401_uart         8896  2 snd_via82xx,snd_mpu401
snd_rawmidi            27552  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          9548  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    60068  12 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
gameport               17032  2 snd_via82xx,analog
soundcore              11040  2 snd

```

And heres the contents of /proc/asound/cards
```

0 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with VIA1617A at 0xe000, irq 201
1 [UART           ]: MPU-401 UART - MPU-401 UART
                     MPU-401 UART at 0x330, irq 5

```

Cheers
- young_dazza

---

