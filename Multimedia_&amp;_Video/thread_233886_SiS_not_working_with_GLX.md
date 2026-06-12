---
title: "SiS not working with GLX"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by yemenim on 2006-08-10
I have configured my laptop (with a SiS M760GX video adapter) with ubuntu, but it complains about the lack of a GLX context.

(see [http://www.ubuntuforums.org/showthread.php?t=165222&highlight=SiS+GLX](http://www.ubuntuforums.org/showthread.php?t=165222&highlight=SiS+GLX) for a nearly exact replica of my xorg.conf file)

$glxgears
Error: Couldn't get an RGB, Double-buffered visual
$glxinfo
Error: couldn't find RGB GLX visual
...

This is especially strange because the exact same config file will work properly with x.org 6.9 on Slackware, but not with Ubuntu's 7.0

Any suggestions?

---

