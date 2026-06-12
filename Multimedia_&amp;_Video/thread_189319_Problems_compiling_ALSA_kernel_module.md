---
title: "Problems compiling ALSA kernel module"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by imrazor on 2006-06-05
I'm trying to compile a kernel module for an oddball sound card that ALSA supports, but isn't included in the modules that come with Ubuntu. According to this:

[http://ubuntuforums.org/printthread.php?t=49458](http://ubuntuforums.org/printthread.php?t=49458)

the trick is to install the alsa-sources package and use make-kpkg to build *all* of the alsa modules. The problem is that when I try the above instructions, configure barfs with this error:

configure: error: You have built-in ALSA in your kernel.

That's the whole point of this exercise - to build a kernel module. Is there any way I can force configure to ignore this error and build the module anyway?

---

