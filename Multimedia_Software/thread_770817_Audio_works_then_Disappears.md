---
title: "Audio works then Disappears"
date: 2008-04-27
forum: Multimedia Software
---

### Post by PlatoDan on 2008-04-27
Hi,

I've been using Ubuntu off and on for a while now but I had some problems with Gutsy and stopped using Ubuntu for a while. Now that Hardy is out I'm back. 

But I have an odd problem... I installed all the audio and video codecs via various guides around the forums, and everything worked fine at first. I then left my computer up for a while (like 8 hours while I slept) and when I came back the sound would not work with any media file. (If I went to a website in firefox I would have sound.) But mp3s and all videos would not playback audio. (The video was fine in VLC, but in totem it skipped.) This problem is also fixed by restarting X, but it is rather annoying...

My sound card comes up as the following in  aplay -l

```
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
```

If you have any idea, please let me know!

---

### Post by compacho on 2008-04-27
I too have this problem. When Ubuntu fully loads up, sound and video works for a while perfectly but somewhere along the line everything just goes screwy. I'll play a video in totem but it will play slowly. As for audio, when i try to highlight a music file in nautilus for a preview, no sound comes through but if i open the file in audacious it works fine.

Like i said, everything works upon boot up but later on it doesn't work so well.

---

### Post by Aesir09 on 2008-04-27
grrrr i know i used too love ubuntu as well and i got my own laptop and couldnt get gutsy to work.

now im living my dream. except can't get wifi card to work or audio!

```
dom@dom-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

