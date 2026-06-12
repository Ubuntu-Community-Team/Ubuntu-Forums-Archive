---
title: "KAudioCreator Not Cooperating"
date: 2006-10-16
forum: Multimedia &amp; Video
---

### Post by Dark Matter on 2006-10-16
I'm trying to change the ogg encoder settings for KAudioCreator, but no matter what I set it to, everything gets encoded at an average bit rate of 112 kbps.

I tried use the quality based encoding option (setting things to quality 6), but KAudioCreator encoded it at 112 kbps.  I then changed it to bitrate based encoding, setting the average bitrate option to 192 kbps.  KAudioCreator didn't seem to care.

Does anyone know what's going on here and how I might be able to fix it?

---

### Post by jeremy on 2007-01-06
This works for me...

oggenc -q6 -o  %o --artist %{artist} --album %{albumtitle} --title %{title} --date %{year} --tracknum %{number} --genre %{genre} %f

---

