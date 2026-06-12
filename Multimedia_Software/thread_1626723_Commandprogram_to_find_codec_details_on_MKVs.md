---
title: "Command/program to find codec details on MKVs"
date: 2010-11-20
forum: Multimedia Software
---

### Post by dfresh4130 on 2010-11-20
I've been searching and haven't had any luck so far so I figured someone here's gotta know the answer to this.  I'm troubleshooting why some of my MKV files will play audio on my WDTV and others won't.  I'm suspecting it's got something to do with the audio codec inside the MKV.  However, I don't know how to view what codecs are being used inside the MKV.  Does anyone know of a good program or command I can run to view what's inside of the MKV?  Thanks

---

### Post by SeijiSensei on 2010-11-20
mplayer -identify /path/to/file.mkv

Most recent Matroska files use the H.264 codec, and many often use AAC or AC3 for the audio codecs.

---

### Post by dfresh4130 on 2010-11-20
Works great, thanks!

---

