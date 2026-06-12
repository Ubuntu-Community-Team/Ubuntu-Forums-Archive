---
title: "XBMC with OSS?"
date: 2008-12-29
forum: Multimedia Software
---

### Post by talon314 on 2008-12-29
Anyone know if XBMC can use OSS (4.1), and if so how XBMC should be configured? I keep getting

```
open /dev/sequencer or /dev/snd/seq: No such file or directory
```

or

```
there is no soundcard
```

depending on what I set the audio device as (/dev/oss/oss_hdaudio0/pcm0, /dev/oss/oss_hdaudio0/mix0, /dev/dsp, etc.)

lspci|grep Audio returns
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```
if that is of any importance.

---

### Post by talon314 on 2008-12-31
Bump.

---

### Post by talon314 on 2009-01-02
Maybe I should ask a different question: is there a way for apps created for alsa to work with oss? XBMC isn't the only application that gives me

```
open /dev/sequencer or /dev/snd/seq: No such file or directory
```

when I try to run it.

---

### Post by kozec on 2009-05-19
I'am using XMBC with OSS4 and "ALSA emulation". Write this to ~/.asoundrc...```
pcm.oss {
    type oss
    device /dev/dsp
}

pcm.!default {
    type oss
    device /dev/dsp
}

ctl.oss {
    type oss
    device /dev/mixer
}

ctl.!default {
    type oss
    device /dev/mixer
}
```
... then go to *Settings->System->Audio hardware* and  set *Audio output device* to "oss".

That should help.

---

