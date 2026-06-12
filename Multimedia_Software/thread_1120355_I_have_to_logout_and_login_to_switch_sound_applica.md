---
title: "I have to logout and login to switch sound applications"
date: 2009-04-08
forum: Multimedia Software
---

### Post by bobdobbs on 2009-04-08
Hi all.
It seems that my desktop system, running ubuntu 8.10, requires me to log out and then log back in, if I want to a different application to use sound.
For example, if I'm listening to music via mpd or amarok, I can't listen to sound from the flash player.
And I can't switch between mpd or amarok without going through the same dance.

System info:
aplay -l outputs:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

I've read various posts that say to switch between sound subsystems. But I get the same result with pulseaudio, alsa and oss.

The sticky sound configuration document says that the problem can be remedied by using alsa-oss. However, configuring this is a pain, and this technique will only work for some applications on some systems.

I have tried passing options to the sound modules. This seemed to fix the weird sounds that I was getting upon login, but still, I cannot switch between apps.

What is the actual problem here?
How do I go about fixing it?


Thanks

---

### Post by markbuntu on 2009-04-09
DId you try this?

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by bobdobbs on 2009-04-09
> **markbuntu said:**
> DId you try this?

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Hi Mark.

I seem to remember having gone through that document before, maybe a few months ago on one of my attempts to fix sound issues.

Nevertheless, I've gone through it again, making sure that my system is configured according to the documents instructions.

And... success!
At least for the moment anyway.
In my experience, I have fixed sound issues, only to have problems re-emerge and settings mysteriously 'unset' later.

Anyway, I've tested by playing music and video via mpd, amarok and flash on two different browsers, leaving the apps open, pausing and switching apps, playing through different apps at the same time.

And everything seems to work without problem so far.

Thanks for directing me to that document.

I won't mark this thread as solved for the moment though.
I'll wait for a while to see how things go.

Cheers.

---

### Post by markbuntu on 2009-04-09
If you start with a clean install and follow that guide and it works you will not have any problems in the future until you start fooling around again with your sound settings. That is the very short version of this

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

