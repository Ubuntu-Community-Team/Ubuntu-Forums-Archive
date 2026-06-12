---
title: "Audio dropouts on Ubuntu 22.04"
date: 2022-10-08
forum: Multimedia Software
---

### Post by astronomertom on 2022-10-08
Recently upgraded to Ubuntu 22.04 from 20.04 and I think that is when this issue started.

I would occasionally stream radio stations through Firefox and would occasionally get audio drops - the audio just went silent but would restart if I refreshed the page and clicked play again.  Happens often enough to be annoying.  For a time I thought this was a Firefox problem.

Then I was playing a podcast in RhythmBox and noticed the occasional audio dropout every few minutes, which would pick up where it left off after a few seconds.

I also have a machine running PopOS 22.04 which does not have either of these problems when streaming radio (Firefox) or playing podcasts (Rhythmbox).

Both machines were upgraded from 20.04, not a fresh installs.

Anyone else having a similar issue or can offer a solution?
Thanks,

---

### Post by Autodave on 2022-10-09
I have seen a lot of stuff concerning FF recently.....both here and on the Mint forums.  Mostly talking about all kinds of lockups, lags, etc.  I myself do not have any of those problems.  However, I do have this one on 2 different machines: after playing videos (not all of them, but quite a few) on FF, my sound outside of FF is just a very loud static noise.  Rebooting always fixes the problem.

---

### Post by #&amp;thj^% on 2022-10-09
> **astronomertom said:**
> 
I also have a machine running PopOS 22.04 which does not have either of these problems when streaming radio (Firefox) or playing podcasts (Rhythmbox).

Both machines were upgraded from 20.04, not a fresh installs.

Anyone else having a similar issue or can offer a solution?
Thanks,
Can you see any differences in:
```
less /etc/tlp.conf
```
from both OS's of course.
Sorry a little more helpful, look at this:
```
TLP_ENABLE=1

SOUND_POWER_SAVE_ON_AC=0

SOUND_POWER_SAVE_ON_BAT=0
```
See if one or both has a "#" in front of those settings

---

### Post by astronomertom on 2022-10-09
Thanks for the idea, but there seems to be no /etc/tlp.conf file on either machine.

Note the system with the audio problem is a desktop and the system WITHOUT the problem is a laptop.

I was wondering if there was some kind of audio buffer setting that might be problem.

---

### Post by #&amp;thj^% on 2022-10-10
Ok thanks for your reply on no "tlp" installed.
> Note the system with the audio problem is a desktop and the system WITHOUT the problem is a laptop.

I don't recall your sound card for the desktop, being shown here:
```
inxi -A --no-host
Audio:
  Device-1: NVIDIA driver: snd_hda_intel
  Device-2: AMD ACP/ACP3X/ACP6x Audio Coprocessor driver: N/A
  Device-3: AMD Family 17h/19h HD Audio driver: snd_hda_intel
  Device-4: DisplayLink UOEOS Laptop Dock type: USB
    driver: cdc_ncm,snd-usb-audio
  Sound API: ALSA v: k5.19.13-zen1-1-zen running: yes
  Sound Server-1: PipeWire v: 0.3.59 running: yes

```

---

### Post by astronomertom on 2022-10-11
Interesting.
in the configuration I was running for the output - one an Apple Cinema display, the other a Logitech headset, it says the driver is hid-generic, snd-usb-audio, usbhid.

I have alternative devices on snd_hda_intel.

Perhaps I should try that next time.

Thanks.

---

