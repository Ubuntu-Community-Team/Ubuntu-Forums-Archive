---
title: "reapiring a video file (.avi)"
date: 2008-10-03
forum: Multimedia Software
---

### Post by skiwithpete on 2008-10-03
Hi,

I've been using a casio exilim camera, and while on holiday it completely spazzed on me.  - It said it had a full memory card, and all of my photos were black and unreadable...

I downloaded a great program called photorec (part of testdisk) and it recovered all but two of my photos!

One video, however, is broken.  In Nautilus, it sees it as 115meg, but only the first 15 seconds of the video plays.

Its a .avi file, but I'm pretty sure the camera is recording in mp4.

I downloaded DivFix++ 0.26 for Ubuntu, and that recovered all of the audio, but lost even the first 15seconds of video.

I'm writing to find out if anyone has any suggestions for programs that I could try in order to recover the rest of the video.

Thanks
P

---

### Post by wolfen69 on 2008-10-03
in the past, i have had vlc ask me if i wanted to repair a broken avi when i right clicked it and open with vlc.

---

### Post by skiwithpete on 2008-10-03
> **wolfen69 said:**
> in the past, i have had vlc ask me if i wanted to repair a broken avi when i right clicked it and open with vlc.

I have done that, and VLC also plays only the first 15 seconds.  I really need a program that will inspect each part of the file to see where the error has occurred and repair it.

---

### Post by binbash on 2008-10-03
re-index the video with mplayer, vlc or with following command : 

mencoder -forceidx -oac copy -ovc copy before.avi -o after.avi

---

### Post by Xnyper on 2009-06-30
binbash's solution worked great for me, thanks!

My situation wasn't as drastic, VLC would prompt to fix the file, fix it, and then play it just fine.  Problem was that it wouldn't stay fixed, had to keep re-indexing the file.  Anyway, this did the trick permanently.

---

### Post by FiReSTaRT on 2010-01-28
Thanks binbash. It also worked perfectly for me.

---

### Post by misssarahdee on 2011-10-13
Sorry, I know this is an oldish thread. But I tried BinBash's method, and it makes the avi playable, but the fixed file only consists of the first 20-odd seconds of the film. The same happened for two separate broken AVIs. 

Any ideas?

---

### Post by leadelisa on 2012-02-02
AVI video files can get corrupted in several situations. If you have a corrupted AVI video file then repair the file using advance [avi repair]("http://www.avirepair.net") tool. It is pretty sure that after repairing the file, you will become able to view the contents of the file and you can easily play this file on your media playing application.

---

