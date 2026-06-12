---
title: "mencoder multithreaded support for XviD"
date: 2008-10-13
forum: Multimedia Software
---

### Post by mobrien118 on 2008-10-13
Hello,

I use mencoder frequently to archive some DVDs I have and make the files smaller than the original DVDs. I like to use the XviD encoder option (usually multi-pass, FYI), which purportedly has multi-threading support, however it is a compiler option that is not currently set.

e.g. I would like to use "-xvidopts threads:2" since I have a dual core machine, but when I do it still only uses 1 core.

I don't even know which package contains the XviD codec and through searching the package lists I couldn't find a definitive answer. I would like to file a big request to report this problem and hopefully it will get solved.

The bug will most likely be entitled "threads:X" option doesn't work in mencoder using XviD codec".

If anyone has any information or comments on this course of action, please let me know! Also, if you know how mencoder works and where the XviD encoder package is located, let me know that too!

Thanks!!!

--mobrien118

---

### Post by eye208 on 2008-10-13
"libxvidcore4" is the encoder library. The mencoder manual states that multithreaded encoding is available only with version 1.2.x of the encoder. However this version does not yet seem to be released. Even the official xvid website states that the latest version is 1.1.3, with xvid 2.0 (H.264) being in development.

If you are looking for quick multithreaded encoding, why not use x264 instead of xvid? Contrary to popular belief, x264 is not necessarily slower than xvid. Its speed depends on the encoding settings. You can make it just as fast (and inefficient) as xvid. And x264 does support multithreading.

---

### Post by mobrien118 on 2008-10-13
> **eye208 said:**
> If you are looking for quick multithreaded encoding, why not use x264 instead of xvid? Contrary to popular belief, x264 is not necessarily slower than xvid. Its speed depends on the encoding settings. You can make it just as fast (and inefficient) as xvid. And x264 does support multithreading.

My biggest concern is compatibility. Videos encoded using XviD will play on windows systems with either XviD or DivX installed, right? I think they also play on OSX by default settings. Can videos encoded with x264 do this as well?

--mobrien118

---

### Post by 3rdalbum on 2008-10-14
Or you could go down the multiprocessing route, and encode two videos at the same time by running mencoder twice.

---

### Post by eye208 on 2008-10-14
> **mobrien118 said:**
> My biggest concern is compatibility. Videos encoded using XviD will play on windows systems with either XviD or DivX installed, right?
DivX does not support all Xvid features, but in general they are compatible.

> I think they also play on OSX by default settings.
No. Quicktime's support for MPEG-4 ASP is limited. But it can be extended using the free Perian plugin.

> Can videos encoded with x264 do this as well?
Yes. Quicktime supports most H.264 features out of the box. The Perian plugin will handle the rest.

For Windows there is FFDshow which adds full support for Xvid, DivX and H.264 to Windows Media Player and other codec-based players.

And finally there are VLC and MPlayer with full support for these formats on all platforms.

There is no need to stick with Xvid unless you have a standalone DivX DVD player.

---

