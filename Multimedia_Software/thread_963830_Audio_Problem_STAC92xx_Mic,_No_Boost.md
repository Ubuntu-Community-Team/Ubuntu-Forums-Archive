---
title: "Audio Problem: STAC92xx Mic, No Boost"
date: 2008-10-30
forum: Multimedia Software
---

### Post by koruptid on 2008-10-30
I ran into this problem while attempting to use skype:

I can get the mic to function, however the input from it is so low that it may as well be non-functional.

In the volume control under "HDA Intel" the recording device "Capture" is enabled, this is the only device thus far that I have been able to get skype to even recognize on the test call.... settings skype to use "pulse" just results in absolutely no sound at all.

Skype Selected "Sound In": "HDA Intel (hw:Intel,0)"

My computer is a Dell Inspiron 1520 with a STAC92xx audio chipset
(82801H (ICH8 Family) HD Audio Controller with Sigmatel STAC9227 Codec)


Changes I've Made hoping it would work:

in ~/.asoundrc
```

pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}

```


in /etc/pulse/daemon.conf
```

default-fragments = 8
default-fragment-size-msec = 5

```

I've also installed all the pulseaudio utilities in order to try to find the problem and thus far have been unsuccessful. I am a programmer and technician (and general geek) so any ideas that are had I should be able to follow. So far I have tried just about every conceivable change and nothing has worked.

---

### Post by koruptid on 2008-10-30
Additional Info:
PulseAudio Manager has a source device identified as
"alsa_input.pci_8086_284b_sound+card_0_alsa_capture_0"
(ALSA PCM on front:0 (STAC92xx Analog) via DMA)

the Volume reads as 100% but the slider shows it more like 10%, trying to push the slider >100% causes it to return to original position.

Why would the slider be displaying at such a low position and not be movable??

---

### Post by koruptid on 2008-10-31
anybody know if this problem is resolved with alsa 1.0.18??

---

### Post by autocrosser on 2008-10-31
I would start by looking in the closed development forum--We most likely covered that problem:  [http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

If not--you will quickly get a idea who to talk to....

---

