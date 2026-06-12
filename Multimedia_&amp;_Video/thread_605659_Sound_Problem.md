---
title: "Sound Problem"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by jondecker76 on 2007-11-07
Hello,

I have an M Audio Delta 1010 and haven't had a single sound problem until now.

I can not get sound out of Mednafen (emulator) no matter what I try.
(Please see related post at [http://http://ubuntuforums.org/showthread.php?t=605012]("http://http://ubuntuforums.org/showthread.php?t=605012")

there is always an error opening the audio device (either No suck file or directory, or Device or resource busy).

I am trying to use Mednafens -sounddevice option, but what format should the option be in to be alsa compliant?  Ive tried:
-sounddevice "hw:0,0"
-sounddevice "ALSA:hw:0,0"
-sounddevice "default"

Am I on the right track?  I can't figure out why EVERYTHING else works for me when it comes to sound, but not this..

thanks,

Jon

---

### Post by Mednafen on 2007-11-08
Try sexyal-literal-default as the device.

---

### Post by jondecker76 on 2007-11-08
Yes! I have sound!

One thing though... Looking at the terminal, i noticed:

```

 Initializing sound...
  Using "ALSA" audio driver with device "sexyal-literal-default":ALSA Warning:  Could not set period size to a nice value. :(


```

Is this something I need to worry about? Is there a ways for me to manually set the period size?

thanks

Jon

---

