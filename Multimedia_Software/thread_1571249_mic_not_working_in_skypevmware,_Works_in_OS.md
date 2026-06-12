---
title: "mic not working in skype/vmware, Works in OS"
date: 2010-09-09
forum: Multimedia Software
---

### Post by Jskarie on 2010-09-09
[solved] I cannot get mic to work in skype or vmware.  When I unmute the mic using KMix I can hear both mics clearly (laptop internal, and external mic).  

SOLUTION:  I had to activate "Capture 1" and set the default device for Capture 1 in alsamixer.  This can also be done in kmix.

If I had to guess, I would say the problem has to do with selecting the microphone input.
I've tried selecting all the possible options for microphone in Skype.

Any suggestions?

Kubuntu 10.04(32 bit)
I am using kernal 2.6.34-020634-generic.
skype 2.1.0.47 (tried 2.1.0.81)
VMware player 3.1.1


'aplay -l' lists

card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

