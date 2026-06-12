---
title: "no sound from 3gp files"
date: 2007-08-25
forum: Multimedia &amp; Video
---

### Post by vishzilla on 2007-08-25
when i play 3gp files transferred from my cell phone, i dont hear any audio...i do get the video.
i dont seem to find the solution in the forums

---

### Post by luisromangz on 2007-08-25
The default ffmpeg in Ubunto doesn't like the amr sound codec that is used in the 3gp file format.

I found some solutions in google, but I ended using the programa Mobile Media Converter (google for the download page) to convert them to mpeg files. This program ships with its own binary version of ffmpeg, compiled with amr support, so it doesn't have problems managing 3gp files.

---

