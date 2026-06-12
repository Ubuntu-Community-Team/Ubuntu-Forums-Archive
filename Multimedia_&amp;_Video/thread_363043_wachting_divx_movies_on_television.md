---
title: "wachting divx movies on television"
date: 2007-02-16
forum: Multimedia &amp; Video
---

### Post by luijkx on 2007-02-16
Hello,

I am trying to connect my laptop with ubuntu 6.06 to my tv to watch movies. I use a super video cable from my laptop with a scart on the other end to my tv. Now, I can see my computer screen on the tv, but when I play a movie it becomes blue on the television, although the rest of the screen is still there! Is this a resolution problem? What should I do?
Thanks for any help
harm.

---

### Post by Paerez on 2007-02-16
Use mplayer to play the movie, and play around with the video playback device in the Preferences menu. Try gl2 or xv.

---

### Post by luijkx on 2007-02-19
Thank you for that, it works best when I set it to X11. And I actually use totem now, because that works now as well. The Mplayer had a problem with the sound, it was not synchron with the picture.
Cheers,
harm

---

### Post by luijkx on 2007-02-20
Hi Again,

Unfortunately, it is not working as I want it too. The size of the picture is very small, even on fullscreen. That is on the monitor as well as on the tv. If I change the video settings, the picture will be really fullscreen on the laptop monitor, but it will become blue again on the tv. I think it has to do with my videocard. My laptop is 4 years old and I actualy don't know the type of videocard. I tried instructions and downloading drivers as mentioned on the ubuntu help pages, didn't make a change.
Can anybody help me out? Thanks so far,
Harm.

---

### Post by luijkx on 2007-02-26
Hi all,

I solved the problem in Mplayer. In the video menu I chose "X11", in the audio menu "OSS" and in the codecs and demuxer menu I chose "FFmpeg's libavcodec codec family" in video codec family. Now there is no delay in sound anymore.
Furthermore, to make the screen full size I just changed the screen resolution (only for watching movies, looks awful for the rest) to 640x480. I can watch fullscreen divx movies now on TV directly from my laptop. Quality is good, provided that the downloaded movie is of good quality.
Cheers,
Harm.

---

