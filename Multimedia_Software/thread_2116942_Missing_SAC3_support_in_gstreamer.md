---
title: "Missing SAC3 support in gstreamer"
date: 2013-02-17
forum: Multimedia Software
---

### Post by edfast on 2013-02-17
Hello,

After downloading an old .mp4 video tried to play it in default videoplayer and got no audio and the message that Python 2.7 needed additional plugins to play SAC3 audio files.

Trying to play via terminal returned as follows```
** Message: Missing plugin: gstreamer|0.10|totem|audio/x-gst-fourcc-sac3-decoder-audio/x-gst-fourcc-sac3 /usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
CRITICAL:Could not find any packages to operate on
** Message: No installation candidate for missing plugins found.

```Anyone out there had a similar problem, and ideally found a solution to it?

---

