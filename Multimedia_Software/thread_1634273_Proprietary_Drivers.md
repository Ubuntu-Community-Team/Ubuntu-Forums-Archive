---
title: "Proprietary Drivers"
date: 2010-11-30
forum: Multimedia Software
---

### Post by Kyluke on 2010-11-30
Hey,
I didn't quite know where to post this, this seemed the most appropriate place, please move it if this post doesn't belong here.

My question is, when is ATI going to produce some quality drivers? It has been ages that the same problems have occured all over the place such as screen tearing and wake ups from hibernation and suspends not working correctly etc. These have been complaints from pretty much every ATI linux user on the web for years now. Does ATI simply not care about the linux community or is there a serious problem with that they can't overcome.
Nvidia has much better drivers so it can be done, why has ATI been letting us down all these years?
The open source drivers are good but they don't offer the performance of the proprietary drivers which is a big problem if your graphics card is not epically powerful.

---

### Post by Yellow Pasque on 2010-11-30
ATI mainly cares about open-source drivers. They are making some progress with the closed-source driver (new 2D acceleration fixes a lot of old issues), but it could be nicer, yes.
If I had my choice, I would rather ATI/AMD keep providing open documentation and code samples rather than trying to polish the ugly hack that is their binary driver. The open-source 3D performance bottleneck is being worked on to make the open-source 3D closer to fglrx (though it will never totally catch up since fglrx uses Windows code and that has a lot more manpower behind it).
While it's kind of technical, there is interesting discussion on the mesa-dev list about the 3D performance and HD video decoding: [http://lists.freedesktop.org/archives/mesa-dev/2010-November/thread.html#3998](http://lists.freedesktop.org/archives/mesa-dev/2010-November/thread.html#3998)

---

### Post by Kyluke on 2010-11-30
Thank you for that very informative answer :)
If fglrx is better than the open source driver because it has more people working on it and uses windows code, why not simply improve and exclusively work on fglrx and then simply provide full documentation on it for the open source community.
I would think that it would be better to have one epic driver than 2 that aren't really complete. Or have I misunderstood?

---

### Post by Yellow Pasque on 2010-11-30
AMD doesn't want to expose its 3D driver optimizations because of the competition, and then there's DRM (i.e. Digital Rights Managament) when dealing with video. Also, the mode-setting and 2D code is completely different on Windows.

---

### Post by Kyluke on 2010-11-30
Oh yes of course, sorry been on linux so long I'm so used to everything being open and free.
That is understandable. Well I do hope that ATI can in the near future develop something which rivals nvidias drivers otherwise I am sad to say I'm going to have to switch to nvidia, not that they care about one person leaving :P

---

### Post by wkulecz on 2010-11-30
I swore off ATI video when Windows 98 was replaced by Windows 2000 and W2K drivers for my ATI cards never came.

Been a very happy Nvidia camper ever since for both Windows and Linux.  I've pased on great deals on motherboards precisely because they came with ATI video built in.

---

