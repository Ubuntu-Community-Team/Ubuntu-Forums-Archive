---
title: "[solved] VIA 8237 No Audio from Coaxial Output"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by fastly on 2006-06-13
I have an onboard VIA 8237 soundcard on my Asus K8V Deluxe motherboard. This has standard audio outputs and a coaxial output.

The card was detected automatically after a fresh Dapper install and the analogue (small headphone jack) output plays sound.

There is also a digital coxaxial output that I am having difficultly enabling. I have unmuted and turned up all channels in alsamixer and the gnome volume applet.

Here is some output that may help diagnose the problem:

```

alex@arnie:~$ cat /proc/asound/cards
0 [V8237          ]: VIA8237 - VIA 8237
                     VIA 8237 with AD1980 at 0xc800, irq 209

```


```
alex@arnie:~$ lspci | grep -i audio
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

```

```
alex@arnie:~$ lsmod | grep -i snd
snd_seq_dummy           5508  0
snd_seq_oss            38372  0
snd_seq_midi           11456  0
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                64088  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            32936  4
gameport               19216  1 snd_via82xx
snd_ac97_codec        110268  1 snd_via82xx
snd_ac97_bus            4096  1 snd_ac97_codec
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
snd_pcm               104712  4 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              29064  2 snd_seq,snd_pcm
snd_page_alloc         13968  2 snd_via82xx,snd_pcm
snd_mpu401_uart        10368  1 snd_via82xx
snd_rawmidi            31648  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device         11280  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    68576  18 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              13216  1 snd
```

---

### Post by fastly on 2006-06-13
Ok, I feel a bit stupid writing this... but all I had to do was go into alsamixer, select IEC958 and press 'M' to unmute. I can then change the volume of the coaxial output using the VIA DXS channel.

---

