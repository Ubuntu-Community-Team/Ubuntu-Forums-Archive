---
title: "[SOLVED] Login sound plays twice"
date: 2007-07-26
forum: Multimedia &amp; Video
---

### Post by mdebusk on 2007-07-26
What could cause the login sound to play twice?

I have several problems with sound on my Feisty Fawn setup. Examples: invoking aplay with a WAV file causes it to sit there, as if waiting for input, until I cancel it; DVDs will freeze as soon as the player (any player I try) attempts to play a sound; and any game that has sound will simply not start (I miss Frozen Bubble!).

I can play mp3s via BEEP or in Audacity just fine, and timidity plays MIDI files perfectly. This just adds to the mystery.

I suspect that something is happening at boot that is causing this, and that thing is causing the boot sound to play twice. If I can solve that, I hope all the other problems will go away.

I'd appreciate any ideas on how to go about this. Thanks.

---

### Post by jamieh on 2007-07-28
Change the sound, does it play twice, or the old one then the new one?

---

### Post by mdebusk on 2007-07-28
> **jamieh said:**
> Change the sound, does it play twice, or the old one then the new one?

I'm rather new at Linux, though I've used OS/2, various versions of Windows, and DOS. I don't know how to change the sound without the GUI, and I can't get the GUI to work either. (Sheesh... I wish I knew what I did to cause all this.) Which config file do I edit to remove the sound?

(I'm tempted to reinstall.)

---

### Post by mdebusk on 2007-07-31
> **mdebusk said:**
> 
I suspect that something is happening at boot that is causing this, and that thing is causing the boot sound to play twice. If I can solve that, I hope all the other problems will go away.


I sort of solved this. I still have all the other problems I mentioned, but my startup sound no longer plays twice. It plays once, and now the little drumroll when GDM comes up also plays. (I hadn't even noticed that it didn't play, as I'd forgotten about it.)

I was searching through every directory looking for any file with the word "sound" in the name and came across /etc/sound/events/gnome-2.soundlist . I found that it contained entries for all system sounds. I opened it with vim and removed any filenames I found. I expected no startup sound at all. I got one startup sound, as I mentioned in the first paragraph.

---

