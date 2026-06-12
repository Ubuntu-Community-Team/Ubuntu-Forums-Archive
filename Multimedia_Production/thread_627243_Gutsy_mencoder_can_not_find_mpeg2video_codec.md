---
title: "Gutsy: mencoder can not find mpeg2video codec"
date: 2007-11-29
forum: Multimedia Production
---

### Post by DaveQB on 2007-11-29
Hi all,

As title says, mencoder cant find mpeg2video.  I found this problem as devede was failing, so I manually ran the coammand it was trying to run and mencoder complained about mpeg2video not found.

What package provides this ? 

I had devede working in Edgy and I think Feisty.

I run 64bit version.

Thank you!

---

### Post by Creative2 on 2007-11-30
plz write the command line you want use.

plz write the version of mencoder\ffmpeg

(to see wich version write, in a terminal :

 mencoder  

and

 ffmpeg -version

ffmpeg -formats |grep YOURFORMAT )

 have you installed mencoder with all supports ? from mendibuntu repo?

---

### Post by eye208 on 2007-11-30
> **DaveQB said:**
> What package provides this ?
It's either libavcodec0d (Edgy, Feisty) or libavcodec1d (Gutsy).

Both are in Ubuntu's own repositories, i.e. no need for Medibuntu or whatever.

---

