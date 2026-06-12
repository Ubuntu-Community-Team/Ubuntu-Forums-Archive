---
title: "No sound in Intrepid, tried everything."
date: 2009-01-18
forum: Multimedia Software
---

### Post by Aiffe on 2009-01-18
I recently installed Intrepid via Wubi. Yes, I'm a big fat n00b. Everything's been great except for the lack of sound. I did the obvious things first, checked alsamixer to make sure nothing was muted, checked the groups to make sure I had the right permissions. Then I went to google, and followed approximately eight billion guides for how to fix pulseaudio, how to get rid of pulseaudio and just use alsa, then purged pulseaudio and alsa, reinstalled, and tried some more. It's entirely possible that all my tinkering is the reason I can't fix this, and to be honest, I don't remember everything I've tried. All I know is I'm about ready to pull my hair out.

By the way, sound works great on Windows, so it's not a hardware issue.

lspci says I have:

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)

and aplay -l returns:

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I throw myself onto your mercy, Ubuntu Forums. I don't care if it's pulseaudio or alsa or a tiny leprechaun that sits under my keyboard making noises, I just want sound.

---

### Post by bradwal on 2009-01-19
I have the same sound card and I've been trying to get my sound to work for the past 2 weeks since install too. PM me if you figure out a fix, I'll do the same.

---

