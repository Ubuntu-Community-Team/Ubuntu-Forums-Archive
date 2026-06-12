---
title: "No audio after 9.10 upgrade"
date: 2010-01-27
forum: Multimedia Software
---

### Post by Eyore15 on 2010-01-27
I've upgraded my computer to 9.10.  There is no audio output.  I don't hear the quirky little sound when I boot up.  There is no playback of my music library using mplayer or vlc.  There's no audio from Hulu or the TV network's direct sites.  I've enabled pulse audio -- I found a reference to it in someone else's post.  Medibuntu is loaded and the codecs downloaded.

Anyone have a suggestion I can try?

tnx

mcm

---

### Post by lindsay7 on 2010-01-27
look under system/preferences/sound and make sure that the mute box is not checked

---

### Post by Eyore15 on 2010-01-27
> **lindsay7 said:**
> look under system/preferences/sound and make sure that the mute box is not checked

sound is not muted,

---

### Post by efflandt on 2010-01-28
Which kernel are you running (**uname -a**)?  If still running the old .28 kernel instead of the new .31 one, you will have no sound.  In Sound Preferences, what shows up in Hardware and Output tabs?

---

### Post by arcticmagnolia on 2010-01-29
ok, I take that back, everything works now (don't know what just happened)

---

