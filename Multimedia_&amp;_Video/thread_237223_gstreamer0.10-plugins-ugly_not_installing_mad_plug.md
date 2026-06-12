---
title: "gstreamer0.10-plugins-ugly not installing mad plugin"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by Daekharel on 2006-08-15
According to [this](https://help.ubuntu.com/community/RestrictedFormats), I need gstreamer0.10-plugins-ugly. However, I have installed that, and gstreamer-based applications (Totem, Quod Libet, BMPx) still are not able to handle mp3's. I've checked whether the gstreamer libmad plugin is installed using "gst-inspect mad", and the result is "No such element or plugin 'mad'"; so obviously there's something wrong with the installation of gstreamer0.10-plugins-ugly. I've tried reinstalling it, but to no avail; likewise with regards to installing the multiverse version. I currently have version 0.10.3-0ubuntu3 of gstreamer0.10-plugins-ugly installed.

Does anybody have an idea how to fix this?

---

### Post by Jagot on 2006-08-16
You appear to be using Breezy, in which cahse the codec you need is gstreamer0.8-mad - have you tried to install that?

---

### Post by Daekharel on 2006-08-16
Thanks, but I'm actually using Dapper; I just forgot to update my profile information on the forum after I upgraded from Breezy.

---

### Post by whatever on 2006-08-16
> **Daekharel said:**
> I've checked whether the gstreamer libmad plugin is installed using "gst-inspect mad"

you should use "gst-inspect-0.10 mad" instead

---

### Post by Daekharel on 2006-08-16
gst-inspect-0.10 mad gives the same results. Besides, gstreamer0.8 isn't even installed on my machine, and gst-inspect --version indicates that gst-inspect is for gstreamer version 0.10.6, so I'm sure gst-inspect is gst-inspect-0.10.

**Edit**
Fixed the problem, by manually recompiling gstreamer and the gstreamer ugly plugins. No idea why this was necessary, but at least it works now.

---

