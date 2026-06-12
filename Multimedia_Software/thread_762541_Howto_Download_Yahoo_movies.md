---
title: "Howto Download Yahoo movies"
date: 2008-04-22
forum: Multimedia Software
---

### Post by phillipchandler on 2008-04-22
Does anyone know how to download movies from yahoo ? Ive tried fernyb, Lyfox & orbit, plus a few others. The link im looking at is [http://new.music.yahoo.com/singleVideo/?vid=2148021](http://new.music.yahoo.com/singleVideo/?vid=2148021) and for the life of me cant find a downloader, not even in the firefox add-ons neither.

Thanks

---

### Post by Stevko on 2008-04-22
You can try to run a (transparent) proxy on your machine that will intercept all requests to Yahoo servers and try to find url of the video there (or even set your proxy to cache everything and then find that video in the cache). That should work.
These methods work usually, but for some reason I was not able to apply them to Yahoo videos:
I use Firefox extension called Tamper Data and find the url of video there (and using replay in browser command I download them), but I did not succeed with Yahoo videos.
Or if you use swfdec you can see the files flash downloaded and save them, but again I was not able to do that with Yahoo videos.

---

### Post by phillipchandler on 2008-04-22
This is the problem, I can rip videos from any other site(ish) like youtube, but yahoo doesnt want to play ball. Shame that

---

### Post by cor2y on 2008-04-22
The reason you can't download is because it is using the new flash protocol rtmp which has not made it into the opensource arena yet.
The closed source flash plugin can understand it but there are no downloaders yet except for closed source ones on the windows side that can understand it yet.
Your best bet is to look in your tmp directory under root to see if anything was left there after you play the video.
Sometimes its cached there sometimes its not.
The windows file downloader called Orbit downloader can understand the rtmp protocol but its windows and closed source , i don't know if it works via wine or not.

---

