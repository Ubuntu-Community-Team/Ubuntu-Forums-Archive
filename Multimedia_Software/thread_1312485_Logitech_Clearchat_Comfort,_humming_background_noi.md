---
title: "Logitech Clearchat Comfort, humming background noise"
date: 2009-11-03
forum: Multimedia Software
---

### Post by p3car on 2009-11-03
I have a Logitech Clearchat Comfort headset. When I try to use the microphone in any application I have to amplify the mic in Sound Prferences. The problem is that I then get a humming background noise. It sounds a bit like when some audio equipment is poorly connected to ground.

aplay -l returns

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```The machine is a Dell Vostro 1320.

What can I do to reduce the noise. It doesn't matter if I use Skype, Ekiga or Sound Recorder, so I guess the problem is driver or hardware related. This is on Ubuntu 9.10

---

### Post by p3car on 2009-11-04
Maybe this is related to the Dell laptop rather than the headset?

I tried the headset in my other laptop, a Lenovo T400, booting to ubuntu 9.04 from an usb-stick. I then connected the Clearchat headset and the sound was very clear with almost no background noise. If I turned full amplification on in sound preferences I had a slight background noise, but that is to be expected. 

Can this be connected to the soundcard that is built into the Dell Vostro 1320?
It identifies itself as  STAC92xx with aplay -l

and hda-intel 82801I (ICH9) according to alsaconfig
and alsamixer reports the chip as IDT 92HD81B1C5

---

### Post by p3car on 2009-11-04
I upgraded to alsa 1.0.21 but no change. Still a humming static in the background

---

### Post by BaldurK on 2009-11-20
I'm having the same problem with the same headset. Using Skype 2.2 beta which supports Pulseaudio, but Sound Recorder is not working any better. The headset never really worked for me either in previous versions of Ubuntu. If anyone has a hint on how to fix this, please do since I'm considering (due to the fact that I NEED Skype for my upcoming work) for the first time in months to set up a Windows dual-boot instead of the emergency VirtualBox I have now...

---

