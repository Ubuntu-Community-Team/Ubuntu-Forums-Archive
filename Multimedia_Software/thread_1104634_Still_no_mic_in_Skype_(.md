---
title: "Still no mic in Skype :("
date: 2009-03-23
forum: Multimedia Software
---

### Post by stardustdk on 2009-03-23
Hey all.

Found this howto/guide and it didn't work at all :(.

> [http://ubuntuforums.org/showthread.php?t=789578&highlight=Skype+microphone+Hardy](http://ubuntuforums.org/showthread.php?t=789578&highlight=Skype+microphone+Hardy)

Anything else works in Ubuntu Hardy (I386).

Have installed Skype-static from medibuntu.org.

Have no internal mic in laptop.


Any suggestions?

Best regards

Stardustdk

---

### Post by markbuntu on 2009-03-24
Does your microphone work at all?
If not then get that working first. You can go here for basic troubleshooting help. There is also a link for getting Skype working but you need to get your mic working first. If you are using a hda sound chip then go to the Drivers/HDA sound chips section for help. Follow the links


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by stardustdk on 2009-03-24
My microphone works, yes. 

aplay -l shows this:

 > aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


What now? I have read your link.

Best regards

---

### Post by markbuntu on 2009-03-24
Ok then, I will assume that you have followed all the directions here and are using Hardy 8.04. Results are different if you are using Intrepid.

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

In the Pulseaudio volume control/input devices and /output devices you need to choose the ALC 883 as the default device by right clicking on it.
In Skype/Options/Sound Devices you need to choose pulse. You may need to close skype and restart for this to work.

This worked for me with my ALC883.

---

### Post by stardustdk on 2009-03-24
That did the trick :).

Thanks 

Best regards

Stardustdk

---

