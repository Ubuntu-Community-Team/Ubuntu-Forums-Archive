---
title: "problem with mplayer that no have sounds"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by nemanaldin on 2007-02-08
hi
when i run mplayer in terminal i cant hear any sounds of my songs but when i login to ubuntu 
i can hear login sound and shutingdown sound and evry sounds in ubuntu but when run  mplayer i cant hear any sound
and it give this error:[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
Opening /dev/dvb/adapter0/audio0
DVB AUDIO DEVICE: No such file or directory
thanks very much

---

### Post by recrispi on 2007-02-09
Hi!

Maybe you don't have properly configured OSS. You could try using option -ao in mplayer to change the audio output driver (maybe ALSA or something else). It should be something like:

mplayer -ao alsa movie.avi

Anyway I recommend to try "man mplayer", it will give you all the options for the program (beware it's a HUGE manual) and when you've find the correct driver then you could update your mplayer config file .

Hope that helps.

---

### Post by dmizer on 2007-02-10
i have the same problem with my mplayer.  no ability to use alsa, and when i force it as with "mplayer -ao alsa movie.avi" i get this output:
```
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
Could not open/initialize audio device -> no sound.
Audio: no sound
Starting playback...
VDec: vo config request - 528 x 384 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.38:1 - prescaling to correct movie aspect.
VO: [x11] 528x384 => 528x384 Planar YV12 
SwScaler: using unscaled yuv420p -> rgb32 special converter
```
mplayer.conf has the following:
```
##################
# video settings #
##################

# Specify default video driver (see -vo help for a list).
vo=x11

##################
# audio settings #
##################

# Specify default audio driver (see -ao help for a list).
ao=alsa
```
~/.mplayer/config looks like this:
```
# Write your default config options here!
vo=x11
ao=alsa
```

---

