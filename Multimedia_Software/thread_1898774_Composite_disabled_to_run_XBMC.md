---
title: "Composite disabled to run XBMC"
date: 2011-12-22
forum: Multimedia Software
---

### Post by pergamon on 2011-12-22
Hello.

I have installed XBMC and Ubuntu 11.04 on a ZBOX ID41. After some problems with stuttering 1080p HD videos I disabled "Composite" in the file xorg.conf:

```

Section "Extensions"
    Option         "Composite" "Disable"
EndSection

``` Now HD playback is working smooth, but there are many strange display errors in Gnome.

Is it possible to disable Composit only for XBMC or is there another workaround instead of disabling composite?

---

