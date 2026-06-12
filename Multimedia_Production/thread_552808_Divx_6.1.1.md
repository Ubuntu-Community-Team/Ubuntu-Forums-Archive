---
title: "Divx 6.1.1"
date: 2007-09-17
forum: Multimedia Production
---

### Post by takakia on 2007-09-17
Is there any way to encode DivX in Linux? Xvid is good, but stage6 does not accept xvid files so Xvid has to be converted to DivX again. 

The divx 6.1.1 codec for linux has been released for quite a while, but there is no program to use it under linux. Will transcode ever use this codec?

---

### Post by vinutux on 2007-09-18
i think gmencoder (mencoder gui) do it 

it offer "mpeg4(divx xvid compitable)" option for converting videos

---

### Post by stmiller on 2007-09-18
VLC will encode a divx movie. Use the vlc 'wizard' in the menu.

---

### Post by rafalr on 2007-10-30
Gmencoder will only use ffmpeg/lavc library to convert video into presumably xvid/divx5 compatible mpeg-4 file. 

I write "presumably", because it will be divx5 compatible only if you supply a mencoder.conf file with ffourcc=DX50=1 enabled. I do not know about divx6 compatibility, though ...

Rafal

---

