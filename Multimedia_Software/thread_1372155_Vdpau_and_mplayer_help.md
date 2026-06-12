---
title: "Vdpau and mplayer help"
date: 2010-01-04
forum: Multimedia Software
---

### Post by mad_max0204 on 2010-01-04
Hi guys,

last night I refreshed my system installation with 9.10 (I had 9.04 till now) and I cant compile mplayer properly to use vdpau with 195.30 nvidia drivers. It all worked well in 9.04 but I cant find a howto that I used to compile it then (was almost a year ago).

Is there any howto on this subject ? Tried searching the forums but I cant find the right one.

I'm using 9800GT 1GB vram and a clean 9.10 64bit Ubuntu.


Thanks

---

### Post by mad_max0204 on 2010-01-04
bump

---

### Post by inobe on 2010-01-04
if i'm not mistaken that is old stuff and the current version mplayer-vdpau is in the repos assuming you have a video card and driver that supports it.

---

### Post by inobe on 2010-01-04
have a look at the avenard repo

[http://avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html](http://avenard.org/media/Ubuntu_Repository/Ubuntu_Repository.html)

---

### Post by mad_max0204 on 2010-01-04
I tried with those files too.
Hm, I'll clean everything when I get home and try again.

Maybe its the problem I installed the latest beta driver first.

Any other ideas other than using packages from that repository ?

---

### Post by inobe on 2010-01-04
i remember adding the repo and was prompted for an nvidia driver update, after that i installed mplayer-vdpau.

in fact i remember testing xine-vdpau only because i think it kills mplayer "my opinion"

---

### Post by mad_max0204 on 2010-01-06
For anyone that gets the same problem:

Mplayer from svn has vdpau support built in. No need for other repos or packages.
My problem was that I installed latest beta drivers and mplayer didnt like them.
After installing latest release driver, recompiled mplayer and now everything works fine.

Mark this thread as SOLVED

---

### Post by Yellow Pasque on 2010-01-06
As the thread creator, you can mark it solved (under thread tools menu).

---

