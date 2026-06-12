---
title: "Switching sound output without closing apps"
date: 2009-02-12
forum: Multimedia Software
---

### Post by clanmackay on 2009-02-12
Hello,

I switch between two audio devices for playback:

```
joshua@thoreau:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I can do this through System -> Preferences -> Sound, but the switch does not take effect in apps unless I close everything I can think of that uses the sound card (at the very least, Totem and Skype) and restart.  When I restart them, they use the new choice.

My question, of course, is how to perform this change in such a way that *open* applications will switch over -- if this is possible.

I am on Intrepid using ALSA.  I have read *Comprehensive Sound Problem Solutions Guide v0.5e*, and if the answer is there, then I do not understand my question well enough.

Thanks in advance.

---

### Post by markbuntu on 2009-02-13
Pulseaudio will do that for you easily. Use the Pulseaudio Volume Control (pavucontrol). There is more info about setting that up here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

and more info than you need here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

ALSA itself has no easy way to move streams on the fly like with pulseaudio.

---

### Post by clanmackay on 2009-02-13
*Marvelous*.  Thank you.

One bit of the guide I found hard to follow was the instruction to "Move Stream".  If any other neophytes are struggling, the way to find this option is to left-click on the Pulseaudio icon in the system tray, as indicated, then "Volume Control".  There is a down-arrow to the far right of every playback stream.  Click on this, and you then have the option to "Move Stream".

Thanks again.

---

