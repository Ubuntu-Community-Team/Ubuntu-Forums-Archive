---
title: "Constant high frequency noise/squeal all the time"
date: 2019-06-14
forum: Multimedia Software
---

### Post by magicmike59 on 2019-06-14
There is a constant high frequency noise (I guess around 20kHz) that keeps playing in the background when my earphones are connected. It is not loud (hardly noticable) but is very annoying. It is most noticable at boot (at the Ubuntu splash screen) where it gets fairly loud. I've been having this since Ubuntu 16.04. This does not occur on my other installation (on the same laptop) that runs Gentoo but with no pulseaudio. This occurs on Ubuntu, Debian and Fedora as well. Although, on Fedora it's volume feels a bit reduced. Naturally, it seemed like a pulseaudio issue but I'm not sure.

Here's what I've tried:

[LIST=1]
[*]    Add tsched=0 to load-module module-udev-detect 
[*]    Followed the sticky on this section that had me put a script into /etc/pm/sleep.d 
[*]    Blacklisting snd_hda_codec_realtek
[*]Muting microphone input.
[*]Muting Loopback mixing, capture etc. in alsamixer
[/LIST]
 None of them worked.

```

uname -a

Linux testbench 4.18.0-21-generic #22~18.04.1-Ubuntu SMP Thu May 16 15:07:19 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

```

aplay -l

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
card 0: HDMI [HDA Intel HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3227 Analog [ALC3227 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Any help is appreciated. Thank You.

---

### Post by Autodave on 2019-06-14
Are the earphones wired or wireless?

---

