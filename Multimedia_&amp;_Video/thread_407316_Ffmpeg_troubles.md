---
title: "Ffmpeg troubles"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by Manatherin on 2007-04-12
im using ffmpeg to try and convert a mpeg2 file to another format however whenever the conversions finished the video and sound are really out of sync, its like watching a terribly dubbed movie, ive tried different formats and tried doing it with the audio and video bitrates 100% identical but nothing works any ideas?

---

### Post by stonux on 2007-04-18
I already had this problem while playing video files from a
TV capture card.

Symptom: At beginning of movie, sound and image are
in sync, later it gets worse and worse. Images are faster
than sound.

This occurs when frames are dropped. If you can
re-capture the video (e.g. from a tape), try different
capture settings that reduce the number of dropped frames.

Otherwise try video editing software where you can cut
out sound snippets independant of the picture stream. 
I do not know whether kino can do that.

---

