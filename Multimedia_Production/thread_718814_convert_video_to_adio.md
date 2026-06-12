---
title: "convert video to adio"
date: 2008-03-08
forum: Multimedia Production
---

### Post by lauraeznag on 2008-03-08
convert video to adio 

--------------------------------------------------------------------------------

how do you convert a dvd or mp4 to adio
is their a program for this ?
__________________

---

### Post by Creative2 on 2008-03-08
video to audio ?
ffmpeg -i INPUT  -vn   -ab 128k -y OUTPUT.mp3
ffmpeg -i INPUT  -vn  -ab 128k -y OUTPUt.ogg
ffmpeg -i INPUT  -vn  -ab 128k -y OUTPUT.flac
ffmpeg -i INPUT  -vn  -ab 128k -y OUTPUT.ac3

---

