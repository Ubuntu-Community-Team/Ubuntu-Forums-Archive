---
title: "Cheap IP camera that works in Ubuntu?"
date: 2009-10-26
forum: Multimedia Software
---

### Post by Fraoch on 2009-10-26
I had an exciting find yesterday, a stock of discontinued Linksys WVC11B IP cameras at a surplus store for $50 each!  That's the cheapest I've ever seen an IP camera.

I have an application where I could use 4-5.  But I'd like to use these in Ubuntu and it seems the video can be streamed to IE only using an OCX plugin.

Bleh.

Current IP cameras start at about twice what these do - and most of these are IE-only as well!

Does anyone know of a *cheap* IP camera that works in Ubuntu?  I'd be using it wired.

Thank you.

---

### Post by Fire_Chief on 2009-10-26
According to a post I found here [http://www.coprolite.com/art58.html]("http://www.coprolite.com/art58.html") the video can be streamed into MPlayer when you use the following source address with the command (insert your details as needed)
```
mplayer http://user:password\@hostname/img/video.asf
```
Since this can optionally save the stream to video files or whatever, you'll have all kinds of flexibility with managing the video from here.

Cheers!

---

### Post by Fraoch on 2009-10-26
Wow, thanks - at about the same time you posted, I found this:

[http://www.infohit.net/blog/post/using-linksys-wvc54gc-webcam-with-linux.html](http://www.infohit.net/blog/post/using-linksys-wvc54gc-webcam-with-linux.html)

which indicates that the model that supersedes the WVC11B (the WVC54GC) uses a raw ASF-formatted stream.

I suspected the same might be true for its predecessor, and it appears to be:

[http://downloads.linksysbycisco.com/downloads/wvc11b_ds.pdf](http://downloads.linksysbycisco.com/downloads/wvc11b_ds.pdf)

 - the datasheet indicates "Video File Format ASF"

Awesome!

Thank you.

---

