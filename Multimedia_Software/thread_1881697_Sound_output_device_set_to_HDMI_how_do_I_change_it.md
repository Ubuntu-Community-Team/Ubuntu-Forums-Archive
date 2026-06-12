---
title: "Sound output device set to HDMI how do I change it"
date: 2011-11-16
forum: Multimedia Software
---

### Post by mdshann on 2011-11-16
I have a Dell Studio XPS 1340. I installed lubuntu 11.10 on it as I want a normal-ish desktop experience. Only problem is I have no sound. I have checked alsamixer in the terminal and it says that my output device is nvidia mcp79/7a hdmi. If I hit F6 to select sound card it does not give me the option to switch. I have run aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

The STAC92xx is my analog output to speakers in the laptop and headphone/mic jacks on the front. How do I go about telling alsa to stop using the HDMI? I'm pretty sure that there is nothing wrong here other than I don't know how to switch the default audio device. Ubuntu had a nice drop down menu in the sound preferences application, but there doedn't seem to be anything like that in lubuntu. The volume control does not do any mixing at all, it is just a volume control. Thanks!

---

### Post by venik212 on 2012-01-12
I have the very same problem, with the same hardware, under Lubuntu, and I also miss the nice Ubuntu sound card preferences that can be accessed from the volume control indicator.  The Gnome-Alsa-Mixer is way too complicated and I have not found the correct combination of checked and unchecked boxes to restore the sound.  It seems that Lubuntu still has a long way to go...

---

