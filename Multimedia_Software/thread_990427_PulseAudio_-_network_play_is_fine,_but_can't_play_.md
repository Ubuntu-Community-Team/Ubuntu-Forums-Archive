---
title: "PulseAudio - network play is fine, but can't play locally!"
date: 2008-11-22
forum: Multimedia Software
---

### Post by gdhgdh on 2008-11-22
Hardy with all updates... problem is fairly easy to describe... Using the 'PulseAudio Chooser' (package padevchooser) I enabled the various listen / send options on multiple machines. ('Configure Local Sound Server')

Now I can easily choose what machine to play sound through - if I use the RTP Multicast sender, I can even play on multiple machines at once - really cool! :D

Alas, I am no longer able to play sound *locally* with PulseAudio. Any time an application tries to play with PA, it hangs (Audacious / Totem / whatever...)

If I force the application to use ALSA directly rather than PulseAudio, playback works perfectly.

I can see the correct local card in the padevchooser menu (gdh@gdh-home: ALSA PCM on front:0 (STAC 92xx Analog) via DMA) but apps just freeze when I start playback.

Some apps like Totem need me to kill the local 'pulseaudio' processes (children of gnome-settings-daemon) before I hear sound (I assume Totem falls back to using ALSA directly...)

ii  pulseaudio                0.9.10-1ubuntu1

---

### Post by gdhgdh on 2008-11-22
After some sleuthing, I found this in syslog:

Nov 22 23:07:08 gdh-home pulseaudio[6381]: module-alsa-sink.c: Error opening PCM device front:0: Device or resource busy

and checking the 'strace -Ff -p6381' output I could see the open() to /dev/snd/pcmC0D0p' was indeed failing.

I then did lsof -n | grep pcmC0D0p and saw that there were two instances of 'cdemud' (effectively Daemon Tools for Linux...) which were eating up connections to the ALSA devices.

So, I updated /etc/default/cdemu-daemon to say AUDIO_DRIVER="null" and rebooted the computer.

Hey presto, sound works perfectly again :)

---

