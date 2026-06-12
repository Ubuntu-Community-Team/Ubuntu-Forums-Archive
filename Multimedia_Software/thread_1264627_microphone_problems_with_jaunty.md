---
title: "microphone problems with jaunty"
date: 2009-09-12
forum: Multimedia Software
---

### Post by pdc124 on 2009-09-12
hardware 
paul@zimmy-desktop:~$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
Subdevices: 1/1
Subdevice #0: subdevice

running skype : 

 paul@zimmy-desktop:$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM cards.pcm.hdmi
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_bluetooth.c:1569:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)

ive also had RtApiAlsa: underrun detected messages in console 

skype is set to use pulse for audio out and ringing, CMI8738 device for sound in. 

After 3 days of looking at this ive ended up with a ~/.soundrc file , and re-activating bluetooth ( deactivating it just changed the error messages) 

ive tried the soundrc file from 
[http://ubuntuforums.org/archive/index.php/t-1144896.html](http://ubuntuforums.org/archive/index.php/t-1144896.html)

Skype test call records nothing - the skype voice is not in sequence for the playback . 
espeak Hello gives a pop.
Skype call to someone gives more popping sounds and no audio at the other end. 
I now get popping sounds from the speaker at my end 


Is this fixable ?

---

