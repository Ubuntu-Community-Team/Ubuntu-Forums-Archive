---
title: "Blender leave traces on window with ati driver"
date: 2008-02-21
forum: Multimedia &amp; Video
---

### Post by nagos on 2008-02-21
I have Ubuntu 7.10 and blender 2.44.
When i use some tools, like box selection (key "b"), dashed line of selection leave traces on blender window.
Its look like this:
[ATTACH]60298[/ATTACH]
I think that problem with ati driver. When i use "vesa" driver in xorg.conf, all looks fine.
Option "Accel" "0"
also works good.

Tested on Radeon 9200 and 9600 (both open source "ati" driver)
Who can help me?

Here is my xorg.conf and logs

---

