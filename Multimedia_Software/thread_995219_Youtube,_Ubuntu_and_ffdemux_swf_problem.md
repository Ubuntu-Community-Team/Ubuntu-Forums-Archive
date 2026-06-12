---
title: "Youtube, Ubuntu and ffdemux_swf problem"
date: 2008-11-27
forum: Multimedia Software
---

### Post by StephaneG on 2008-11-27
Hi there,
I cannot play any Youtube videos on Ubuntu totem movie player.
I´ve selected the youtube plugin, installed GStreamer as required but I keep on getting this message:

ffdemux_swf: Element doesn't implement handling of this stream. Please file a bug.

Can anyone help?
Thanks.

---

### Post by glenmo on 2008-12-07
i'm right there with you... i found a bug report in launchpad, but there was no solution.

[https://bugs.launchpad.net/bugs/163380](https://bugs.launchpad.net/bugs/163380)

---

### Post by mpalla on 2009-01-09
actually the bug report for this issue is this one:

[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/288494](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/288494)

while the fix has not yet been loaded in the repositories, you can copy the fixed youtube.py file into /usr/lib/totem/plugins/youtube/ (just make a backup of the original before)

---

