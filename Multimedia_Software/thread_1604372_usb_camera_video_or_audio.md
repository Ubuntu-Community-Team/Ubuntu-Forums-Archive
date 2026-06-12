---
title: "usb camera video or audio"
date: 2010-10-23
forum: Multimedia Software
---

### Post by kajkoz on 2010-10-23
Hi
I have a problem with my Logitech QuickCam pro 4000 webcam. Under skype, I can't shows my video, and i can't talk with my interlocutor in the same time. No bi-directional voice. 
Video works under skype - option, voice either, but never together.

Under Google talk works video or voice, it is depends what I'll set up under gstreamer-properties.Video and voice never worked together.
This cameras work under windows.

content of
/proc/asound/modules 
 0 snd_hda_intel
 1 snd_usb_audio
 2 snd_hda_intel

and

/proc/asound/pcm
00-00: ALC888 Analog : ALC888 Analog : playback 1 : capture 1
00-01: ALC888 Digital : ALC888 Digital : playback 1
00-02: ALC888 Analog : ALC888 Analog : capture 1
01-00: USB Audio : USB Audio : capture 1
02-03: ATI HDMI : ATI HDMI : playback 1

---

