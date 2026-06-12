---
title: "ffmpeg and removing noise"
date: 2007-12-11
forum: Multimedia Production
---

### Post by Dafydd on 2007-12-11
I use ffmpeg to convert radio I listen to (vsound dumps a AU file).

Unfortunately, there are occasionally interruptions and realplayer gives a high skreaky sound.

Is there any way I can automatically remove that? Or limit the strength of such sounds?

Thanks
Dafydd

---

### Post by stmiller on 2007-12-12
Open the audio file in Audacity and edit away...

---

### Post by Dafydd on 2008-02-09
that's what i have been doing, but it is time consuming...

---

### Post by Creative2 on 2008-02-09
to remove noise you must give , to a program , for example sox, a profile , if you can do that easly you should do this : (i think is a bit difficult):
1 extract audio track----------------------------------------------; denoise audio track; put audio into video.

ffmpeg -i INPUT  -vn -acodec mp3 -ab 128k -y /tmp/my.mp3 ; sox "something" ;ffmpeg INPUT -newaudio soxoutput  OUTPUTVIDEO

---

