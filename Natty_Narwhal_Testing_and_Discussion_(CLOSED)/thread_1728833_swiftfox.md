---
title: "swiftfox"
date: 2011-04-14
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-04-14
this seems to work much better than ff4 in natty. it can be installed from the spm. and if you have the ff ext nightly tester tool installed first all of the ext that you have in ff4 should work. after you install swift you should get the option to install all of your ff4 extensions. 
the only thing is that there is no global menu for swift. but imho no big deal

---

### Post by lovinglinux on 2011-04-14
Swiftfox is optimized for your processor family, so it runs faster. However, I doubt Swiftfox 3.6 is faster than Firefox 4. When Swiftfox 4 comes out then it probably will make a difference.

The major drawbacks is that Swiftfox is 32bit only and proprietary.

---

### Post by rburkartjo on 2011-04-14
but still works great in my 64bit machine

---

### Post by lovinglinux on 2011-04-14
> **rburkartjo said:**
> but still works great in my 64bit machine

I don't doubt it. I have used myself in the past, when my processor was slow and Firefox 3 was even slower. But I am curious. Does flash work properly?

---

### Post by rburkartjo on 2011-04-14
love, no flashplayer does not work correctly but neither does it in natty while using ff4

---

### Post by lovinglinux on 2011-04-14
> **rburkartjo said:**
> love, no flashplayer does not work correctly but neither does it in natty while using ff4

But the reason is that Swiftfox is 32bit, so most likely other plugins like totem-mozilla and gecko-mediaplayer won't work either.

---

### Post by chrisccoulson on 2011-04-14
The build-config changes made by Swiftfox are only likely to have minimal effect on performance (I never really noticed any difference tbh). In addition to this, the main difference with swiftfox is that it is built with -O3, and this is the now the default in Firefox 4 anyway.

The other additional build flags they pass (-msse2 -mmmx -m3dnow) are all default on amd64, so have no effect at all.

---

