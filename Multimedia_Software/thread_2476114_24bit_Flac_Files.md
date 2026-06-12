---
title: "24bit Flac Files"
date: 2022-06-16
forum: Multimedia Software
---

### Post by speartip on 2022-06-16
Using Ubuntu 22.04, I've got some Music which is 24bit Flac. It plays alright, if a bit on the quiet side for some reason. Does Ubuntu automatically pick up on and play 24bit files (Using Rhythmbox) or is there any codec or file I need to either download or edit to get the full benefit?

---

### Post by #&amp;thj^% on 2022-06-16
In short: no. By default pulseaudio/wireplumber and alsa are configured for 44.1kHz 16-bit audio. 
Have a look here: [https://wiki.archlinux.org/title/PipeWire#Changing_the_default_sample_rate](https://wiki.archlinux.org/title/PipeWire#Changing_the_default_sample_rate)

---

### Post by #&amp;thj^% on 2022-06-16
I use something like:
For my use I wrote to "~/.config/pipewire/ "
with this config: (Important my dac supports this and up to 32 bits)
```

 default.clock.rate          = 96000
 default.clock.allowed-rates = [ 44100 48000 88200 96000 192000 ]
```
and:
```
 cat /proc/asound/card2/pcm0p/sub0/hw_params
access: MMAP_INTERLEAVED
format: S16_LE
subformat: STD
channels: 6
rate: 48000 (48000/1)
period_size: 512
buffer_size: 32768


```

---

