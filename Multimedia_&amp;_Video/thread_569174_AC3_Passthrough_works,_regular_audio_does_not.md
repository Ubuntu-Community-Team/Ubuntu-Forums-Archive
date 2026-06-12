---
title: "AC3 Passthrough works, regular audio does not"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by jimbodude21 on 2007-10-06
I'm using the DIN jack on a Soundblaster Audigy.  Everything was working very well - I had AC-3 passthrough for DVDs and such, and regular audio for TV watching with MythTV.  Suddenly, I am not able to get any sound over the DIN cable except AC-3 passthrough.

I have a Cambridge Soundworks DTT3500 receiver which has an indicator light for DIN activity.  In the past, the light would be solid almost as soon as Ubuntu booted - indicating a good connection.  Now it flashes - indicating no connection on the DIN input.  I can switch into digital mode on the receiver to get the AC-3 sound, but no matter what mode I'm in I do not get any other audio.

I've tried the usual settings in the aslamixer to get it to work, but no luck there.  I've also checked the default card setting, and it is indeed set to the Audigy.  I'm out of ideas.

The only thing I've changed recently is that I added 2GB of RAM, for a total of 3GB.

I'm using Gusty, latest versions of everything, including:
ALSA - 1.0.14
MythTV - 0.20.20070821-1

Not sure how useful these will be, but:
asoundconf list
```
Names of available sound cards:
Audigy
UART

```

lspci | grep Creative:
```
04:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
04:08.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
04:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
```

lsmod | grep snd
```
snd_emu10k1_synth       9344  0 
snd_emux_synth         40064  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       9088  1 snd_emux_synth
snd_emu10k1           152864  2 snd_emu10k1_synth
snd_ac97_codec        122200  1 snd_emu10k1
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_pcm                94344  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         12560  2 snd_emu10k1,snd_pcm
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd_seq_dummy           5380  0 
snd_seq_oss            36864  0 
snd_seq_midi           11008  0 
snd_mpu401             11944  0 
snd_mpu401_uart        11008  1 snd_mpu401
snd_rawmidi            29824  4 snd_seq_virmidi,snd_emu10k1,snd_seq_midi,snd_mpu
401_uart
snd_seq_midi_event      9984  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                62496  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul
,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10260  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd
_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    69288  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_
ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_mpu401,sn
d_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              10272  1 snd
```

---------------------------------------
EDIT:
Additional information:
I am able to get sound using the regular 1/8" jacks if I shut off the "Audigy Analog/Digital Output Jack" in alsamixer - as expected.  This is not a permanent solution, because I'm unable to use AC-3 passthrough with the mixer configured in this manner.

---

### Post by PhatBoy on 2007-12-01
I have a similar problem:

Audigy 2 ZS

With a DVD playing I get Dolby digital out to external receiver via spdif pass through.

With any other source I get no output on the digital jack but I do get an output on the analog jacks. (Unfortunately due to speaker setup and other uses I make of the analog jacks this is not ideal plus I lose the ability to use the external receiver's pro logic for upmixing stereo inputs).

The strange thing is I did used to have it working in such a way that I always had a digital output that switched between being 2 channel or more depending on source (which is how it works in Windows) but either I have changed something or an update has...

Any ideas anyone?

Cheers.

:?:

---

### Post by jimbodude21 on 2007-12-01
I still have this problem.

My solution was to simply use the analog outputs.  When I have an AC-3 signal, I pump it through the digital output.  My receiver automatically switches inputs, so it's not that inconvenient.

---

### Post by PhatBoy on 2007-12-02
Cracked it:

[http://ubuntuforums.org/showthread.php?p=3877095#post3877095](http://ubuntuforums.org/showthread.php?p=3877095#post3877095)

---

### Post by rpangrle on 2007-12-04
A somewhat less invasive solution that doesn't require copying files or rebooting would be to use this command:

```
iecset audio on
```

it can be found in the alsa-utils package.

(from: [http://ubuntuforums.org/showthread.php?p=3674039](http://ubuntuforums.org/showthread.php?p=3674039))

---

