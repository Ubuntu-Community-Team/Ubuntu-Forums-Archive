---
title: "no sound in Ubuntu 8.10"
date: 2009-01-14
forum: Multimedia Software
---

### Post by ronti69 on 2009-01-14
Hello,
I cannot get any sound from my HP laptop with Ubuntu 8.10. Under system>preferences>sound I have set everything to "ALSA", and when I hit the test button it behaves as if everything was OK, except that I can't hear anything either from the speakers or the earphones. 
The command aplay -l returns:

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC268 Digital [ALC268 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I double clicked the volume control and made sure nothing is muted or at volume zero. Still no sound.

And the lspci command returns:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)


Can anybody please help? I am rather new to Ubuntu. I am trying to learn as much as I can... loving it already!

---

### Post by utnubuuser on 2009-01-15
Hi -- not to sure on this, but have you tried installing pulse-audio through synaptic?

And in your System>>Administration>>Hardware drivers is anything listed that's not enabled?

---

### Post by ronti69 on 2009-01-15
yes, pulse-audio is installed
all the hardware drivers are enabled...

---

