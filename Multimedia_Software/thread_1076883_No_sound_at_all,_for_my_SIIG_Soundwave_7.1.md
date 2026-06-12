---
title: "No sound at all, for my SIIG Soundwave 7.1"
date: 2009-02-21
forum: Multimedia Software
---

### Post by Auctionedllama@gmail.com on 2009-02-21
Hey everyone.. I am running Intrepid 8.10, and am using a SIIG Soundwave 7.1 surround sound card. I cannot get any sound to come out of it all, but the computer recognizes it. I have tried most of this: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting), some of the things here: [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012) and various other tutorials, to no success. Any help would be great, thanks!

---

### Post by markbuntu on 2009-02-21
Ok, it worked out of the box for me. 

What does aplay -l tell you?
If you open the Pulse Audio Volume Control is it listed there in Output Devices. It should be:

ALSA PCM on front:2 (C-Media PCI DAC/ADC) via DMA

---

### Post by Auctionedllama@gmail.com on 2009-02-21
The first command came back with 

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And yeah, it shows up. But when I select it, all I can change for volume is just the master. If I choose the second option (C-Media CMI8768 ALSA Mixer) it gives a bunch of volume controls.

---

### Post by markbuntu on 2009-02-21
Ok, it is basically working driver wise so your problem is just setting things up for multiple sound cards. 

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

You should also follow the directions in the **Sound Server Setup** here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Auctionedllama@gmail.com on 2009-02-21
I only have one soundcard though.

---

### Post by markbuntu on 2009-02-22
No, you have two. The ICH5 is the sound chip on the motherboard. That counts as one. The sound card makes two.

---

