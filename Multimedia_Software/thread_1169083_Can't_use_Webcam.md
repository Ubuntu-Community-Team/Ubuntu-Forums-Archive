---
title: "Can't use Webcam"
date: 2009-05-24
forum: Multimedia Software
---

### Post by R2D2! on 2009-05-24
A month ago I could use my webcam (I took a photo w&#305;th Cheese), but now &#305;t won't work. I th&#305;nk &#305;t's because of an update.

Runn&#305;ng cheese on term&#305;nal outputs th&#305;s:
```
** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:7956): WARNING **: could not generate thumbnail for /home/ilhuitemoc/Videos/Webcam/0033.ogv (video/ogg)

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:7956): WARNING **: could not generate thumbnail for /home/ilhuitemoc/Videos/Webcam/2008-11-24-203943.ogv (video/ogg)

** Message: Error: Stream contains no data.
gsttypefindelement.c(786): gst_type_find_element_activate (): /GstPlayBin:play/GstDecodeBin:decodebin0/GstTypeFindElement:typefind:
Can't typefind empty stream


** (cheese:7956): WARNING **: could not generate thumbnail for /home/ilhuitemoc/Videos/Webcam/2008-11-24-204037.ogv (video/ogg)


** (cheese:7956): WARNING **: could not generate thumbnail for /home/ilhuitemoc/Videos/Webcam/0023.ogv (video/ogg)

libv4l2: error turning on stream: **Cannot allocate memory**

```

And runn&#305;ng luvcview outputs:```
luvcview 0.2.4

SDL information:
  Video driver: x11
  A window manager is available
Device information:
  Device path:  /dev/video0
Stream settings:
  Frame format: YUYV (MJPG is not supported by device)
  Frame size:   640x480
  Frame rate:   30 fps
Unable to start capture: **Cannot allocate memory**
Error grabbing
Cleanup done. Exiting ...

```

What does &#8220;Cannot allocate memory&#8221; mean?

However, I can use the camera w&#305;th Skype and w&#305;th Adobe Flash, so &#305;t's detected by the system

&#8212;Ilhu&#305;temoc &#948;

---

### Post by R2D2! on 2009-08-29
Anyone???:confused:

---

