---
title: "xine issu with hardy"
date: 2008-04-30
forum: Multimedia Software
---

### Post by linuksamiko on 2008-04-30
After upgrading from gutsy to hardy I have big problems with xine and sound in general. Multiple aplications which try to play music at the same time might end up in playing nothing or even a freez and xine won't play ogg.
VLC has no problems with ogg but xine-apps have.

---

### Post by cor2y on 2008-04-30
launch xine from the terminal and see what the error is on ogg playback.
As for the multiple apps playing audio i don't know, pulse is supposed to take care of that but not all apps are pulse audio ready.
Try switching to alsa without pulse in your audio setup of ubuntu and see what happens.

---

### Post by linuksamiko on 2008-04-30
I allready tried to play an ogg from the console to get any error but it just said that I need to install xine-ui (and when I tried to install it I hade some problems with the internet)

Now that I've installed it xine says something like "demuxer plugin missing".

---

### Post by linuksamiko on 2008-05-08
I'm still stuck with my "can't play ogg" problem. Even after installing different plugins and reinstalling xine there seams to be nothing that helps.

I wish I could post the error-message from xine but it is not in english.

But basicly it says:

```

xine: plug-in error
there is no demuxer-plugin to handle <FILENAME>. Usually that means that the filetype is not recognized.

```

This all happend with the upgrade Gutsy --> Hardy and is quite annoying since half of my music collection is ogg.

---

### Post by linuksamiko on 2008-05-18
:guitar:

After more then two weeks without my favorite ogg-music I finally found a solution to my problem and just in case somebody, someday stumbles upon this problem I want to post my fix and further reading to this problem:

In my case it was corrupted .xine/catalog.cache I deleted/renamed the old one and then it worked.
I don't know what the catalog.cache is for and how it can corrupt but that isn't so important to me.

For further reading and another fix that might help read:
[http://crazedmuleproductions.blogspot.com/2007/06/xine-no-demuxer-plugin-available-to.html]("http://crazedmuleproductions.blogspot.com/2007/06/xine-no-demuxer-plugin-available-to.html")

---

### Post by Defrector on 2009-08-29
I am using kubuntu 9.04 and I confirm that deleting ~/.xine/catalog.cache as described above works for me too. I can now play OGG and other vorbis content.

Win!:KS

---

