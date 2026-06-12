---
title: "sound device wakeup latency?"
date: 2011-09-29
forum: Multimedia Software
---

### Post by pitkataistelu on 2011-09-29
Hey all,

I hope this hasn't been asked before--I've tried to find it, really I have.

As part of a simple bash email notification script, I use the command

```
aplay -q /home/paul/Music/notify.wav
```where notify.wav is a short (1.3sec) 22kHz wave file I extracted from a proprietary operating system. However, whether used within the script or just from the command line, if no other audio has been playing in the past few seconds or so, the wave file, though playing, will only become audible after .3 or .4 seconds or so, making it easy to mistake the notification for something else. If I issue the command again right after, it plays fine, but if I give it a while it will do the same thing again. If I'm playing audio through a different program, the sample plays correctly alongside it. Interestingly, I cannot reproduce the error when my ThinkPad x60s is **both** in its docking station **and** hooked up to AC power, though meeting just one of those requirements does not solve the issue. I've tried playing with aplay's -R (start-delay) and -A (minimum wakeup time) settings without noticing any difference. 

I'm assuming that my problem is to do with the time it takes to wake up ALSA/PulseAudio, but I can't find anything on that. Disabling gnome-power-manager makes no difference. Is there a command to wake up my audio driver/device I could issue before running aplay? Obviously affixing .3 seconds of silence to the wave file would be a cop-out.

I'm running Ubuntu 11.04 with kernel 2.6.38-11-generic on a ThinkPad x60s with the default ALSA/PulseAudio setup, no OSS emulation, and gdm+XMonad. My onboard soundcard is an HDA Intel with the AD1981 chip.

I may actually turn to generating a notification sound with siggen instead, just because. Still, curious about this one.

---

### Post by pitkataistelu on 2011-10-17
Issue is still here after installing 11.10/Oneiric Ocelot to my new SSD.

---

### Post by n411303 on 2011-10-26
If I play any sound (movie or audio anything) there is a 2/3 second delay in it starting.  Movies are synchronised but there is an initial delay.

---

