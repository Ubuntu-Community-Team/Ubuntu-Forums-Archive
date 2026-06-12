---
title: "Audio from HDMI not working"
date: 2010-05-05
forum: Multimedia Software
---

### Post by mrblaineng on 2010-05-05
Hey guys, I currently installed ubuntu 10.04 and I am having trouble getting sound from my monitor. The monitor that I have is a HANNS-G HH251. It is connected to a Sapphire 4850 Video card through a HDMI wire. The monitor has audio when I boot it in windows7, but there is no audio when I use ubuntu 10.04. Thanks!

---

### Post by lidex on 2010-05-06
Can you post the output of these commands please:
```
sudo lspci -nn | grep VGA
aplay -l 
```

---

### Post by mrblaineng on 2010-05-06
For the first command I got this:

01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV770 [Radeon HD 4850] [1002:9442]

For the second command I got this:

card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Thanks!

---

### Post by lean on 2010-05-06
Stupid question. Have you chosen the hdmi output from the sound preferences?

Click the speaker icon, sound preferences, output. Choose hdmi.

---

### Post by mrblaineng on 2010-05-06
> **lean said:**
> Stupid question. Have you chosen the hdmi output from the sound preferences?

Click the speaker icon, sound preferences, output. Choose hdmi.

Yup, I have tried that already. Thanks for the suggestion though.

---

### Post by lidex on 2010-05-06
Have a look here if you haven't already:
[http://alsa.opensrc.org/DigitalOut]("http://alsa.opensrc.org/DigitalOut")
I'll reiterate one section here:
> Mixer settings will affect your testing later on, so check them now. Run alsamixer. Check that Playback or All is selected for View (top of screen). Look for the following channels and take action as noted.
    * IEC958 Output: Press M to unmute.
      Error creating thumbnail: Unable to run external programs in safe mode.
      alsamixer with IEC958 channels set to PCM out.
    * IEC958, IEC958 1 or similarly named channels: Set to "PCM Out". 

---

