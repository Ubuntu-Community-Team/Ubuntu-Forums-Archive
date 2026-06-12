---
title: "Movie colors are weird"
date: 2008-01-31
forum: Multimedia &amp; Video
---

### Post by masi0 on 2008-01-31
Hi :)
first - i spend some time googling this with no luck :confused:
while playing movies in any player (mplayer, smplayer, vlc) - colors are like solarized/too big contrastr anyway look like crap:mad:
any idea how to fix it?

thx

---

### Post by arsenic23 on 2008-01-31
I beleive this problem happens when using a mix of certain players at the same time.  If I remember correctly, I've had this happen when I use gxine and then try to use another play after that.  I think restarting the gdm cleared it up untill the next time I used gxine....  but it might have been another player altogether.

Hopefully someone who is a little more familiar with the issue can give you more information as to the why and how of it.

---

### Post by archivator on 2008-01-31
It's more likely related to the use of fglrx (ATI's drivers) and XGL at the same time. At least that's when I get some weird artefacts (color shift, shadow images, etc.). For me, Totem is the only one not suffering from such issues. But then again, VLC performs *much* better with 720p x264 files. You might want to try different output modules (in VLC) or play around with Compiz Fusion's YUV colorspace option (under Video Playback in Advanced Desktop Effects).

---

