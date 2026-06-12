---
title: "How to mix music audio and voice(which programms can do this)?"
date: 2008-07-24
forum: Multimedia Software
---

### Post by inhibitor on 2008-07-24
Sorry for my bad english...I tried to record voice with gnome-sound-recorder 2.22.0. Can I mix music and my voice in recording process with gnome-sound-recorder 2.22.0 or another media programm and how do this? May be I can redirect audio stream from audio device to input device, I mean something like this: cat /dev/audio > /dev/[input]? Please, help me.

---

### Post by prshah on 2008-07-24
> **inhibitor said:**
> Sorry for my bad english...I tried to record voice with gnome-sound-recorder 2.22.0. Can I mix music and my voice in recording process with gnome-sound-recorder 2.22.0 or another media programm and how do this? May be I can redirect audio stream from audio device to input device, I mean something like this: cat /dev/audio > /dev/[input]? Please, help me.

If you don't mind a two step process, you can use Audacity from the repositories to do this; first, create your voice track, then import the music track in Audacity, and then import your voice track, then merge the two by choosing export to MP3/flac/whatever.

Audacity is easy to use; install it and give it a try!

I'm sure that there's a single step process too; don't know what it is though.

---

### Post by inhibitor on 2008-07-25
Thanks a lot!

---

