---
title: "Totem crashes with mp4"
date: 2015-02-07
forum: Multimedia Software
---

### Post by z987k on 2015-02-07
Totem just stopped playing mp4s today.  It crashes instantly giving - "Segmentation fault (core dumped)".  VLC still plays the files fine.  It was working fine 20 minutes ago and I've made no changes at all.  Googling that issue with totem turned up an old bug from 2012, which I tried the fix for to no avail.  Any ideas?

14.04 64 Bit.

---

### Post by mc4man on 2015-02-07
From afar no clue really, maybe try deleting ~/.cache/gstreamer-1.0/registry.x86_64.bin

---

### Post by z987k on 2015-02-07
> **mc4man said:**
> From afar no clue really, maybe try deleting ~/.cache/gstreamer-1.0/registry.x86_64.bin

Ya, nothing.

---

### Post by mc4man on 2015-02-07
I also don't use totem much, try some gst debugging & see if anything shows
 ```
totem --gst-debug-level=1 /path/to/yourfile
```
(1 is errors only, you could also raise a bit if 1 produces nothing, then try 2 (goes to 9 but 2 or 3 is likely the limit for useful info in this case

---

### Post by z987k on 2015-02-08
> **mc4man said:**
> I also don't use totem much, try some gst debugging & see if anything shows
 ```
totem --gst-debug-level=1 /path/to/yourfile
```
(1 is errors only, you could also raise a bit if 1 produces nothing, then try 2 (goes to 9 but 2 or 3 is likely the limit for useful info in this case

at level 3
```
0:00:00.288942180 15751 0x7f2ddbe2f790 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.306154575 15751 0x7f2ddbe2f790 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.313994517 15751 0x7f2ddbe2f790 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.314033010 15751 0x7f2ddbe2f790 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.324763812 15751 0x7f2ddbe2f790 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.324798642 15751 0x7f2ddbe2f790 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.325955987 15751 0x7f2ddbe2f790 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.325985512 15751 0x7f2ddbe2f790 FIXME                    bin gstbin.c:4008:gst_bin_query: implement duration caching in GstBin again
0:00:00.351435529 15751 0x7f2d98092ad0 WARN                 qtdemux qtdemux_types.c:196:qtdemux_type_get: unknown QuickTime node type iods
0:00:00.351510341 15751 0x7f2d98092ad0 WARN                 qtdemux qtdemux_types.c:196:qtdemux_type_get: unknown QuickTime node type btrt
0:00:00.351589330 15751 0x7f2d98092ad0 WARN                 qtdemux qtdemux.c:7977:qtdemux_parse_trak:<qtdemux0> unknown version 00000000
Segmentation fault (core dumped)

```

---

### Post by z987k on 2015-02-09
New symptom, nautilus also crashes with a segmentation fault (core dump) when trying to look at the properties of an .mp4.

---

