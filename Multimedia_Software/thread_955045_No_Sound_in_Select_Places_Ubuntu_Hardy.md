---
title: "No Sound in Select Places Ubuntu Hardy"
date: 2008-10-21
forum: Multimedia Software
---

### Post by NickViper1024 on 2008-10-21
Hey guys,

I have done some extensive searching on the subject of no sound in this forum and I haven't quite found a solution so I thought I would throw my particular problem up there:

I have no sound from my OS or any application EXCEPT music apps (like Amarok). In Amarok, I changed the xine output engine to ALSA, and all is well in the world. The sound volumes are configured appropriately but I just cannot get any sound to work in the OS or any app that doesnt have native sound settings.

I am using a Logitech USB headset, NOT my motherboard's default sound jacks on the back or front. My mobo is an Nvidia nForce SLI MCP 550 or 750, I can't remember which. It's a mid-range gaming mobo.

```
viper@viper:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

I have used "asoundconf set-default-card headset" (headset was the detected name of my USB headset). 

If I go to System->Preferences->Sound, I can hit "test" on ALSA or USB Sound and hear tones in my ear, but if I switch over to the Sounds tab, I can't get any sounds to play despite having both checkboxes checked and being able to hear test tones. I believe this issue is linked to regular apps like Firefox (where there is no sound config) being unable to output sound.

---

### Post by NickViper1024 on 2008-10-21
Problem Solved. 


I followed the advice on a different thread that seemed similar. I installed a PulseAudio configuration tool (pavucontrol), set my Headset to the default channel, and switched my OS sounds to PulseAudio instead of USB Audio or ALSA.

---

