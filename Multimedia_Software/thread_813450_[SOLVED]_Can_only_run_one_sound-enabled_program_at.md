---
title: "[SOLVED] Can only run one sound-enabled program at once"
date: 2008-05-30
forum: Multimedia Software
---

### Post by TroyDowling on 2008-05-30
I've noticed that in both installs of Hardy, of each my desktop and laptop, I can only have one program running sound at once. For example, if I'm listening to music in Rhythmbox, I can't hear the sound of a clip on YouTube via Firefox. Both programs run perfectly, however, individually. If Firefox was the first program to open, Rhythmbox refuses to play a track (reminicent of Windows Media Player when it cannot detect a sound card if that helps). This general, one-at-a-time, rule applies for nearly all programs, but there are a couple of exceptions such as Pidgin. In that program, the sounds of a new message will not play, but the sound of a log on will... I've been looking into PulseAudio, but I don't seem to be able to find anything that helps my situation. Anybody have a solution?

```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Troy.

Note that this is an HP Pavilion dv9013ca laptop. Hardy is so far the only *buntu that runs so far, but I don't attribute that to the problem because it does the same thing on my desktop system (custom build).

---

### Post by abhiroopb on 2008-05-30
Yea this happens on/off with me as well. If I'm speaking on skype and I switch on a video the video won't have sound.

---

### Post by wolfen69 on 2008-05-30
i had the same problem. [THIS]("http://ubuntuforums.org/showthread.php?t=776739") thread fixed it for me perfectly.

---

### Post by TroyDowling on 2008-06-01
Okay, I'll be sure to try that.

[jump]

Yeah, it worked perfectly for me to. Besides sound now working perfectly (haven't tested external speakers via laptop's sound port), the only difference is there is a new icon in the system tray beside the clock. At first I was kinda bummed and tried to remove it, but it's actually quite handy.

---

