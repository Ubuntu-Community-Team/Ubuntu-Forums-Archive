---
title: "Script to generate video playlist"
date: 2016-03-01
forum: Multimedia Software
---

### Post by mrmrva on 2016-03-01
Struggling with the entire day but not working. Need a script to generate playlist of video files from a folder. Tried this
> cd /your/folder/
find . -name '*.mp4' > playlist.m3u

and similar variants but mplayer (vlc also) wont play such file.
Any help appreciated

---

### Post by QDR06VV9 on 2016-03-01
See if this is what you need..
[http://ubuntuforums.org/archive/index.php/t-942164.html](http://ubuntuforums.org/archive/index.php/t-942164.html)

---

### Post by mrmrva on 2016-03-02
Thanks runrickus for that link but it turns out the problem is not in the code that generates playlist. Tried it and it works on Xubuntu but on Ubuntu (14.04.4 32-bit) I get error bellow although the file exists. Tried to move it to /home/Videos/ folder but still the same

> linford@linford-ck1:~/Desktop$ mplayer -playlist lista.txt
File not found: 'lista.txt'
Failed to open lista.txt.
Error while opening playlist file lista.txt: No such file or directory
Error parsing option on the command line: -playlist
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team


---

### Post by mrmrva on 2016-03-02
Deleted script file, recreated it and the problem is gone!?

---

### Post by QDR06VV9 on 2016-03-02
He He He! Stranger things have happened..:D
Glad you got it sorted out.
Kind Regards

---

