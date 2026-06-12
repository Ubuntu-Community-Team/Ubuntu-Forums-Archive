---
title: "alsa volume osd"
date: 2009-11-30
forum: Multimedia Software
---

### Post by kartoffel1337 on 2009-11-30
I'm running Ubuntu 9.10 on a Lenovo T400 with an external pcmcia soundcard (audigy2).
To get everything running the way I want I removed pusleaudio and replaced it with alsa.
So far it's is working fine, I set up shortcuts to control the volume and buttons that switch the .asoundrc depending on whether I want to use the internal or the external soundcard.

The only problem is that I don't get a visual feedback from the volume control buttons, because the the gnome volume applet only works with pulseaudio.
Did anybody find a way to get some kind of on-screen-display with alsa?

I wrote a script that uses notify-send to pop up messages about the current volume, but that's no use, every single message stays on the screen for a few seconds, so if I turn from 80 percent volume to 100 percent I have to wait about a minute until the last message disappears.

I also tried using the tpb package from the ubuntu repos.
Tpb was able to give me visual feedback of the mute button, but it doesn't seem to recognize the volume up and down buttons, tpb seems kind of old anyways.

This thread is not about the decision whether to use pulseaudio or alsa ;)
(I tried using pulseaudio and there is just no way to get lag free sound, on the fly switching between the soundcards, 5.1 sound, skype and flash to work with that at the same time, yet)

---

### Post by sisco311 on 2009-11-30
Try this script: [http://bbs.archlinux.org/viewtopic.php?id=69589]("http://bbs.archlinux.org/viewtopic.php?id=69589")

---

### Post by kartoffel1337 on 2009-12-01
great thanks, that solves my problem.

---

