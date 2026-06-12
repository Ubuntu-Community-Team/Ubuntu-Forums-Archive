---
title: "Gstreamer LADSPA problems"
date: 2007-12-09
forum: Multimedia Production
---

### Post by -=Ghostlike=- on 2007-12-09
Hello,

For a school project we are working on a gstreamer-java application, I'm trying to implement some extra functions, but how do you add a ladspa plugin to a gstreamer pipeline?

my pipeline right now is:
gst-launch-0.10 filesrc location=01\ -\ A\ Million\ miles\ Away.ogg ! decodebin ! audioconvert ! alsasink

when I insert ladspa-freeverb3 anywhere it does not run, behind the audioconvert it says failed to link ladspa-freeverb30 to alsasink0, and in front of audioconvert it gives an "** (gst-launch-0.10:17438): WARNING **: foo" error.

Does anyone have any clues?

---

