---
title: "How can i rip audio from flash player?"
date: 2009-10-29
forum: Multimedia Software
---

### Post by hempa on 2009-10-29
Does anybody know how to rip audio from flashplayer?

---

### Post by Dynaflow on 2009-10-29
I would use Video Downloadhelper (look for it amongst the Firefox add-ons) to save the streamed video onto my hard drive, and then use Avidemux to separate out the audio channel.  Just set audio to save as MP3 (or whatever you prefer), open the saved video file, and hit "Save" in the "Audio" toolbar menu.

---

### Post by Andy Mack on 2009-10-29
mencoder a.flv -o a.mp3 -of rawaudio -oac mp3lame -lameopts cbr:br=192 -ovc copy

---

