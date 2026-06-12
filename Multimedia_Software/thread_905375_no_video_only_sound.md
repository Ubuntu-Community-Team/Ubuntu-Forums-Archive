---
title: "no video only sound"
date: 2008-08-30
forum: Multimedia Software
---

### Post by crofty1984 on 2008-08-30
hello all, I was wondering if you could help me.
I have ubuntu on my new Elonex webbook, I can't play video.
I get sound but no picture.

I've spent the last day or so trying to fix it. I have installed Mplayer and gnome mplayer, i've derestricted the restricted codecs, but no joy.
 The thumbnail of the video shows when it's an icon.
PS. it's an avi file

I know other people have had this problem, but I don't seem to be able to fix it.

---

### Post by Alan Bell on 2008-08-30
hi there,
the problem is that the graphics drivers don't support the XV extension correctly although they say they do. You need to press alt+F2 and run gstreamer-properties and on the output plugin tell it not to use XV. More details available on the [webbook blog]("http://webbookblog.com/?p=44")

---

