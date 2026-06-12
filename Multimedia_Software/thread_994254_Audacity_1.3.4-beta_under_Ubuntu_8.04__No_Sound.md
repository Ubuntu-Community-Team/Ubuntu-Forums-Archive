---
title: "Audacity 1.3.4-beta under Ubuntu 8.04  No Sound"
date: 2008-11-26
forum: Multimedia Software
---

### Post by LarryJ2 on 2008-11-26
If after importing a known good sound file into Audacity, you see the output level meter's green indicator jumping in sync with your wave form, but you still get NO sound from your speakers,  try this.

With Audacity running,   ( Apps->Sound and Video->Audacity)  open a terminal and issue this command.

```
killall jackd
```

On my system using the MB's Realtek ALC885 sound chip with ALSA, the tests provided in the gnome  System->Preferences->Sound  test Playback etc  all worked ok.  It was just Audacity that refused to produce a sound.

This solution is referenced here:

[http://audacityteam.org/forum/viewtopic.php?f=18&t=128&st=0&sk=t&sd=a&sid=b944e0c0193f8d4e7e1626217c57f1d4&start=10](http://audacityteam.org/forum/viewtopic.php?f=18&t=128&st=0&sk=t&sd=a&sid=b944e0c0193f8d4e7e1626217c57f1d4&start=10)

and again here:
[http://audacityteam.org/forum/viewtopic.php?f=18&p=16503#p16503](http://audacityteam.org/forum/viewtopic.php?f=18&p=16503#p16503)

A symptom of this problem inaddition to no sound from Audacity when playing back your file is that  Edit -> Preferences takes about twenty seconds to display and  if you open audacity in a terminal,  you'll see error messages perhaps similar to:

Expression 'ret' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1034
Expression 'AlsaOpen( hostApi, parameters, streamDir, &pcm )' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 1066

Also  if you don't issue the  "killall jackd" command,  Audacity will post the following error message
> 
Error while opening sound device. Please check the output device settings and the project sample rate.

Apparently the "jackd" daemon was installed when I tried out Ardour by installing it from the repository.  Through synaptic,  I removed jackd   and  ardour,   the problem referenced above disappeared.    As far as I can tell now,  after removing "jackd" and "ardour",  I do NOT have to issue the  "killall jackd"  command.       Good grief!

---

### Post by vajorie on 2009-09-20
> 
```

killall jackd

```


thank you! (I know it's been about a year, but...)

:)

---

