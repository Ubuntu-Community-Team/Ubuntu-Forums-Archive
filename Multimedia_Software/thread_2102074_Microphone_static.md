---
title: "Microphone static"
date: 2013-01-06
forum: Multimedia Software
---

### Post by dannyboy79 on 2013-01-06
I used to be able to record audio using my Turtle Beach X31's (gaming headset and mic) with a 1/8" female to 3/32" male adapter connected to my mic input port (pink) and use audacity to record my voice without and static at all. 

THen I installed an HD PVR (usb HD capture device device) and a Logitech C260 (usb webcam) and now when I try to record with audacity there is a bunch of static in my recordings. I don't know how to fix, I could try to unplug those devices and see if that fixes it but that would be a pain to have to do everytime I want to record my voice.

My hardware is as follows
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: VT82xx [HDA VIA VT82xx], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 3: VT82xx [HDA VIA VT82xx], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I haven't done anything special to any config files except I followed an ARCH guide to remove static by setting the default sampling rate within /etc/pulse/daemon.conf to 96000 which is what my hardware showed when using command
```
arecord -f dat -r 60000 -D hw:0,0 -d 5 test.wav
```
and that returned the following
```
Recording WAVE 'test.wav' : Signed 16 bit Little Endian, Rate 60000 Hz, Stereo
Warning: rate is not accurate (requested = 60000Hz, got = 96000Hz)
         please, try the plug plugin
```
Can anyone please help?

---

