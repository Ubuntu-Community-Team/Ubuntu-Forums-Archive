---
title: "When Firefox runs, other apps can't play sound (and vice versa)"
date: 2009-10-31
forum: Multimedia Software
---

### Post by Kymus on 2009-10-31
Here's the basics: When I run Firefox, sound in Firefox is fine (YouTube, MegaVideo, Pandora, Hulu, etc. etc.) but sound will not work when I try to play something in VLC or Amarok (for example). Now, if I play music in Amarok, then load Firefox, then I will get no sound in Firefox but music will play fine in Amarok.

System Info:
Ubuntu 9.04
on-board sound from Foxconn NFUK8AA
Firefox v3.0.14

---

### Post by beastrace91 on 2009-10-31
Do you have pulse audio enabled? It should be the default in 9.04 but double check your settings in your sound manager to make sure this is the case as it is needed to get audio from multiple applications at the same time.

~Jeff

---

### Post by Kymus on 2009-10-31
Unless I'm seriously misunderstanding something (which is quite possible), I've set it to PulseAudio and the same problem persists (maybe I need to exit out of firefox and then load it again and then try?)

I checked the sound preferences, and basically everything was at Auto Detect save for Sound Capture (*nvidia CK804 with ALC850 ALSA*). Also, the device for the Default mixer tracks is set to *monitor of nvidia CK804 with ALC850 (PulseAudio Mixer)*.

I changed all the auto-detects to PulseAudio Sound Server, closed sound preferences, loaded Amarok and VLC (while Firefox was open) and nothing. Audio was still fine in Firefox.

This may or may not be notable, but, under each option (save for Default Mixer Tracks) there is a listing of *nvidia CK804 with ALC850 (ALSA)* and *nvidia CK804 with ALC850 (OSS)*, but no *nvidia CK804 with ALC850 (PulseAudio)*.

---

