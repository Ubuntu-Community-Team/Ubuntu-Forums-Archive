---
title: "Route pulseaudio monitor sound to alsa loopback device"
date: 2022-01-11
forum: Multimedia Software
---

### Post by niconl on 2022-01-11
Hello,

For an application that requires speaker level information, we want to use arecord. We have a working script that uses arecord to log in a file the volume peaks on the microphone and triggers something when the volume reaches a threshold.

Now, we want to do the same but with the sound coming from the speakers instead of the sound coming from the microphone.

In parallel to this we have another application that needs snd-aloop to be loaded, so we already have an alsa loopback device card (card 2), with device 0 and device 1, each with 8 subdevices.
So this is the output of arecord -l:
```
card 0: PCH [HDA Intel PCH], device 0: ALC3246 Analog [ALC3246 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 2: Loopback [Loopback], device 0: Loopback PCM [Loopback PCM]
  Subdevices: 7/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Loopback [Loopback], device 1: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
```

Note that for the parallel application I mentioned, we are sending some audio to hw:2,0,3 and monitoring it on hw:2,1,3.

When using arecord to list the sinks available to find the speaker, we get the following output:
[HTML]0       alsa_output.usb-Jieli_Technology_UACDemoV1.0_4150333035313401-00.iec958-stereo  module-alsa-card.c      s16le 2ch 48000Hz       SUSPENDED
1       alsa_output.pci-0000_00_1f.3.analog-stereo      module-alsa-card.c      s16le 2ch 44100Hz       SUSPENDED
2       alsa_output.platform-snd_aloop.0.analog-stereo  module-alsa-card.c      s16le 2ch 44100Hz       SUSPENDED[/HTML]

The speaker we are interested in is the USB speaker, with index 0. I have tested that I can access it nicely with 
```
pacat --record -d alsa_output.usb-Jieli_Technology_UACDemoV1.0_4150333035313401-00.iec958-stereo.monitor > dump.raw
sox -t raw -r 44100 -e signed-integer -L -b 16 -c 2 dump.raw output.wav
```
This records the speaker output, while still having the sound come out of the speaker.

What I would like is to be able to access this "alsa_output.usb-Jieli_Technology_UACDemoV1.0_4150333035313401-00.iec958-stereo.monitor" with arecord, while also keeping the output playing in the speaker, and without breaking the other parallel application that uses snd-aloop. Does anyone know if there is a simple way to either route or duplicate what is sent to ```
alsa_output.usb-Jieli_Technology_UACDemoV1.0_4150333035313401-00.iec958-stereo.monitor
``` and send that to a hw:2,1 subdevice or similar?

I have seen posts online about making a .asoundsrc file but anything I have tried just broke the parallel application that needs snd-aloop.

Thanks to anyone who could give me some pointers!

---

