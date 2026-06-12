---
title: "Tearing in Gnome"
date: 2006-07-13
forum: Multimedia &amp; Video
---

### Post by transm on 2006-07-13
I run a geforce go7800 on my dell e1705 laptop. Is there any way to get rid of the tearing issues that i'm seeing in gnome when I drag windows? i installed nvidia-glx and the screensavers aren't tearing at all. It's only when I drag windows. This also happens when compiz runs as well.

Before I installed compiz, I tried changing the driver settings after running nvidia-settings but nothing seemed to help.

---

### Post by oldmanstan on 2006-07-13
are you running the nvidia drivers? (i assume that's what you meant by nvidia-glx but just checking) your /etc/X11/xorg.conf should have the "glx" line added near the top and i think the "dri" line should be commented.

also, under DEVICE the driver should be "nvidia" not "nv"

---

### Post by transm on 2006-07-17
Thanks for the response- all of those settings are already there as per the compiz/xgl nvidia install tutorial @ [http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)

As far as I can tell this is an issue affecting many people and has as of yet been unresolved. Another post addressing this is also running.

---

