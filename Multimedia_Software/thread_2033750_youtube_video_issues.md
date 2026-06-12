---
title: "youtube video issues"
date: 2012-07-26
forum: Multimedia Software
---

### Post by kaushikgaurav on 2012-07-26
I am using Ubuntu 12.04 on lenovo X61 tablet.
The issue i am facing is that whenever i try to maximize the video on youtube, it does maximize but i get snow in the video.
It is very annoying.
Does anyone has any solution to this problem?
I already try to disable hardware acceleration in display settings but no luck.

Thanks in advance.
Gaurav

---

### Post by moshuptrail on 2013-01-12
I am getting this too.  Seems to be Adobe Flash.  I get little yellow snow when the video plays, maximized or not.

That's right, yellow snow.  No, don't eat it!

---

### Post by furtom on 2013-01-22
Yup. Same here. Doesn't have to be maximized. Happened after update. 

I've downloaded some flv vids to test, and they play fine in Mplayer or VLC, etc. Seems Flash problem.

I'm running 12.10.

---

### Post by furtom on 2013-02-02
I'm very happy to say I've discovered a work around for this bug.

If you go to chrome://plugins/ and expand the Shockwave entry, you will find something called "pepper flash"

```
/opt/google/chrome/PepperFlash/libpepflashplayer.so
```

It may have something to do with Chrome Remote Desktop, which I don't think is an issue for non ChromeOS users, and probably not too many of them, either.

Anyhoo, if you disable this plugin, the odd yellow show will vanish from Flash.

Hope this helps.

---

