---
title: "WMV file broke my Codecs...Possibly Foreever"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by xyphier on 2007-03-02
I recently tried to play a wmv file i know was DRM protected. After getting an error in the tetem player i exited out and promptly tried to play another file i know i could open before. Now none of my movie files that used to work...work.

I tried reinstalling, all the codecs. Then uninstalling and reinstalling.

I've been trolling through forums and it seems other people are having the same problem, although they did not link it to any DRM files. Some even reformatted and reinstalled ubuntu and they still could not get any codecs to work.

Any thoughts of what when wrong or suggestions on how to fix it?

---

### Post by 23meg on 2007-03-02
See if refreshing your GStreamer codec registry helps:

```
rm -rf ~/.gstreamer-0.10
gst-inspect-0.10
```

---

