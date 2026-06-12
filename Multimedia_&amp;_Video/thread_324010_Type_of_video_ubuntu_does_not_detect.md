---
title: "Type of video ubuntu does not detect?"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by feardotcom on 2006-12-23
Ok heres the deal, i got some video downloads, the file names has "hdtv.xvid.lol" in it, and its xvid, but why wont any of the movie players detect it, i look at the properties and under the "audio/video" tab, in sub cats of general and audio, everything says "unknown" i have all the codecs i could possibly find, i can play all of my movies except these few, cansomeone please help me? i dont understand why the file is doing this.](*,) ](*,) ](*,)

---

### Post by 3rdalbum on 2006-12-23
If it's an xvid, why does it have ".lol" at the end? Something like that would immediately make me suspicious - often Windows trojans have a name like "angelinajolienude.jpg.exe", because the user won't see the ".exe" on the end; the user will assume that it's a JPEG.

---

### Post by pay on 2006-12-23
Read this [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Lord Illidan on 2006-12-23
The .lol at the end also makes me suspicious. It might not be a video file at all.

---

### Post by pay on 2006-12-23
lol is the guy that ripped the video. Like here [http://www.torrentspy.com/torrent/861896/Family_Guy_S05E02_PDTV_XviD_LOL_Mother_Tucker](http://www.torrentspy.com/torrent/861896/Family_Guy_S05E02_PDTV_XviD_LOL_Mother_Tucker)

---

### Post by Lord Illidan on 2006-12-23
Then why not rename it, leaving the .lol part out.

---

### Post by feardotcom on 2006-12-23
no, its a AVI file, its just part of the file name has "hdtv.xvid.lol" in it, for example, "dell.commercial.hdtv.xvid.lol.avi"


EDIT: and i already went through the restricted formates page, and i did rename it to just a plain "name.avi" and it still wont play

---

### Post by pay on 2006-12-23
If you have mplayer installed, try playing it with ```
mplayer /path/to/name.avi
```and then it will give you some information about the video.

---

