---
title: "Sound problem"
date: 2008-11-15
forum: Multimedia Software
---

### Post by risotto77 on 2008-11-15
I have problem with sound here on a new 8.10 install. I am not really sure where the problem is, pulse-audio or alsa or somewhere else. I usually have no problems with this card (terratec EWS88 MT , using ice1712 alsa driver), but never used pulse-audio before.

I do get system sounds ( like when gdm loads, and det "savanna" intro when loading Gnome).

But when playing music files I get problem. Playing a flac music file with Totem make it hang, and I have to kill Totem. Trying with aplay I get white noise whatever rate and formats I am trying.

Trying the test feature under preferences-sound (where I have pulse-audio)I get:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

Thanks for any help

Edit:
I have installes/removes some software following the  "Comprehensive Multimedia & Video Howto".  
I can play music files now usin vlc and alsa-output, But Totem and Rhythmbox still do not work

---

