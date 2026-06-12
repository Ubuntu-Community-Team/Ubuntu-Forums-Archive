---
title: "Amarok locks audio device"
date: 2008-04-29
forum: Multimedia Software
---

### Post by dkrig on 2008-04-29
Hello.

On this weekends I upgraded my Ubuntu from 7.10 to 8.04 and audio device problem appeared.

The problem is:
When Amarok plays some music it locks audio device, so Kopete does not play audio notifications (audio notification on new message arrival) and when I open some video in MPlayer error message displayed "Could not open/initialize audio device -> no sound.". But when I pause playback - all sounds come back - either Kopete and MPlayer.

The same thing happens with Exaile.

When MPlayer plays video Kopete plays sounds but Amarok just hangs up, so to continue listening to music I have to close MPlayer, close Amarok, open Amarok and play music.

Please help me to solve this problem.
Thanks.

---

### Post by spidermagicat on 2008-09-25
I also have this problem when using aMSN and amarok

---

### Post by markbuntu on 2008-09-25
The first thing you can try is in System/Preferences/Sound change everything to ALSA instead of autodetect. Different applications use different sound servers, some use alsa, some use OSS, some use Pulse Audio. When Sound is set to autodetect, the application grabs the sound server all to itself. Setting to ALSA forces all applications to use alsa for the sound server and prevents a lot of these conflicts.

For a more involved and comprehensive solution, you can look in my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

