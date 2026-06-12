---
title: "Sound works only with AlsaPlayer"
date: 2009-02-28
forum: Multimedia Software
---

### Post by avrilrox on 2009-02-28
I have a M2N-SLI MotherBoard with an onboard chip sound called C-Media 6501 which happens to be an usb audio device.

The thing is, after compiling, recompiling, editing files, changing settings, installing stuff and everything, i got Ubuntu to play the login sound and mp3 files using **AlsaPlayer**. The rest of the applications do not seem to work, i get no sound output.

Is there anything else that i should do to make this work? I am currently running Alsa 1.0.19 (latest version) and **is** compatible with my sound driver. I checked the sound settings and everything seems to be okay.

```

asd@x2:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Thanks.

---

### Post by avrilrox on 2009-03-01
Sound works flawlessly with AlsaPlayer but it is the only program that gets to play audio. Is there anything i could check?

---

