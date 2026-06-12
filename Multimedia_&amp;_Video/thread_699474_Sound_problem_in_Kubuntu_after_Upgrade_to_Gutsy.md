---
title: "Sound problem in Kubuntu after Upgrade to Gutsy"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by Qray on 2008-02-17
Hi everybody,

I had Kubuntu feisty running without any sound problems. Since my upgrade to gutsy I get no sound in KDE anymore. First thing I checked was if something is muted, but alsamixer shows no muted or low volume channels, neither does kmix. Trying out different settings in the sound part of "system settings" did not help.
Using the generic kernel instead of 386 did not help and the modules packages are installed.

If I login to KDE straight away I get no sound output. Only the sound from the line-in is working and I can control the volume (either with alsamixer or kmix). Also if I use the master volume slider, the noise gets louder and less louder. But I get no sound nor from aplay on the command line neither from Amarok etc. or system sounds.

If I switch to the konsole login in kdm **before ** loggin in to KDE, I can play a wav file with aplay without problem on the command line. After starting kdm again, again no sound. Even after stopping KDE and kdm and switching back to the command line: no sound.

So I think I can rule out Alsa driver problems... seems more to me that it is a problem with arts or something like that.

The error messages I get is: 
From aplay: 
"*aplay: pcm_write:1265: write error: Input/output error*"
From dmesg: 
many times: "*Vortex: vortex_fifo_setadbctrl fail*"
and one time inbetween: "*spurious 8259A interrupt: IRQ7*."


Maybe somebody here has an idea where to look further, because I am stuck.

Thanks in advance for any help :) 



----------------------------------------------------------------------

And here some infos that are typically asked for if posting sound problems and that may help:

Soundcard info from lspci:
```

00:0f.0 Multimedia audio controller: Aureal Semiconductor Vortex 1 (rev 02)

```

Output from aplay -l 
```

**** List of PLAYBACK Hardware Devices ****
card 0: au8820 [Aureal Vortex au8820], device 0: AU88x0 ADB [adb]
  Subdevices: 16/16
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
card 0: au8820 [Aureal Vortex au8820], device 3: AU88x0 WT [wt]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31

```

Output from lsmod | grep snd
```

snd_au8820             33696  1
gameport               15240  2 snd_au8820
snd_ac97_codec         99492  1 snd_au8820
snd_pcm_oss            43264  0
snd_mixer_oss          16640  1 snd_pcm_oss
snd_pcm                77320  3 snd_au8820,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10504  1 snd_pcm
ac97_bus                2304  1 snd_ac97_codec
snd_mpu401_uart         8576  1 snd_au8820
snd_seq_dummy           3844  0
snd_seq_oss            31872  0
snd_seq_midi            8704  0
snd_rawmidi            24832  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                50416  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22916  2 snd_pcm,snd_seq
snd_seq_device          8332  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    52356  13 snd_au8820,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_mpu401_uart,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7520  1 snd

```

---

