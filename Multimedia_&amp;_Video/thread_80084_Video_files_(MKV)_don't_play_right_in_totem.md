---
title: "Video files (MKV) don't play right in totem"
date: 2005-10-21
forum: Multimedia &amp; Video
---

### Post by Tsume on 2005-10-21
I was using ALSA sound system and it was horrible- it would start out almost vieweable and pause every second, then the pauses got longer and longer and well it's no fun watching that.  I switched it back to the game-hating ESD and it still plays for a second and pauses for a second... still unviewable, but better.  I noticed it was using 100% cpu.  If I play this in gxine, the cpu usage is at 33% but the audio gets a bit out of sync after a while (and I can't choose the language track in my file like I can in totem, so this isn't a good solution for me).

What should I do to get totem to play this correctly without using 100% cpu?

VLC won't play it at all, which is strange because the windows version of VLC on this dual-boot computer plays it just fine.

---

### Post by stoeptegel on 2005-10-21
MKV is matroska, you might have to install a new codec: [http://www.matroska.org/downloads/linux.html](http://www.matroska.org/downloads/linux.html)  I've not tested it myself yet.

Edit:
It should play with gstreamer:
[http://www.matroska.org/technical/guides/playback/linux/index.html](http://www.matroska.org/technical/guides/playback/linux/index.html)

---

### Post by bored2k on 2005-10-21
You could try installing libmatroska-dev from repositories.

---

### Post by Tsume on 2005-10-21
I made sure all the codecs were installed, I installed the gstreamer stuff as far as the file needed (XVID and an mp3 decoder), and it appears to support matroska either by default or by something I installed... or else it probably wouldn't play at all.

I tried installing that libmatroska thing anyway, but it didn't help.

DVD playback and AVI playback are equally as poor in totem, but seemingly fine in other programs.

---

