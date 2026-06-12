---
title: "[help] having weird sound problems"
date: 2008-05-02
forum: Multimedia Software
---

### Post by psychofish25 on 2008-05-02
I'm running 8.04 and I have noticed some differences. Now, my music crackles from time to time and sounds messy and also, pidgin will not make sounds while my music is open. Under pidgin I am running aplay %s for sound which works, except when I play music. Under Preferences->Sound I am running everything on OSS, is there something I should do? I tried PulseAudio and ALSA but I still have those problems. I have posted this before but got no response. Someone please help.

Thanks,
Jordan

---

### Post by psychofish25 on 2008-05-02
(bump)

---

### Post by psychofish25 on 2008-05-04
can someone please help me?

---

### Post by kmsiwiec on 2008-05-12
Hi,

Had the exact same problem. The moment 8.04 came out, I upgraded to it from 7.10 through the update manager. Since then there was always a little bit of accompanying noise whenever I played audio of any sort: mp3, movies, flash on Youtube, you name it (I also had Pidgin default sounds snapping a little bit). I tried different players, twiddled with Pulse and Alsa settings, tweaked with a couple of plugins - only to revert back to previous config; nothing worked. Until yesterday.

I thought I'd have a go at UbuntuStudio just for the glee of having all the extra stuff it comes with - so I upgraded once more. I guess it must've overwritten some library that got corrupt during my earlier transition from Gutsy or pulled along a missing bit of configuration. Whichever the case, my sound is back to normal and I don't get the background noise anymore - though Pidgin beeps still come out somewhat broken, but that hardly bothers me.

If you've too much free time (plus around a Gig of free space for the installation cache and the actual data) I urge you to try Ubu Studio (that is, as long as you're on vanilla Ubuntu and not Studio already). You can move to it by:

```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-image-rt
```

as described in [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy").

If you by wish or prejudice would prefer to only pick some of the components, just knock the rest off that list. Heck, you might even go hunting for individual sound-related packages and their dependencies (all listed here: [https://wiki.ubuntu.com/UbuntuStudio/PackageList]("https://wiki.ubuntu.com/UbuntuStudio/PackageList")), but I cannot vouch for that, I went for the whole bundle; did me no harm, got a stupendous number of specialist apps to play with if I ever desire to and a killer optional theme (if you like dark ones).

Good luck.

Chris

---

