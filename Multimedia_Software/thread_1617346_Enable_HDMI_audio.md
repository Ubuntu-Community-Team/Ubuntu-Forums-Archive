---
title: "Enable HDMI audio"
date: 2010-11-09
forum: Multimedia Software
---

### Post by Bananasdoom on 2010-11-09
I have just built a HTPC and I want to use it with Mythbuntu (10.10) but I cant enable the sound through HDMI for my TV, I have a Geforce GT 240. Please can anyone point me towards a good Gide or post it.

---

### Post by dartmusic on 2010-11-09
This may help you: [http://ubuntuforums.org/showpost.php?p=10030988&postcount=10](http://ubuntuforums.org/showpost.php?p=10030988&postcount=10)

---

### Post by cotcot on 2010-11-09
Have you tried System --> Preferences --> Sound --> Hardware --> Profile --> Digital Stereo Duplex or some other selections in this list ?

---

### Post by Bananasdoom on 2010-11-09
> **cotcot said:**
> Have you tried System --> Preferences --> Sound --> Hardware --> Profile --> Digital Stereo Duplex or some other selections in this list ?

Because mythbuntu is a slimmed down xfce ubuntu setup there is no "Preferences -->" in the menu. How do I open the xfce  version of gstreamer-properties because at the moment I cant find anything but the mixer [IMG]http://dumpt.com/img/files/tews2ou8lbkwz1k80wdj.jpg[/IMG]as you can see I have changed the drop down box to HDA Nividia to no avail.[IMG]http://www.dumpt.com/img/viewer.php?file=tews2ou8lbkwz1k80wdj.jpg[/IMG][IMG]http://www.dumpt.com/img/viewer.php?file=yyttt81q0yz104sw6619.png[/IMG]

---

### Post by Bananasdoom on 2010-11-11
bump

I have not been able to play any sound through my HDMI to my tv i have  checked my tv cable rebooted and made sure that the tv is picking up  audio from the hdmi input and the computer says that the card is working  so i have no idea what is wrong so please help

```
$ sudo aplay -l
[sudo] password for : 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by dartmusic on 2010-11-11
> **Bananasdoom said:**
> bump

I have not been able to play any sound through my HDMI to my tv i have  checked my tv cable rebooted and made sure that the tv is picking up  audio from the hdmi input and the computer says that the card is working  so i have no idea what is wrong so please help

```
$ sudo aplay -l
[sudo] password for : 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Can you tell us what options are available in Sound Preferences on the Hardware tab?

Also, can you open a terminal, type "gstreamer-properties" (obviously without quotes) and tell us what options are listed in the dropdown box?

Lastly, also in the terminal, have you typed "alsamixer" and made sure that all 4 stereo pairs are unmuted?

---

### Post by lidex on 2010-11-11
Have a look here:
[http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240)

---

