---
title: "Very slow sound while palying mp4 files"
date: 2010-01-24
forum: Multimedia Software
---

### Post by metricspace on 2010-01-24
Hi, 
I've an inbuilt sound card on my mother board which is ASUS P5N73AM.

I get proper sound in win XP, however in Ubuntu it's very very slow

I just installed VLC , the movies are playing fine, however the sound is very slow, hardly i can hear it at full volume.

Please assist,

Thanks,
metric

---

### Post by ajgreeny on 2010-01-24
Do you really mean slow or just very soft?

---

### Post by metricspace on 2010-01-24
thanks for a response, It's very very slow even at a full volume. 

Regards,
metric

---

### Post by tgalati4 on 2010-01-24
open a terminal and run mplayer:

mplayer oneofmybazillionmp4tracks.mp4

See what errors come up.

---

### Post by metricspace on 2010-01-24
i got the following lines

[http://pastebin.com/d57cd6a43](http://pastebin.com/d57cd6a43)

thanks,
metric

---

### Post by metricspace on 2010-01-24
i installed mplayer, however in mplayer there is no sound and video both .

in VLC and totem video runs correctly, however the volume is very slow

thanks,
metric

---

### Post by LuridCinema on 2010-01-24
Is the mp4 file in HD ? 1920x1080  or 1280x720........ I have probs running HD files in 9.10. Im guessing my Video card is not powerful enough

---

### Post by metricspace on 2010-01-24
no the files are not in HD format

Regards,
metric

---

### Post by metricspace on 2010-01-25
the problem is solved , this page helped me [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

it got sloved with this commands,
alsamixer
and the settings were saved by 
sudo alsactl store 0

Regards,
metric

---

