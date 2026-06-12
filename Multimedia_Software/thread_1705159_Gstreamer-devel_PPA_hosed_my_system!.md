---
title: "Gstreamer-devel PPA hosed my system!"
date: 2011-03-11
forum: Multimedia Software
---

### Post by wkulecz on 2011-03-11
"Updating" gstreamer with the PPA hosed my system, none of the gstreamer video input stuff works now.  I was developing an application using gstreamer as the video interface and now nothing works.

How do I revert to the repo versions of all the gstreamer stuff?

---

### Post by mc4man on 2011-03-11
Install ppa-purge, it should be able to take care (assuming you haven't messed with your sources list

then something like this
```
sudo ppa-purge ppa:gstreamer-developers/ppa
```

---

### Post by wkulecz on 2011-03-15
Thanks a bunch.

It worked but wasn't pretty, I had to manually re-install a lot of things that didn't re-install automatically after the purge.  Good thing I set large default scrollback buffers on my terminal windows.

---

