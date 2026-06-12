---
title: "xowave"
date: 2006-08-30
forum: Multimedia &amp; Video
---

### Post by damu on 2006-08-30
Has anyone tried [XO Wave]("http://www.xowave.com/")?

What I find potentially very interresting in it is the video sync possibility.
The only way I found to have video sync on a linux based DAW is xjadeo. But , it is a very very basic app, which needs the video to be reencoded in raw format ( so you end up with a huge video file...) and that I didn't manage to get working in Studio-to-go even with a deb provided by teh STG team!(I didn't try in Ubuntu yet)


XO Wave works with .mov , so it might do the job!

---

### Post by bejayoharen on 2006-09-08
Well, as author of [XO Wave]("http://www.xowave.com"), who happened upon this forum, I am a bit biased, ;)  but I'll try to stick to the facts:

- XO Wave is starting to come into moderately wide use on the mac and it's fairly stable there, despite being beta. On Linux, there's more trouble, but many users have reported success with ASLA, OSS and JACK, so it's all doable.

- You asked about video sync, and it's there and it works, but it's based on JMF, sun's ancient java-based media framework. Many formats are readable, though, and if there isn't a list on the XO Wave site, [this one]("http://java.sun.com/products/java-media/jmf/2.1.1/formats.html") should help. I did a major audio for video project with XO Wave on Linux using a video file that was small, but contained every frame, and used cinepak compression and it worked very well. I think it was an AVI file. I didn't even have sun's "performance pack" installed.

HTH,

   bjorn

---

### Post by damu on 2006-09-10
thanks for ur answer. :) 
Can it be synced through jack?

---

