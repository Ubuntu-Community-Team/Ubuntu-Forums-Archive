---
title: "Output stopped working on Steelseries Siberia USB Soundcard"
date: 2010-06-11
forum: Multimedia Software
---

### Post by woop12 on 2010-06-11
Hi

i recently installed Ubuntu and the USB soundcard worked just fine, but when i changed the "Connector" in Sound Preferences (Output tab) the output stopped working (= no sound). Input still works. Sound did not come back even when i changed the Connector setting back (I hear no sound when its set to Analog Output as well as Analog Headphones, which are the only 2 setting). 

please help
woop

---

### Post by woop12 on 2010-06-13
noone has any idea? There must be a way to get the "default settings" back, and I guess that would fix it since it worked in the beginning.

please help me with this issue

---

### Post by woop12 on 2010-06-15
Got it ...

For all those who face a similiar problem:
open "alsamixer" in a terminal, Press F6 and choose your Soundcard (for the Steelseries one its "C-Media USB Headphone Set"). Use the arrow keys to choose "Speaker" at the bottom and Max it out ( Press UP arrow). That should solve the problem.

For some reason, choosing "Analog Output" in Sound Preferences will turn down the volume for this soundcard completely.

---

### Post by AintJoe on 2010-08-24
This doesn't work for me, here is my info:

```

root@blackbox:~# uname -a
Linux blackbox 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
root@blackbox:~# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Headphone Set  ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
root@blackbox:~# cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
root@blackbox:~# head -n 1 /proc/asound/card*/codec#*
Codec: VIA VT1708B 8-Ch

```

---

### Post by Souliz on 2010-12-20
Aah thanks you saved my day! =)

---

### Post by rkwan on 2011-02-27
I recently started to experience the exact situation as the one who created the thread with the same soundcard.  I spent many hours of looking for a solution that would resolve my issue, and finally found this thread.

I tried using the method mentioned above with the alsamixer and got my audio back!  Just felt like saying thanks to woop12.

---

