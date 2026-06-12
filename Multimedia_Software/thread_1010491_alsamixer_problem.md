---
title: "alsamixer problem?"
date: 2008-12-13
forum: Multimedia Software
---

### Post by Roger Allott on 2008-12-13
I've read the instructions in LordRaiden's "Comprehensive Sound Problem Solutions Guide", but I'm a tad confused by the somewhat brief comments made about the use of alsamixer.

My core problem is that I'm getting almost no sound out of my laptop, and Rhythmbox has either hung or simply refused to play my mp3 files.

Anyway, here's what I think are my soundcards:

```
stuart@stuart-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Does that list look sensible and correctly installed?

OK, so then I move on to alsamixer. LordRaiden's article said that what I'd see here would be something similar to a graphic equaliser to adjust settings. Oh yeah?? You can perhaps understand my confusion with this screenshot:

[IMG]http://i476.photobucket.com/albums/rr122/Latrax/Screenshot-alsamixer.png[/IMG]

A graphic equaliser with just one slider???

What's more, I don't seem to be able to DO much in alsamixer. My up-down arrows adjust what I presume is the volume of this single channel, and well ..... that's it as far as I can tell!

What should I be seeing and has anyone got any ideas as to why I'm not seeing ten sliders as I had been expecting?

---

### Post by markbuntu on 2008-12-14
That guide is really overkill for most people's problems. Try this


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by Roger Allott on 2008-12-14
> **markbuntu said:**
> That guide is really overkill for most people's problems. Try this


[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Sir, you are a genius!

I've just rebooted my machine and I've heard the Ubuntu intro noise for the first time ever!

One little curiosity though. When it was shutting down it seemed to hang in what I presume is bios mode after the Ubuntu flash screen had finished. Then I got a message:

```
apcid:exiting
```

and then it switched off as normal.

Any idea what that means? It's the first time it's happened and I presume it's related to the adjustments I've made to sound cards etc.

---

