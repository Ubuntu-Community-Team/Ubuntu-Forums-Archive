---
title: "video encoding problems"
date: 2008-10-04
forum: Multimedia Software
---

### Post by georgeliquor on 2008-10-04
I seem to be having a problem encoding videos.

When using devede, qdvd, todisc, or k3b to author dvds, the burned iso won't play on my home dvd player. They will however, open in my computer.

Thinking it may have been brasero's problem, I sent a finished iso to windows and burned it there. no luck.

Using the same video in windows with devede, the disc burns fine and plays in my dvd player.

Trying to narrow down the problem, I converted a video in avidemux to mpeg, and sent it windows. It won't open there. It's not recognized as a usable file.

So I'm thinking ubuntu may be encoding the videos improperly. Has any one heard of this happening? Is there a fix?

It's a bit frustrating, because I feel so dirty having to use windows for something.

Thanks

---

### Post by xc3RnbFO8P on 2008-10-04
Read this:
[http://ubuntuforums.org/showthread.php?t=787299&page=5]("http://ubuntuforums.org/showthread.php?t=787299&page=5")

---

### Post by georgeliquor on 2008-10-04
That looks like the problem, however, when I try t depackage the downgrade, I get this:


ds@ds:/$ sudo dpkg --force-downgrade -i genisoimage_1.1.6-1ubuntu3_i386.deb
dpkg: status database area is locked by another process

---

### Post by georgeliquor on 2008-10-04
wow, it worked!


Devede doesn't work now though. Appearently it needs one of the replaced files. I need to find a new dvd authoring app now.

This is great though. Thanks!

---

