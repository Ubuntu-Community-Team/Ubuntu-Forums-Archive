---
title: "Play video in chromium"
date: 2019-06-14
forum: Multimedia Software
---

### Post by irv on 2019-06-14
I have always used the Chrome Browser, but I am trying Chromium instead. The only problem I have found is I can't get videos to play.
youtube tv, Netflix, Hulu, etc. I think I need a plugin but not sure which one and how to install it.

EDIT: I can play youtube videos, not youtubeTV videos.

---

### Post by TheFu on 2019-06-15
My guess is this is a DRM problem.  Chromium is different from Chrome - no DRM.
[https://www.theregister.co.uk/2019/04/03/googles_widevine_drm/](https://www.theregister.co.uk/2019/04/03/googles_widevine_drm/) has a little history.
> "I'm sorry but we're not supporting an open source solution like this," says the note from Widevine, which Maddock posted to his website.

That's my guess.

---

### Post by CatKiller on 2019-06-15
The good thing about using Chromium rather than Chrome is that you can use hardware accelerated video decoding, which Chrome doesn't support. However, Chromium is not allowed to distribute the Widevine DRM stuff, even though they can use it. You just need to copy a file - libwidevinecdm.so, I think - from your Chrome install to your Chromium one.

---

### Post by irv on 2019-06-15
Yes, it is a DRM problem trying to use Chromium. I tried a few things, but no luck as yet. This is a shame that Google will not release the code for DRM to opensource so all browsers can have a clear playing field. 
I find I will have to play around with this at a later date. I need to get some work done and can not do this when playing around with browsers. I really love opensource.

---

