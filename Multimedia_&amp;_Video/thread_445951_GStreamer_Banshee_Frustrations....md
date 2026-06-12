---
title: "GStreamer Banshee Frustrations..."
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by Abaddon on 2007-05-16
Hi All,

I'm trying to build the latest Banshee from source, and I keep getting:


```
checking for GST... configure: error: Package requirements (gstreamer-0.10 >= 0.10.3
                gstreamer-base-0.10 >= 0.10.3
                gstreamer-plugins-base-0.10 >= 0.10.3
                gstreamer-controller-0.10 >= 0.10.3
                gstreamer-dataprotocol-0.10 >= 0.10.3) were not met:

No package 'gstreamer-plugins-base-0.10' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

```

Despite the fact that I've very definitely got all of the GStreamer plugins installed.  Grrr!

Any ideas?

---

### Post by reclusivemonkey on 2007-05-17
I'm not sure whether this will help, but whenever I want to compile something from source on Ubuntu with dependencies, I need to install the -dev versions.

---

