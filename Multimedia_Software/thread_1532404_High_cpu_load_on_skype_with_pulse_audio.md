---
title: "High cpu load on skype with pulse audio"
date: 2010-07-16
forum: Multimedia Software
---

### Post by vangop on 2010-07-16
Hi,
just noticed that during calls skype uses ~30-50% cpu, + pulseaudio uses ~20%
I found some old threads on this like [http://ubuntuforums.org/showthread.php?t=1127056]("http://ubuntuforums.org/showthread.php?t=1127056")
Or [http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9]("http://www.howtoforge.com/how-to-fix-the-sound-issues-between-skype2.0-and-pulseaudio-on-fedora9")
The former suggests to purge pulse and use alsa/oss instead. The latter suggests changing mic in skype to DeviceXX and tweak the pulse.conf
There's also a launchpad bug on that with status Confirmed->invalid (due to "problem fixed in skype 2.1 beta") but looks like it's not (Im using 2.1 beta)
1. Does any1 has this problem?
2. I can't try 2nd link's approach as my skype has only PulseAudio in the settings, so I can't select Device or anything else!
3. Should I try to remove pulse in favor of ALSA? I'm pretty happy with pulse otherwise that this issue, I use it to record sound out of my sound card and I'm not sure if I can do this with alsa/oss.
Please advice :)

---

### Post by vangop on 2010-07-17
so anybody checked the cpu usage of skype/pulseaudio?

---

### Post by Nick Brohman on 2010-08-11
G'day vangop

Try this thread for possible solutions..

[http://ubuntuforums.org/showthread.php?t=886560&highlight=Pulse+cpu+usage](http://ubuntuforums.org/showthread.php?t=886560&highlight=Pulse+cpu+usage)

There are different solutions for the same problem.....the solution could be as simple as no sound or video running during the call, other than Skype.....disabling the 'Allow Skype to Set Your Levels" in the Audio options of Skype....

If video is the cause, you have to change your gstreamer-properties....it's all covered in the thread above.

BTW Pulse loves to use CPU, just run your music player and monitor, take note of levels when you start the Monitor, then play music....

---

### Post by slyboots on 2010-11-18
i have something similar. I am using skype with higher cpu usage. Also when i play audio the cupu usage is higher. I think it's a issue by the alsa driver.

---

### Post by freshmeatz on 2010-11-18
while in a session in skype I will use about 65% on one cpu and pulse will use about 20% off the other, once "sleeping" they will drop to like 1% and 4%

---

