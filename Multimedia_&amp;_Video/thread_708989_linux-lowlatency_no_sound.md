---
title: "linux-lowlatency no sound"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by realillusions on 2008-02-27
Running 7.04 on a Dell pre-intsalled 1420n, I installed the -lowlatency kernel in order to do some sound production in Rosegarden, because the -generic kernel just wasn't cutting it. However, after installing and rebooting the machine with the new kernel, I have no sound at all. Nothing on login, no sound testing works, nothing. I've checked with *aplay -l* and* lspci -v*, both of which show the card (as being there, as it is with the -generic kernel.

The relevant output of both is below

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

lspci -v | grep Audio```

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```


Help :D

---

### Post by realillusions on 2008-02-29
anyone?  :icon_frown:

---

### Post by realillusions on 2008-03-04
hate to do it again, but....bump.

---

### Post by Joe_Atlanta on 2008-03-05
> **realillusions said:**
>  I installed the -lowlatency kernel ...
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
 
You might want to check the ALSA volume control and mixer (usually somewhere on a taskbar).

On my machine (rt kernel w/ intel HD audio) the primary volume control was assigned to the stereo front channel (5.1 audio), while the mixer (double click on vol control to access) only displayed front channel and PCM . When I went into options and displayed all the other sliders, I found them all the way down (muted). Once I turned up the center and LFE channels, I had sound.

Upshot is that a bug has  **left and right stereo is assigned to center and LFE sliders**(respectively). By using the PCM slider as my main vol control (rt click/ options) and leaving the center and LFE sliders up in the mixer, I now have sound.


good luck,
Joe

---

### Post by realillusions on 2008-03-05
No dice, though center and LFE were both muted. I've made all the sliders visible, and cranked them all up to 11. I've even set all the options for the primary output, and all i'm hearing is my fingers hit the keyboard.

Any other ideas?

---

### Post by Joe_Atlanta on 2008-03-06
(on my system: Gutsy 7.10 w /2.66.2-14-rt, Gnome 2.20.1, Dell w/945 Intel mobo, 82801G (ICH7 Family) High Definition Audio Controller)

On the main menu:
system/preferences/sound

Under the *sound* icon there are a number of options for using different sound drivers, try 'em all. Good luck. It maybe that your answer lies in the terminal (about which I know nothing), or going to later version of the OS and kernel.

Joe

ps -Does the headphone out work? One of the bugs I've read about lets the headphone out work while the speaker outs are hosed.

---

### Post by realillusions on 2008-03-06
I've tried all the available drivers,, my kernel is as up to date as it can be, I believe (2.6.20-16), and I tried a Gutsy upgrade only to be met with disgust at the fonts and some other things. My headphones don't work, either.

---

### Post by Joe_Atlanta on 2008-03-07
Well, you could try a separate installation of Ubuntu Studio. It was one of the few installs that "saw" my audio (I went through 5 different live disks and installs before finding one that worked with my sound AND printer). Comes with the low latency kernel and all the audio programs you could possibly want.

Unless one of the command line experts jumps in with some way to tweak a conf file, you may be better off dropping an Audigy SE into your box. Seems to be universally supported.

good luck,
Joe

---

