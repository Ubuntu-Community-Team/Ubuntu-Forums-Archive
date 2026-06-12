---
title: "Cannot capture sound the is sent to speakers"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by kmcgrath on 2008-04-13
I have been trying and failing to capture the sound that goes to my speakers to a .wav file.  In Windows I have used audacity to do this often.  So I loaded up audacity in my new Hardy install and I've been fighting to get sound with no luck.  I have also tried arecord and tried to mess with JACK.  I've messed with just about every option in the Gnome Volume Control, alasamixer, and Sound Preferences.  The end result is I get nothing dumped to a file, .wav files are silent, and in audicity I just get a flatline.  

I don't know if I'm missing something very simple, but I cannot get this work at all.  Here is my output from arecord, any help would be appreciated.

 arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


 arecord -L
default:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

---

