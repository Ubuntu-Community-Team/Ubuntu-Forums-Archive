---
title: "Microphone Device for VLC /dev/?"
date: 2011-05-20
forum: Multimedia Software
---

### Post by devilcode on 2011-05-20
Hi All,

I'm sure this is a quick one if you know it  but I'm stuck been searching around for a long while now.

All AUDIO works  mic/Spkers/Skype etc... which is great. 

What I am trying to do is get the mic to stream via VLC but for that i need to know the device as in /dev/video0 (webcam) but what is the same for the Mic In on the sound card and how do i find that out ?

Under **Sound Preferences >> Input ** its listed under Internal Audio Analogue Stereo (Rear Microphone)

```

cat /proc/asound/cards
0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ffc000 irq 44
 1 [HD5001         ]: USB-Audio - Microsoft® LifeCam HD-5001
                      Microsoft Microsoft® LifeCam HD-5001 at usb-0000:00:1d.7-6.2.4, high speed

``````

aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Many Thanks for your help.
Richard

---

### Post by Luz77 on 2011-10-23
Hi Richard,

I think there are no such devices for the sound.
However I've found this page:
[http://forum.videolan.org/viewtopic.php?f=4&t=89173]("http://forum.videolan.org/viewtopic.php?f=4&t=89173")

Maybe you want to have a look at their code snipped:
```
vlc -vvv v4l2:///dev/video0 :input-slave=alsa://hw:0,3 --sout
```

Haven't had the time to try it, but if you still want to fix the problem it could help you ;)

Regards, Luz77

---

