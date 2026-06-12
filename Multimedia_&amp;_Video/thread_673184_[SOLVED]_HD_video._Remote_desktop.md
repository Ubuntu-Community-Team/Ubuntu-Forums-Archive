---
title: "[SOLVED] HD video. Remote desktop"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by Sceiron on 2008-01-20
Hello!

Im trying to  stream HD video from my Windows XP computer to my ubuntu laptop.
On the XP computer the viewing of HD material works just fine.
By using Remote Desktop i access my XP computer, and everything works perfekt.

But here's the problem:
When viewing HD material in remote desktop the players show only 1FPS or less.

When using wmp-classic i get this message:
"Media Player Classic could not render some of the pins in the graph, you may not have the neede codecs or filters installed on the system."   the movie starts but its "hicks" all the time.
I know ffdshow is not supported in linux. But i was kinda hoping it wold work if i ran rdesktop.

I have also tried VLCplayer, Mplayer. Here i get no error messages, but same low FPS so its not possible to view the movie.
Does anyone know if this is a codecproblem, or could it be a problem with streaming so much data over the network? (not using wireless network)
I think this is a codec problem.

Do i need to install the same codecs on my ubuntu-computer and my XP computer?'
I'm kinda new to linux, so need info on a basic level.
Thx for any help on this subjecct.

---

### Post by Sceiron on 2008-01-22
Kinda "solved" this by setting up a home network and sharing the actual video files.
By using this HOW-TO:
[http://ubuntuforums.org/showthread.php?t=558538&highlight=svn+ffmpeg](http://ubuntuforums.org/showthread.php?t=558538&highlight=svn+ffmpeg)
i now can watch HD in 720p atleast. When trying view 1080p the player tells me that the buffer size is to small or something.

But the original problem is solved...

---

