---
title: "Firefox no longer runs flash correctly"
date: 2014-07-26
forum: Multimedia Software
---

### Post by vroom2 on 2014-07-26
Hello,

Today I went to YouTube and started playing a video... A video ad popped up, and played for a few seconds (without audio), but then automatically skipped to the video. The video began playing without audio in near full HD, but then very quickly (inside of a second or two) dropped down to 360p, then 240p, then 180p, and then it skipped to the next video in the playlist and repeated the process (or crashed, saying that an error has occurred if there isn't a playlist available). I've also tried going to the Steam website, and playing a few game trailers off of there, and although the video plays, there is no audio. Chromium runs everything just fine.

These are the steps I've taken to try to solve this:
[LIST=1]
[*]Clear cache + cookies.
[*]Delete ~/.mozilla directory.
[*]Install updates.
[*]Uninstall and reinstall Firefox.
[*]Perform steps 2 and 4 simultaneously.
[/LIST]

I'm still not having any luck fixing this, and I'd rather not have to switch to a new browser. Any ideas?

Thank you!

---

### Post by renanrischiotto1 on 2014-07-26
Hello!

Strange in Chromium run well, because as far I know, Chromium uses the same version of Flash of Firefox. Must be because of the outdated version of Flash that Firefox uses, but it's just a guess.

Hugs!

---

### Post by vroom2 on 2014-07-26
You appear to be correct, renanrischiotto1! I checked the flash versions, and Firefox is using Flash version 11, while Chromium is using Flash 14... Any idea if I could force Firefox to use version 14?

---

### Post by renanrischiotto1 on 2014-07-26
Try to follow these procedures.

[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

But I do not recommend (at least the part of Flash (or maybe I did not do right), it may be that other things work), because after the YouTube videos have become slow.

---

### Post by QIII on 2014-07-26
Hello!

If you read down toward the bottom of those instructions, you will find a link to some instructions to make sure that hardware acceleration is used.

That has made a great deal of difference for me.  You might try and see if it works for you.

---

### Post by Yellow Pasque on 2014-07-26
Did you clear the Flash cache?
```
rm -r ~/.adobe/Flash_Player/*
```

---

### Post by vroom2 on 2014-07-27
> **Temüjin said:**
> Did you clear the Flash cache?
```
rm -r ~/.adobe/Flash_Player/*
```

I wasn't aware that Flash had a cache, and that fixed it! Thank you!

---

