---
title: "recordMyDesktop CLI ALSA error"
date: 2009-08-13
forum: Multimedia Software
---

### Post by harry71194 on 2009-08-13
Update: no one knows I guess, so I just used my main device.



> :~$ recordmydesktop
Initial recording window is set to:
X:0   Y:0    Width:1280    Height:800
Adjusted recording window is set to:
X:0   Y:0    Width:1280    Height:800
Your window manager appears to be Metacity

Initializing...
Buffer size adjusted to 4096 from 4096 frames.
ALSA lib pcm_hw.c:1429:(_snd_pcm_hw_open) Invalid value for card
Couldn't open PCM device hw:0,0
Error while opening/configuring soundcard hw:0,0
Try running with the --no-sound or specify a correct device.So, I try -device hw:default,0
I get:
Broken pipe: Overrun occurred.
and no sound.

I try -device plughw:default,0
No error, but no sound either. :(


How can I fix this? I am trying to have it record the sound my computer outputs, not any microphone.

I am using a headset, with a nonworking microphone, as my default soundcard. My onboard soundcard on this laptop is disabled. All the sound goes through my headset.

Thanks.

---

### Post by harry71194 on 2009-08-13
Bumpo

---

### Post by harry71194 on 2009-08-16
Bump~ ( &#65439;&#9697;&#9697;&#65439;)

---

### Post by harry71194 on 2009-08-19
Heh, would be nice if someone knew ^_^

---

### Post by harry71194 on 2009-09-08
Bump? :3

---

