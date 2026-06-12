---
title: "rhythmbox not loading playlist?"
date: 2010-05-30
forum: Multimedia Software
---

### Post by pythonscript on 2010-05-30
On Ubuntu 10.04, when I select Playlist -> Load From File and select a .m3u file in Rhythmbox, the playlist shows up but is totally blank. This is an m3u file exported directly out of windows media player 12 on a different computer, and when I open it with gedit, I can *see* all the tracks listed. Why is it blank? I've relied on this feature for almost two years and now it's suddenly gone!

---

### Post by pythonscript on 2010-05-30
¡maldita la hora! I momentarily forgot that Windows uses different file name syntax... A simple replace all fixed the problem of different slashes..

"Music\*song-name*" -> "/home/user/Music/*song-name*"

---

