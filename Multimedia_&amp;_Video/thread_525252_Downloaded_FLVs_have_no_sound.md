---
title: "Downloaded FLVs have no sound"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by punong_bisyonaryo on 2007-08-14
Hello everyone.

I have multimedia set up just the way I like it: so far haven't encountered a file format I can't play. My xine has mlayer codecs, flash works in firefox, youtube works, etc.

But when I download FLVs from youtube on my computer using Miro, there is no sound playback at all, and the playback slider goes quickly from left to right, regardless of the video (I mean, the video is still playing when the slider reaches the end.

As far as I know, all I need are mp3 codecs for sound in FLV to work. But my mp3s play with no problem. What could be the cause?

Thanks in advance.

---

### Post by punong_bisyonaryo on 2007-08-14
Quick update, the quick slider problem exists in Miro. In Xine, the slider moves normally and as expected. And totem won't play my flv at all, says I have missing codecs.

---

### Post by tseliot on 2007-08-14
FLVs play well in VLC

---

### Post by punong_bisyonaryo on 2007-08-14
> **tseliot said:**
> FLVs play well in VLC

I tried installing vlc. The FLVs play in VLC with sound. However, sound still doesn't play anywhere else. Is there a common codec I can download so all my media players can take advantage of these codecs?

If I may also ask, how are the codecs structured in linux? The gstreamer and other codecs i installed thru synaptics can be accessed by everything. How about libxine-extracodecs? Is it only xine that can use them?

---

### Post by tseliot on 2007-08-14
> **punong_bisyonaryo said:**
> I tried installing vlc. The FLVs play in VLC with sound. However, sound still doesn't play anywhere else. Is there a common codec I can download so all my media players can take advantage of these codecs?

If I may also ask, how are the codecs structured in linux? The gstreamer and other codecs i installed thru synaptics can be accessed by everything. How about libxine-extracodecs? Is it only xine that can use them?
VLC doesn't rely on the w32codecs package. It's built in a different way.

I *guess* libxine-extracodecs is only for Xine, Totem-xine, Kaffeine-xine, etc.

Gstreamer works in a different way. Not that I'm an expert in this field...

---

### Post by punong_bisyonaryo on 2007-08-14
I read about a problem with .H264 (?). I tried playing the file on VLC and Mplayer. They both worked. I also read that Miro uses Xine as its engine, so I guess it's a problem with Xine then. I'll post more info here if I get it fixed, for other people's reference as well.

Then again, maybe there's someone out there already who knows about this problem. Kindly enlighten us.

---

### Post by punong_bisyonaryo on 2007-08-14
I've got it working!

Miro can use either gstreamer or xine engines, but since I couldn't get around playing FLVs in gstreamer at all, I decided to try and fix the xine problem. At first I tried installing libxine1 (the "heart" of xine) debs from Gutsy and Feisty. Obviously, they won't work in Edgy.

In the end I had to install xine-lib from source, following instructions at [Xine's FAQ]("http://xinehq.de/index.php/faq#AEN72").

So, playing FLVs with sound was solved, and also the "fast slider" problem in Miro was solved as well. My only concern is if it is okay to leave libxine1 in my system. I can't remove it, because xine-ui and miro both depend on it.

---

### Post by evri2 on 2007-08-15
> **tseliot said:**
> FLVs play well in VLC

 Can you seek in a FLV video?I cannot forward to last 10-15 second of video in VLC.When i try to do that,it stops the video.

---

### Post by punong_bisyonaryo on 2007-08-15
Nope. Actually mine stops still near the beginning as I'm sliding the slider slowly.

---

### Post by evri2 on 2007-08-15
I cannot understand that.I have an another distro installed named Pardus by Tubitak(Turksih Guys).In that distro i can do whatever i want in VLC.Forward,backward, seek anywhere in video.

---

### Post by Steve S. on 2007-08-16
Wish I could be more help, punong, but I began running either VLC which works almost all the time, or simply using flvconvert via the command to convert it to an mpg...most people I end up sharing videos with can barely figure out mpg's, much less flv's...;-)

...good luck!

---

### Post by punong_bisyonaryo on 2007-08-23
I have to add that before installing xine-lib from source, remove xine-ui first, or you'll break your xine. That's what happened to me consistently. Even if you completely remove xine-ui after you break it, subsequent installs still won't fix it.

Again, before compiling xine-lib from source, make sure you don't have xine-ui installed.

---

### Post by movil on 2007-10-31
Good tip. Too bad I readed it after doing all the mess...

I compiled XINE from latest source but I still don't  have sound in FLV's for Miro.

Ok, and <<offtopic>>>  now I have a really stupid problem with Flash.  Flash 7 plays sounds. But Flash 9 not. How the hell can this happen ?

---

### Post by Loetje on 2008-06-04
for Miro, installing gxine fixed the sound problem for me

---

