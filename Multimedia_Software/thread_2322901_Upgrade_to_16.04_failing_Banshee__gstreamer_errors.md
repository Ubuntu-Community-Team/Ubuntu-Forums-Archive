---
title: "Upgrade to 16.04: failing Banshee / gstreamer errors"
date: 2016-05-01
forum: Multimedia Software
---

### Post by kmd on 2016-05-01
Hi, 

I recently upgraded a clean installed ubuntu 15.10 to latest 16.04. However this is causing serious problems with Banshee, it refuses to play any sound. I've been looking around for clues but unfortunately I can not find any hints to solve this problem. Tried re-installing Banshee, tried a fresh Banshee profile, tried re-installing gstreamer (which did not work, dependency errors). Weirdly, Banshee/Gstreamer work (!) on another profile, only not on the profile I use daily.

I see these errors after starting Banshee after tapping 'play'.


[Info  16:34:37.179] nereid Client Started

(Banshee:17455): GStreamer-CRITICAL **: gst_bin_add_many: assertion 'GST_IS_ELEMENT (element_1)' failed

(Banshee:17455): GStreamer-CRITICAL **: gst_element_link_many: assertion 'GST_IS_ELEMENT (element_2)' failed
[Info  16:34:37.205] GStreamer version 1.8.0.0, gapless: True, replaygain: False
[Error 16:34:40.332] GStreamer resource error: NotFound

(Banshee:17455): GStreamer-CRITICAL **: gst_bin_add_many: assertion 'GST_IS_ELEMENT (element_1)' failed

(Banshee:17455): GStreamer-CRITICAL **: gst_element_link_many: assertion 'GST_IS_ELEMENT (element_2)' failed
[Error 16:34:40.649] GStreamer resource error: NotFound

etc etc etc

Any help would be great. Upgrading to 15.04 also totally trashed Banshee (regression problems) and now with 16.04 again unfortunately. It's a program a use daily. Any hints?

Thank you
Michael

---

### Post by kmd on 2016-05-27
Problem seems fixed after an ubuntu update, gstreamer update (28thMay16).

---

