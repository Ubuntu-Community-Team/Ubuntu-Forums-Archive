---
title: "Headphones mute at medium- to high volume"
date: 2012-04-07
forum: Multimedia Software
---

### Post by PirateChef on 2012-04-07
I just got through re-formatting my HD and re-installing 11.10. My system's about a year old, and it had a couple of annoying issues and some cruft had been building up, so I hoped that this would give me a fresh start. Well, it did in a way, but some of the old problems remained, and in some cases even gotten worse!
The biggest problem is with sound. I don't have desktop speakers, only headphones. The first issue is that when I plug them in, the sound mutes. I can unmute it from the sound mixer widget on my system tray, but it's still annoying. What's worse is that the sound also mutes if the volume is too high. This is not consistant, and seems to depend upon how bassy (?) the sound is, not so much the level. For instance, I can crank up the volume on a song, and it will be okay for awhile, but when a certain part of the song kicks in, it'll kill the sound. Reducing the volume unmutes it again. So, some songs have to be listened to at a lower volume than others.

Here's my output from aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

(I tried following the steps [here]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"), but it wants me to install Unity, which I don't really feel like doing. I use KDE. Is it really necessary to install the default Ubuntu desktop just to do sound troubleshooting?)

---

