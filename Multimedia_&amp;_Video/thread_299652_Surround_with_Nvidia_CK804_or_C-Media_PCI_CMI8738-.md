---
title: "Surround with Nvidia CK804 or C-Media PCI CMI8738-MC8"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by the ev on 2006-11-14
I'm trying to get surround sound working with either of these two devices, and I haven't been able to find help anywhere else.  I've tried this guide ([http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml]("http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml")) and when it told me to run speaker-test I got the following error:

For speaker-test -c 6 -D surround51
```
speaker-test 1.0.11

Playback device is sorround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM sorround51
Playback open error: -2,No such file or directory

```

..with the last two lines repeating until I terminated the process.  Elsewhere on the forum I found another speaker-test command and tried that (speaker-test -c6 -Dlug:surround51), resulting in the same as above.

All of that was for the Nvidia CK804, which is the onboard sound on my motherboard.  The speaker-test command yielded the following when I switched devices to the C-Media:
```
speaker-test 1.0.11

Playback device is surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 12 to 5461
Period size range from 6 to 2730
Using max buffer size 5461
Periods = 4
was set period_size = 0
was set buffer_size = 5461
Unable to set sw params for playback: Invalid argument
Setting of swparams failed: Invalid argument

```

Both devices work so far as providing sound to the front left and right channels; the center, woofer, and surround channels are silent.  lsmod gives me this:
```
Module                  Size  Used by
snd_intel8x0           42024  1 
snd_ac97_codec        127064  1 snd_intel8x0
snd_ac97_bus            4352  1 snd_ac97_codec
snd_cmipci             48672  1 
snd_pcm_oss            57344  0 
snd_mixer_oss          22784  1 snd_pcm_oss
nvidia               5673048  36 
snd_pcm               108168  5 snd_intel8x0,snd_ac97_codec,snd_cmipci,snd_pcm_oss
snd_opl3_lib           15104  1 snd_cmipci
snd_hwdep              14088  1 snd_opl3_lib
snd_mpu401             12200  0 
snd_mpu401_uart        12928  2 snd_cmipci,snd_mpu401
snd_timer              31112  2 snd_pcm,snd_opl3_lib
snd_rawmidi            34432  1 snd_mpu401_uart
snd_seq_device         12180  2 snd_opl3_lib,snd_rawmidi
gameport               21008  2 snd_cmipci,analog
i2c_nforce2             9984  0 
pcspkr                  5248  0 
snd                    79016  16 snd_intel8x0,snd_ac97_codec,snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_hwdep,snd_mpu401,snd_mpu401_uart,snd_timer,snd_rawmidi,snd_seq_device
i2c_core               29312  3 i2c_ec,nvidia,i2c_nforce2
soundcore              14112  1 snd
snd_page_alloc         13200  2 snd_intel8x0,snd_pcm

```
(I edited out all the entries that didn't seem related to sound).

This is driving me nuts.  I tried, per [this]("http://ubuntuforums.org/showthread.php?p=1744216") post to delete or rename .asoundrc and .asoundrc.asoundconf, but that seemed to accomplish absolutely nothing.

I also followed up on [this]("http://ubuntuforums.org/showthread.php?t=96370&highlight=nvidia+sound") post, except that I can't seem to install the Nvidia nForce drivers since I'm on a x86_64 system.  

Help!](*,)

---

