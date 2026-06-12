---
title: "MPlayer and USB audio"
date: 2008-11-18
forum: Multimedia Software
---

### Post by tomcant on 2008-11-18
I just installed MPlayer on my laptop as an alternative to Totem because I like the audio/video synchronisation feature it provides. I use ALSA to play sound from external speakers via a USB device (Edirol UA-5). When I open a file in MPlayer the file plays seemingly fine, however an errant message box flashes on the screen about five times a second with the message:```
[AO_ALSA] Unable to find simple control, 'PCM',0
```This isn't the usual case of the problem, however, since switching to use the Pulse audio drivers doesn't output to the USB device. The sound comes straight from the laptop speakers when using Pulse. I need a way of preventing that error message from appearing whilst also outputting sound to the USB device.

I'm running Hardy, if that helps. Any help would be appreciated.

Thanks,
Tom

---

### Post by markbuntu on 2008-11-19
If you use the Pulseaudio Volume Control, pavucontrol, you can change your audio streams to any device that alsa can use. If you do not have pavucontrol, you should get it. For more comprehensive help on getting your sound dialed in go here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

You can skip over the troubleshooting parts and start at the Sound Server setup section.

---

### Post by tomcant on 2008-11-19
Thank you, I will have a go and post back here if I run into any troubles.

Thank so much,
Tom

---

### Post by tomcant on 2008-11-19
That worked brilliantly. Thanks so so so much.

Tom

---

