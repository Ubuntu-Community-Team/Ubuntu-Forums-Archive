---
title: "Totem internal data flow error"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by rogeriovinhal on 2007-04-20
Hi, I am runing Ubuntu Feisty AMD64 with open source drivers and beryl with AIGLX.

I tried to open a XVID video, and the codec installer installed the codecs correctly to open the video, but if I try to open it, it says "internal data flow error" and nothing happens, but If I click on "play" two or three times, the video start playing normally. Why is that?

---

### Post by sebas.rhcp on 2007-04-22
I have the same problem :(

---

### Post by Static-X on 2007-04-26
same problem but only with subtitles...

---

### Post by 3zero2 on 2007-04-27
same problem here. haven't found any solution yet.

don't know if the same would occur without subtitles but i will definitely try.

---

### Post by luder on 2007-04-29
Same here, but with divx. So far, only VLC could play the video with subtitles, and it only works sometimes...

---

### Post by rogeriovinhal on 2007-06-01
Nothing yet?

This may have something to do with Video Driver set to X Window System without XV, since I am using Beryl right now.

---

### Post by stchman on 2007-06-01
> **rogeriovinhal said:**
> Hi, I am runing Ubuntu Feisty AMD64 with open source drivers and beryl with AIGLX.

I tried to open a XVID video, and the codec installer installed the codecs correctly to open the video, but if I try to open it, it says "internal data flow error" and nothing happens, but If I click on "play" two or three times, the video start playing normally. Why is that?

I have never had much luck using Totem for anything.  Use VLC for all your multi-media needs.

---

### Post by simpsonatwork on 2007-08-03
The same error, always with subtitles of any encodings. I don't want to use VLC, as Totem to my taste is perfect in all details except subtitles.

---

### Post by RomeReactor on 2007-08-03
Hi. This seems to be [a bug in Gstreamer]("https://bugs.launchpad.net/totem/+bug/70223"); it's fixed in Gutsy (**gstreamer0.10-plugins-base** version 0.10.13); looks like we'll have to wait for a fix in Feisty.

---

### Post by simpsonatwork on 2007-08-04
On the [Bugzillathread]("http://bugzilla.gnome.org/show_bug.cgi?id=350299#add_comment") there's a [possible fix]("http://bugzilla.gnome.org/attachment.cgi?id=88687&action=view").
But I don't have any idea how to install it. Could you please explain how to install it?

---

### Post by RomeReactor on 2007-08-04
I wouldn't know what to do with that code, sorry.  However, this solution worked for me:
```
gst-launch-0.10 playbin uri="file:///FILENAME.avi" suburi="file:///FILENAME.srt"
```
didn't try it with other subtitle formats besides **.srt**, and it seems you can't fast forward or rewind; you have to watch the video as it plays without controls. The simplest solution in Feisty is to just quickly press play 3 or 4 times to get the video started. Just bear with it until Gutsy comes out in October.

---

### Post by IamAcoconut on 2007-10-23
Contrary to what's been said here, the problem does occur in **Gutsy**. 
I can play files normally, though a network stream stops after some (random period of) time, and no other file can be played without restarting Totem.

Pain in the **** - it never happened to me on previous Ubuntu versions (6.06+). I'll be glad to see a fix too.

---

### Post by speckman on 2007-11-04
i'm getting this error when trying to move the slider, while playing an .mp3.  Now, I'm not sure that the data isn't corrupted in the mp3.  But it seems to work fine if I just do it again.

Gutsy 64
Nvidia 7x

---

