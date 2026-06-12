---
title: "sound not comming out of headphone sony vgn-n320e"
date: 2008-09-26
forum: Multimedia Software
---

### Post by discord on 2008-09-26
I tried to follow the instructions on the thread below, before my problem was that I had sound comming out both the speakers and the headphones  when i only wanted sound out of the headphone. After following the instructions I am unable to change the volume for the headphones in alsamixer. I see the headphones and can mute and unmute them but I cannot add volume. I just want to be able to use my speakers but plug the headphone in and have them mute, like it should work.

[http://ubuntuforums.org/showthread.php?t=780029](http://ubuntuforums.org/showthread.php?t=780029)

I tried all the alsa-base modprobe options. 
Right now I am trying options snd-hda-intel index=0 model=vaio. Still no luck when I restart alsa

I also tried running the alsaconf.sh script. no luck. I have a Sony VGN-N320E. 

colin@crystal:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC262 Digital [ALC262 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by markbuntu on 2008-09-26
If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

Here are a few more threads about hda sound chips:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

---

### Post by discord on 2008-10-01
thanks mark,

the assamd option i choose wasn't listed in the other forums i tried. It worked after reboot but not after an alsa restart.

---

