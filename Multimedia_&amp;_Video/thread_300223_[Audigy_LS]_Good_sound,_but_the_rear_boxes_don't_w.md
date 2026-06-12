---
title: "[Audigy LS] Good sound, but the rear boxes don't work"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by mhueting on 2006-11-15
My soundcard is a Creative Audigy LS (I know, not the best sound card in the world, but hey, it's 5.1), and it works great, except for the fact that my rear boxes don't seem to work. But if I do a simple "speaker-test -c6 -D plug:surround51", the rear boxes work like a dream.

So I'm curious: Why do my rear boxes work when I'm testing, and not when I listen to music in Amarok, or when I hear the startup sound for Edgy?

I'm quite amazed :-? :confused:

---

### Post by Phoenix128zx on 2006-12-19
Hello! I've just solved the problem under Ubuntu Edgy, it was the same problem I had under Suse!
Open the default Gnome volume panel, go to edit/preferences and activate those:
PCM Front
         Surround
         LFE
         Center
Then:
          Front
          Surround
          LFE
         Center

You could also enable microphone recording and a very simple equalization(Bass&Treble only).
Now close, pimp up Front,Surr.,LFE, Center volume and enjoy!!

---

