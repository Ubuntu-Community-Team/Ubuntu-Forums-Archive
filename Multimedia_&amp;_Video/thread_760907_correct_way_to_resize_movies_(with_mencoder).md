---
title: "correct way to resize movies (with mencoder)"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by Kulgan on 2008-04-20
I have been looking for ages to find a good way to reduce the size of videos, both in terms of MB's, and screen dimensions. 

In this case, it's an anime that I can only find in mp4, which wouldn't be a problem if it weren't for the huge dimensions (1280 x 720). That's bigger than my laptop screen, and I refuse to have to start a noisy desktop every time I want to watch an episode. The use of higher resolutions are increasing, and my screen size isn't, so I need a way of reducing the dimensions. The big ones don't play properly beacuse they apparently require more resources than I have to resize every frame to fit my screen. So it's laggy. 

I have been looking all over for something that explains how to use mencoder to resize. I eventually found this: 
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-rescale.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-rescale.html)

it didn't quite work as given, so I have tried this instead:
```
mencoder input.mkv -ovc lavc -oac pcm -lavcopts vcodec=mpeg4:mbd=2:trell -vf scale=640:480 -o output.avi
```

and later figured out I needed to use 640:320 to keep the ratio. 

That resizes the vid and turns it into an avi. That's fine. It also takes the file size from under 70 mb to over 400. That's not fine. 

So... is there a way to get it back to a decent filesize? A standard medium quality episode should be around 100-150 MB as an avi...

I don't mind reading docs, but I haven't found any of the docs I have read so far particularly useful. 

Any help greatly appreciated. 
Thanks,
~K

---

