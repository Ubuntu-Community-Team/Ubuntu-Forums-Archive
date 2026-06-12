---
title: "Sound working in applications but not in Gnome"
date: 2009-02-24
forum: Multimedia Software
---

### Post by MatthieuM on 2009-02-24
Hi !

I've got a weird problem... My SoundBlaster Live seems to be correctly installed, as the sound is working in applications like Amarok ou Audacity, but it doesn't seem to work in Gnome !
When I go into System/Preferences/Sound, every options in the sound playback drop down menu are OK (the test gives me a Sine sound) ; when I go into the Sounds tab, and I click on the play button near Alert Sound I hear the "thump" ; but when I open, for example, the Text Editor, and hits the backspace key in an empty file, all I hear is the internal PC speaker beeping.

If someone could tell me what I've done wrong...

Thanks !

---

### Post by arepaking on 2009-02-24
Hi Matthieu,
I happen to have the same issue than you a few minutes ago. This is how I resolved it.

Go to your terminal and run the following command:
```
alsamixer
```

Then press "M" . This is for Mute or Unmute the sound. For some unknown reasons mine got Muted.

Hope it helps!

---

### Post by MatthieuM on 2009-02-24
Hi arepaking !
I tried alsamixer, but it didn't solve it. It wasn't muted I guess...

The really strange thing is that sound is working otherwise, I just don't have login/logout sound, or any other system sound for that matter...

---

