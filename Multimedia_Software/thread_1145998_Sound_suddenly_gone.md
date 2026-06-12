---
title: "Sound suddenly gone"
date: 2009-05-02
forum: Multimedia Software
---

### Post by hackapelite on 2009-05-02
That's all. I tried playing music videos on youtube, nothing. I tried Amarok, and no song would play - the playlist would just start looping as if it was attempting to play the tracks but none of the songs actually started. MPlayer would freeze when I try to play a video on it.

This happened all of sudden - no changes to the system have been made recently. Also, when I go to sound preferences and hit "Test" on sound playback, it comes up with the following error message:

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argumentThen, it freezes and I have to force quit.

Also, I think Amarok came up with some kinda error message and I caught the word "xine"...

I'm stomped. What's going on?

OS is Ubuntu 8.10, I'm on integrated audio that comes with the ASRock AOD790GX/128M motherboard.

---

### Post by xc3RnbFO8P on 2009-05-02
Go to System/Preferences/Sound and try to switch everything to ALSA from auto-detect.

---

### Post by hackapelite on 2009-05-02
Everyone was set to auto-detect, but thanks anyways - another restart fixed the problem (I already restarted once and it didn't do it, so I assumed that another reboot wouldn't help, but tried anyways).

---

