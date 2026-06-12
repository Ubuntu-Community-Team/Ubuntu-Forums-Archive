---
title: "m-audio keyrig no imput lmms"
date: 2010-09-08
forum: Multimedia Software
---

### Post by homy06 on 2010-09-08
Hey,

I just got an m-audio keyrig.

I have madfuload installed and ubuntu (lynx normal not studio) recognizes it.

I can even select keyrig under midi devices, but when I press any of the keys nothing is registered. no notes or sounds. 

Any help?

I'm using alsa since lmms works better with that then jack

my input/output setting in lmms is alsa-sequencer

lsusb:
Bus 002 Device 006: ID 0763:019b Midiman KeyRig 49


cat /proc/asound/cards:
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfebfc000 irq 16
 1 [K49            ]: USB-Audio - KeyRig 49
                      M-Audio KeyRig 49 at usb-0000:00:1d.0-1, full speed


thank you


**EDIT**

Spoke too soon, I just "turned it off, and turned it on again" and it worked. 

But latency is horrible, i say a little over a second. any suggestions?

Fixed latency

make sure your buffer size is set right. and follow this guide:

[http://lmms.sourceforge.net/wiki/index.php?title=Fixing_audio_latency_on_Ubuntu](http://lmms.sourceforge.net/wiki/index.php?title=Fixing_audio_latency_on_Ubuntu) 

basically under audio tab in the settings, change the "device" field to your custom setting

mine was 
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

so I changed it to:
hw:0,0

hope that helps

---

### Post by Chronon on 2010-09-10
I'm glad you fixed your problem.  However, can you mark this as solved so that others don't open this topic trying to help and so that others looking for help can find it?

---

