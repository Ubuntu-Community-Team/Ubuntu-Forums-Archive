---
title: "Swapping between HDMI and Internal Audio"
date: 2011-03-10
forum: Multimedia Software
---

### Post by maninscarymask on 2011-03-10
This is a pretty confusing issue I've been having.  I have an nvidia geforce gt430, and video works perfectly, and the internal audio works perfectly.

BUT!!  when I want to use the HDMI audio/video output on the card, the video works, but NOT the audio.

I found this:

[http://ubuntuforums.org/showthread.php?t=1668737](http://ubuntuforums.org/showthread.php?t=1668737)

and it works 100% perfectly in that the HDMI audio output works.  HOWEVER!!!  my Internal Audio is then rendered nonexistent, as evidenced by:

```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

It shows that I have two devices in Sound Preferences:

HDA NVidia
HDA NVidia Digital Stereo (HDMI)

If I add this line to my /etc/pulse/default.pa:

```

load-module module-alsa-sink device=hw:0,1

```

it then shows **4** devices, but only the Internal audio will work.

I'd like to get it to just 2 devices,

Internal Audio Analog Stereo
HDA NVidia Digital Stereo (HDMI)




Does anyone know how to stop pulseaudio from doing what it wants, and just have it do what I want?  I want to put my movies on the tv, and hear the sound on the tv.  When I need my speakers on the computer working, I swap output in sound preferences and the tv doesn't get sound.  That's ALL I want.

I'm perfectly okay with attaching or pasting whatever is needed to inspect to get this working.  What little hair I have left on my head is being pulled out as we speak...

---

