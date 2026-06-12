---
title: "25_skiploop_option in 0.22 ?"
date: 2009-09-03
forum: Mythbuntu
---

### Post by red321 on 2009-09-03
devs,

II have just started playing with upgrading to 0.22. I see from the weekly builds that my 25_skiploop_option is in the patches directory, but has never been applied to the trunk builds. 

Is that because it needs to be updated, or has it been dropped for other reasons. Nothing in the changelog.

---

### Post by red321 on 2009-09-03
In case they are still needed, I've updated the patch. I also produced a 1 line mini-patch if that is more useful. Most of the patch is all about letting the user turn on/off the loopfilter. Clean source its always on, with the mini patch its always off. Personally I cant see any reason not to have it off by default, as it saves a load of CPU, and I cant see any visual degradation.

---

### Post by red321 on 2009-09-06
Ok, having been educated on the mythtv-dev list, the issue is:

BBC-HD is now encoded slightly differently, and ffmpeg cannot mult ithread its decoding unless the loopfilter is turned off.

[http://www.gossamer-threads.com/lists/mythtv/dev/395983#395983](http://www.gossamer-threads.com/lists/mythtv/dev/395983#395983)

[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-October/012083.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2007-October/012083.html)[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

So in trunk, setting max CPUs to 2+ makes no difference to h264 decoding, as it stays single threaded.
Depending on the stream, dissable the loopfilter may allow multi threaded decoding. That is the case for BBC-HD. However it does not seem to be the case for ITV-HD, so ffmpeg will still be single threaded on ITV-HD. 

So, if you have a multi core CPU, and you want to watch BBC-HD, and a single core cant do it, then you still need the patch above. In most other cases, it will not help you. So the patch is now a " Use multiple cores for BBC-HD" patch :-)

I also produced a slightly diffrent patch:

With this simple patch, if you set max CPUs to 1, ( which you may as well, as ffmpeg doesnt do anything usefull when its set to 2) then normal trunk behaviour, loopfilter is on, and single core is used.

If you set max CPU to 2+, then loopfilter is turned off, (which gives little benifit on its own ) but multi threading is allowed where multi slice encoding has been used. (Like BBC-HD !)

---

