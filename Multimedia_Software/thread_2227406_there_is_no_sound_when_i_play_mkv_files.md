---
title: "there is no sound when i play mkv files"
date: 2014-06-01
forum: Multimedia Software
---

### Post by hugo12 on 2014-06-01
Hi there, I am a brand new Ubuntu user.

My problem is that there is no sound when I play mkv files. I played it in VLC, and Media Player. I installed  several codecs (Gstream, ubuntu-restricted-extra,mkvtools), but still no sound.

can you help me?

---

### Post by Vladlenin5000 on 2014-06-02
Hi, welcome.

MKV is just a container. It can contain different codecs, both video and audio. As such, first of all, you need to know which audio codec are in those files.

---

### Post by Yellow Pasque on 2014-06-02
```
sudo apt-get install mediainfo
mediainfo file.mkv
```

---

### Post by SeijiSensei on 2014-06-03
If the audio stream is MP3-encoded Ubuntu won't play them by default because MP3 is a patented algorithm.  Installing the ubuntu-restricted-extras package should have added the MP3 decoder and some other items.

I take it you can hear audio just fine from other sources?  Can you play an MP3?

I use [SMPlayer]("http://smplayer.sourceforge.net/"), a graphical front-end to mplayer which has its own codecs.  (I avoid the morass that is GStreamer whenever possible.)  You can trying installing it with "sudo apt-get install smplayer" and see if that works for you.

---

