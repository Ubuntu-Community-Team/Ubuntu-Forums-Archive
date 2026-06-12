---
title: "Poor video playback with VLC on Jaunty"
date: 2009-09-29
forum: Multimedia Software
---

### Post by sb73542 on 2009-09-29
Hi there,

I am using Jaunty on a common Dell Inspiron B130.  It is nothing fancy, but it is perfectly capable of playing videos.  I use the latest version of VLC from the c-korn PPA, which is supposedly the official VLC repo.

I have always used VLC, but it seems that recently the performance has been terrible.  DVD disks, as well as playing DVD ISOs results in jerky, laggy performance.  There are frequent pauses, interruptions, the video lags as the audio continues, etc.  I have verified this behavior both with the stock intel video drivers that come with Jaunty, as well as with the new 2.7.1 intel drivers from the x-swat PPA, but there is no difference.  When I play the same videos with Smplayer, the performance is quite good.  So any idea what the matter is with VLC and how I can fix it?

Thanks!

---

### Post by HappyFeet on 2009-09-29
I don't know about the korn ppa, but the [kow]("https://launchpad.net/~kow/+archive/ppa") ppa works perfectly for me.

---

### Post by sb73542 on 2009-09-30
I don't think the PPA build is the problem.  The c-korn PPA is from the developers of VLC after all.  Anyone else have any suggestions about an advanced setting that I can change?

Thanks!

---

### Post by amsum on 2009-09-30
I had similar problem and most of this got fixed when I changed the Video Output to X11 in VLC Video Settings.

---

### Post by sb73542 on 2009-10-12
Well, I tried the kow PPA and I tried X11 video output and it makes no difference.

---

