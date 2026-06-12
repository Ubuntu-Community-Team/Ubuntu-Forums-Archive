---
title: "ffmpeg: sound and video do not coincide"
date: 2012-03-30
forum: Multimedia Software
---

### Post by Smiletastic on 2012-03-30
[SIZE=4]Hello all,
I'm trying to record a desktop video via ffmpeg. I'm using:
[/SIZE]   	 	 	 	 	 	  ffmpeg -f alsa -ac 2  -ab 128k  -i hw:0,0 -f x11grab -s $(xwininfo -root | grep 'geometry' | awk '{print $2;}') -r 30 -qscale 1  -i :0.0   -f avi ./Desktop/mydesktop.avi [SIZE=4]It works but sound and video don't coincide. Is there any way to fix this problem?

Many  other commands  I tried didn't work at all.
Thanks in advance.
[/SIZE][SIZE=4] [/SIZE]

---

### Post by gordintoronto on 2012-03-31
Have you tried recordmydesktop?

What CPU and video card in your computer?

---

