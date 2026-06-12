---
title: "Mediatomb and MP4 vieos."
date: 2009-12-01
forum: Multimedia Software
---

### Post by bshosey on 2009-12-01
I have Mediatomb installed and running on my server. I have other machines that connect to mediatomb with totem. Some mp4 videos I can play and some will not play. But they will play if I copy them to the machine and then open the file up with totem but not through mediatomb.

Running ubuntu 9.10 desktop as server and ubuntu 9.10 on the machines trying to use the mediatomb server though totem. The error I get is Gstreamer encountered a general stream error.

the error when I run totem from terminal then trying to stream the file

request to play: X Men - Origins Wolverine.mp4 235 [http://192.168.1.10:49153/content/media/object_id/235/res_id/0/ext/file.mp4](http://192.168.1.10:49153/content/media/object_id/235/res_id/0/ext/file.mp4)
** Message: Error: GStreamer encountered a general stream error.
qtdemux.c(2816): gst_qtdemux_chain (): /GstPlayBin2:play/GstURIDecodeBin:uridecodebin0/GstDecodeBin2:decodebin20/GstQTDemux:qtdemux0:
no 'moov' atom withing first 10 MB


ubuntu 9.10 has been a rough release for me. I have other isuess that I have created threads for but no solutions.

Thank you in advanced for any help you can provide.

---

### Post by bshosey on 2009-12-04
OK. I figured it out. Totaly the fault of the encoder ( Me! ) I redid the videos with Web Optimization in HandBrake. Works great! so I consider this resolved with lesson learned.

---

