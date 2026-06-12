---
title: "xmame alsa spdif problem"
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by Simoo on 2007-07-10
Hi all,

I am running Xmame on Xubuntu, I have alsa setup to use my spdif output on my Audigy 2ZS which works fine for MythTV and ZSNES. However xmame no longer has sound.

Here is my /etc/asound.conf:

pcm.!default {
type plug
slave {
pcm "spdif"
rate 48000
format S16_LE
}
}

and here is the error I now get from xmame:

ALSA lib conf.c:3837:(parse_args) Parameter AES0 must be an integer
ALSA lib conf.c:3931:(snd_config_expand) Parse arguments error: Invalid argument
ALSA lib confmisc.c:1105:(snd_func_refer) Unable to find definition 'cards.Audigy2.pcm.iec958.0:CARD=0,AES0=,AES1=,AES2=,AES3='
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM spdif
Alsa error: audio open error: No such file or directory
/bin/sh: /usr/bin/esd: not found
error: esound open stream failed
info: Writing sound output to file "xmameout.wav" in 48000Hz/16/S PCM format
info: sysdep_dsp: using waveout plugin
info: dsp: using timer-based audio
info: sysdep_mixer: using alsa plugin
MIT-SHM & XV Extensions Available. trying to use.
Initialized no effect: bitmap depth = 16, color format = RGB 888 (32bpp)
Using Xv & Shared Memory Features to speed up
Average FPS: 59.621508 (1151 frames)

I am really stuck now! any help would be much appreciated.

Thank you :)

Simon

---

