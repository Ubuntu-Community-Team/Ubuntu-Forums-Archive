---
title: "Karmic Sounds or Silence"
date: 2010-03-18
forum: Multimedia Software
---

### Post by SeanMc98 on 2010-03-18
(Previously posted in "Absolute Beginner" forum)

I have installed **Karmic** on a desktop and a laptop.  The desktop has a sound card (**Ensoniq**) and speakers, while the laptop has only the integrated sound controller and the **PC speakers**.  The desktop has full (and wonderful) sound, but the laptop is **silent**.

The laptop has sound on **Windows** and **SUSE *11.2***.  After researching, I followed the article [http://drowninginbugs.blogspot.com/2...io-in-910.html]("http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html") and the thread [http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019) without success.  After further reading, I am of the impression that the **PC** speaker sound does not function under **Karmic**, and the resolution is sometime in the future.

Is this a fair statement for **PC** speaker sound ?  This cannot be resolved by adding a sound card, as the laptop has an integrated sound controller for the **PC** speaker(s) as well as the external jacks (mic, headphones and external speaker(s)). I can wait for sound, though I do not wish to spend time now on a problem that cannot be resolved.

---

### Post by dino99 on 2010-03-18
Sound is often an issue, but try to use info you still have:

- look at /var/crash if any
- open system - admin - log viewer : is there any complaint about sound driver or sound hardware

go to system - pref - sound: are the settings good (ie analog), watch the hardware tab: you might have a device, if not that mean your sound hardware is not found. On other tab be sure sound is unmute .

- run alsamixer and tweak sound levels as you want , specially output line and speaker.

- are you using pulseaudio ?
if so:
gksudo gedit /etc/pulse/default.pa 
gksudo gedit /etc/pulse/client.conf
gksudo gedit /etc/pulse/daemon.conf
gksudo gedit /etc/init.d/pulseaudio

see in each of the above's that needed lines are not commented 

what return: aplay -l
that will give you the real sound hardware name, then you can search on google: karmic+"that name"

you can find some good info there:
[http://forums.debian.net/viewtopic.php?f=16&t=12497&sid=666eef3840e114a52f52209b12913ba3&start=30](http://forums.debian.net/viewtopic.php?f=16&t=12497&sid=666eef3840e114a52f52209b12913ba3&start=30)

---

### Post by linxuser14 on 2010-03-20
The sound of silence. I'm searching an trying to resolve this too. But thanks for the audio trigger. I haven't heard that song for years and right now its playing in my mind in detail. Thank you.

---

