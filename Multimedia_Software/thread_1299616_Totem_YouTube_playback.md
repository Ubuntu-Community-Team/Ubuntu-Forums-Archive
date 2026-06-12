---
title: "Totem YouTube playback"
date: 2009-10-24
forum: Multimedia Software
---

### Post by oohbuntoo on 2009-10-24
In Jaunty 9.04 when I try to play YouTube video search results in Totem I get this message:

**[COLOR="Red"]GStreamer encountered a general supporting library error.[/COLOR]**

What does this mean, and, how do I fix it??

---

### Post by gh4ever on 2009-10-25
I'm getting the same thing.

---

### Post by vinutux on 2009-10-25
Try miro or **[minitube]("http://www.getdeb.net/app/Minitube")** instead

**[http://www.getdeb.net/app/Minitub]("http://www.getdeb.net/app/Minitube")**e

[IMG]http://www.getdeb.net/media.php?id=730&type=screens&w=425&h=350[/IMG]

---

### Post by br0t on 2009-11-08
the bug is reported here: [https://bugs.launchpad.net/gstreamer/+bug/459423](https://bugs.launchpad.net/gstreamer/+bug/459423)

currently there is an update for karmic in the karmic-proposed package-source, which works fine for me and others, see:
[https://bugs.launchpad.net/gstreamer/+bug/459423/comments/47](https://bugs.launchpad.net/gstreamer/+bug/459423/comments/47)

someone also prepared a patch for jaunty, but it still needs acknowledged to get into the jaunty-proposed package-source:
[https://bugs.launchpad.net/gstreamer/+bug/459423/comments/68](https://bugs.launchpad.net/gstreamer/+bug/459423/comments/68)

if you want use the proposed updates take a look at the following how to:
[https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed)

with some patience a public fix should be available soon through the official/stable package-sources..

---

