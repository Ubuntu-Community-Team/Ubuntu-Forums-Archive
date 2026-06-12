---
title: "cannot build sound-juicer"
date: 2018-03-27
forum: Multimedia Software
---

### Post by lister171254 on 2018-03-27
Runing the lates 64 bit version of Ubuntu

sound-juicer cannot rip audio to flac due to a bug in gstreamer

[https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good1.0/+bug/1730116]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-good1.0/+bug/1730116")

as this bug has been fixed but the package gst-plugins-good1.0 isn't updated (don't know why), I decided to build sound-juicer (and gstreamer) locally.

When running configure I get the following error

```
llist@LeoGamesLT:~/gitrepos/sound-juicer$ ./configure --prefix=/home/llist/local
./configure: line 2143: syntax error near unexpected token `git-directory'
./configure: line 2143: `AX_IS_RELEASE(git-directory)'

```

Any help would be appreciated

---

### Post by mc4man on 2018-03-28
Hasn't been updated as 17.10 only has another 3 months or so of life & it's fixed in 18.04
Alternatives to building a newer gstreamer (sound-juicer likely won't need a rebuild) are install 18.04 or simply get the current 17.10 gst-plugins-good source, patch it  with the upstream commit to fix & rebuild as debian packages.
You can get some idea of how to patch for package build in screens, upstream commit/patch attached, extract ( the name I made up.), link to commit,
[https://cgit.freedesktop.org/gstreamer/gst-plugins-good/commit/?id=d4c04cb079661948ea520d55da2cc77e5d7ae295](https://cgit.freedesktop.org/gstreamer/gst-plugins-good/commit/?id=d4c04cb079661948ea520d55da2cc77e5d7ae295)

---

### Post by lister171254 on 2018-03-28
Thanks for the quick reply, but your recommendations regarding patching exceeds my skill set.
If is read this link [https://cgit.freedesktop.org/gstreamer/gst-plugins-good/commit/?id=d4c04cb079661948ea520d55da2cc77e5d7ae295]("https://cgit.freedesktop.org/gstreamer/gst-plugins-good/commit/?id=d4c04cb079661948ea520d55da2cc77e5d7ae295") correctly, there is a patch already available.
I have no idea, though, how to get it.
Thanks

---

