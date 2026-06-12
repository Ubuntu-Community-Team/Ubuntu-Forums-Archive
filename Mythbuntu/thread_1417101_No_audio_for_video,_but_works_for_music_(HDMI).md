---
title: "No audio for video, but works for music (HDMI)"
date: 2010-02-26
forum: Mythbuntu
---

### Post by korgman on 2010-02-26
This is a new one for me.  I enable mythbuntu weekly builds and did an upgrade.  I get no audio over HDMI when I watch live TV or a video.  I DO get audio over HDMI with the music player.

matt@mythtv:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

It finds my device and speaker-test -c2 give me white noise in the L/R channels.  Front the frontend log:

```

2010-02-26 22:13:27.038 Opening audio device 'default'. ch 2(6) sr 48000 (reenc 1)
2010-02-26 22:13:27.038 AudioOutput Error: AudioOutputALSA::SetIECStatus: snd_ctl_open(default): Invalid argument
2010-02-26 22:13:27.038 Opening ALSA audio device 'hdmi'.
2010-02-26 22:13:27.039 AudioOutput Warning: Mixer attach error -22: Invalid argument
			Check Mixer Name in Setup: 'default'
2010-02-26 22:13:27.039 NVP(6): Disabling Audio, reason is: AudioOutputALSA::SetIECStatus: snd_ctl_open(default): Invalid argument
2010-02-26 22:13:27.040 AudioOutput Error: AudioOutputALSA::SetIECStatus: snd_ctl_open(default): Invalid argument

```

I will say, that after the upgrade to weekly build there were some permission problems.  mythfrontend.sh for example did not have 'x' privileges.  Looks like maybe something similar here...i dunno

---

### Post by skip1305 on 2010-05-01
I managed to solve the same problem on my system by removing ~/.asoundrc.asoundconf

Skip

---

