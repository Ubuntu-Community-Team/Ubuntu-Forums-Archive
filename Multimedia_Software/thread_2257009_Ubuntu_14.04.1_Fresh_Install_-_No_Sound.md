---
title: "Ubuntu 14.04.1 Fresh Install - No Sound"
date: 2014-12-16
forum: Multimedia Software
---

### Post by baz.g on 2014-12-16
Hi All,

I have a fresh install of 14.04.1 on a Asus N550J and I have no sound whatsoever. I have googled and found the original culprit was because the HDMI was set to the default output, this was solved (I think) by following instructions I found on a site by creating /etc/asound.conf and adding the lines:

defaults.pcm.card 1
defaults.pcm.device 0
defaults.ctl.card 1

Now when I run alsamixer in a terminal, the first device it shows is the HDA Intel PCH device, but still I get no sound.

I have also tried following other instructions I found on another site which involved purging alsabase and pulseaudio and then reinstalling them (which also required running apt-get install ubuntu-desktop too as it removed a few things). The only other instruction I can find is to edit /etc/default/speech-dispatcher and change RUN=yes to RUN=no, but it was already set to NO after installation.

I also tried a fresh install with 14.10 but no difference.

I have also realised that the sound works fine with headphones plugged in, just not when they are not.

This is the output of aplay -l:
```

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC668 Analog [ALC668 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

Please let me know if there is any more info you need to diagnose, or what other tips you have to fix this :)

---

### Post by baz.g on 2014-12-18
Anybody please?

---

