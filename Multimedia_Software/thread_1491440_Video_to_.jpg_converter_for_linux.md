---
title: "Video to .jpg converter for linux"
date: 2010-05-23
forum: Multimedia Software
---

### Post by Gemu on 2010-05-23
I'm looking for a way to capture pictures from videos. Does anyone have any idea. I understand there is a free program for Windows that does just that but I want to use Linux if I can.

---

### Post by sharath.puranik on 2010-05-23
I think VLC has capture screenshot option, not sure though, try it.

---

### Post by dtfinch on 2010-05-23
This seems to work for me:
ffmpeg -i videofilename.ext out%4d.png

If you need just a few frames,you can use -ss to specify the starting second, and -t to specify duration in seconds. like "ffmpeg -i videofilename.ext -ss 10 -t 1 out%4d.png"

---

### Post by Gemu on 2010-05-23
> **sharath.puranik said:**
> I think VLC has capture screenshot option, not sure though, try it.



 Thanks I've found now that Kino does the trick simply by pausing the vid and hitting the save still frame button.

---

### Post by alphacrucis2 on 2010-05-23
> **Gemu said:**
> Thanks I've found now that Kino does the trick simply by pausing the vid and hitting the save still frame button.

Another way for any video player that lets you pause. Just hit print screen when paused.

---

### Post by Gemu on 2010-05-24
> **dtfinch said:**
> This seems to work for me:
ffmpeg -i videofilename.ext out%4d.png

If you need just a few frames,you can use -ss to specify the starting second, and -t to specify duration in seconds. like "ffmpeg -i videofilename.ext -ss 10 -t 1 out%4d.png"


Thats awsome! I wish I new every command there is to know. The front part of that command I suppose has to be changed to whatever video format your using. I was trying to grab some pics from a .flv for instance.

---

