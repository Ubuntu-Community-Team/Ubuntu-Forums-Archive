---
title: "can't get MP4 videos to play"
date: 2007-03-06
forum: Multimedia &amp; Video
---

### Post by Statik on 2007-03-06
Hi all,

I've been playing with the greenscreen plugin for Blender and the author has two demo videos on his website in MP4 format. I cannot get them to play. I have used automatix and easy ubuntu to install the restricted codecs but it still will not play. What can I do to determine where the problem lies, and then, what can I do to solve it?

Statik

---

### Post by magicfab on 2007-03-06
As a workaround you could download the files and try to convert them by suing the ffmpeg2theora package. Install ffmpeg2theora and use the following command:
ffmpeg2theora file.mp4

It will produce an Ogg Theora file with .ogg extension that can be viewed with any Ubuntu media player.

---

### Post by Statik on 2007-03-07
statik@statik-desktop:~$ ffmpeg2theora hardwater.mp4
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'hardwater.mp4':
  Duration: N/A, bitrate: N/A
No video or audio stream found


video clip came from here: [http://paprmh.googlepages.com/greenscreen](http://paprmh.googlepages.com/greenscreen)

Statik

---

