---
title: "kdenlive killed my gstreamer files in Koala"
date: 2009-12-02
forum: Multimedia Software
---

### Post by horseradish on 2009-12-02
or so it seems. I trried using kdenlive in koala for the first time and since then nothing using gstreamer seems to work. I tried reinstalling everything with gstreamer that I could see and no change. Even software center doesn't load longer than 2 seconds before disappearing

error is :

(software-center:3052): GStreamer-WARNING **: adding type GstFourcc multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstIntRange multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstDoubleRange multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstFractionRange multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstValueList multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstValueArray multiple times

(software-center:3052): GStreamer-WARNING **: adding type GstFraction multiple times

(software-center:3052): GStreamer-WARNING **: adding type gdouble multiple times

(software-center:3052): GStreamer-WARNING **: adding type gfloat multiple times

(software-center:3052): GStreamer-WARNING **: adding type gchararray multiple times

(software-center:3052): GStreamer-WARNING **: adding type gboolean multiple times

(software-center:3052): GStreamer-WARNING **: adding type GEnum multiple times

(software-center:3052): GStreamer-WARNING **: adding type GFlags multiple times

(software-center:3052): GStreamer-WARNING **: adding type gint multiple times

(software-center:3052): GStreamer-WARNING **: adding type gint64 multiple times

(software-center:3052): GStreamer-WARNING **: adding type glong multiple times

(software-center:3052): GStreamer-WARNING **: adding type guint multiple times

(software-center:3052): GStreamer-WARNING **: adding type guint64 multiple times

(software-center:3052): GStreamer-WARNING **: adding type gulong multiple times
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

---

### Post by horseradish on 2009-12-03
problem solved

```
sudo apt-get remove frei0r-plugins
```

[http://ubuntuforums.org/showpost.php?p=8377817&postcount=8](http://ubuntuforums.org/showpost.php?p=8377817&postcount=8)

---

