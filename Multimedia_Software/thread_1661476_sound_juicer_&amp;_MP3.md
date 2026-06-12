---
title: "sound juicer &amp; MP3"
date: 2011-01-06
forum: Multimedia Software
---

### Post by oxo2oxo on 2011-01-06
I am sure that this is very simple but I have installed sound juicer and the gstreamer plug ins. The problem is i still cannot select MP3 as an output output option

---

### Post by oldfred on 2011-01-06
Did you look under edit, preferences? I always extrract to flac and then use sound converted to convert to mp3s on my mp3 player. I started to do this and it seemed like it copied the files faster than just copying the mp3 files with Nautilus.

---

### Post by Yellow Pasque on 2011-01-06
You either need gstreamer0.10-lame or gstreamer-fluendo-<something> (available from the partner repo)

---

### Post by samfuzz on 2011-01-07
delete or create (if not exist) a mp3 profile in your preference and create another one with this line for example :

audio/x-raw-int,rate=44100,channels=2 ! lamemp3enc name=enc quality=2 ! xingmux ! id3v2mux


preference of gnome audio profile  can be accessible via preference in soudjuicer or rhythmbox, or in command line interface : gnome-audio-profiles-properties

---

