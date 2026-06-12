---
title: "Which package owns/maintains /etc/asound.conf"
date: 2010-07-11
forum: Multimedia Software
---

### Post by doesntcount on 2010-07-11
Can anybody tell me which package owns/maintains /etc/asound.conf? I thought it would have been alsa-base, but I uninstalled alsa-base, and the file was still there.

I have a suspicion that I messed with my /etc/asound.conf file and I would like to regenerate it. I was thinking a simple reinstall of the package that owns this file would help me do that.

Thanks for the help.

---

### Post by mc4man on 2010-07-11
Haven't seen that file ever in /etc, never used jaunty but that appears to be last time it was in alsa-utils, ect. (asoundconf

[http://packages.ubuntu.com/search?suite=jaunty&arch=any&mode=filename&searchon=contents&keywords=asoundconf](http://packages.ubuntu.com/search?suite=jaunty&arch=any&mode=filename&searchon=contents&keywords=asoundconf)

you could download the .deb, then use the archive manager to extract the contents (don't install... (if asoundconf is what you're looking for vs asound.conf



Edit;
possibly related though maybe not what you're talking about
[http://ubuntuforums.org/showthread.php?t=1348604](http://ubuntuforums.org/showthread.php?t=1348604)

---

