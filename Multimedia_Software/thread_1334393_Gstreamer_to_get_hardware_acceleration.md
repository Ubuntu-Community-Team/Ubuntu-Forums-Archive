---
title: "Gstreamer to get hardware acceleration"
date: 2009-11-22
forum: Multimedia Software
---

### Post by amauk on 2009-11-22
Yes!!
Hopefully this will be ready for Lucid+1

[http://www.phoronix.com/scan.php?page=news_item&px=NzcyOA](http://www.phoronix.com/scan.php?page=news_item&px=NzcyOA)

> Last month we talked about a hackfest to improve Linux video playback that came about after a GNOME developer began work on using Cairo/Pixman for raw video in GStreamer and looking at other ways to leverage hardware acceleration within this major open-source multimedia framework. This Linux video meeting started in Barcelona on Thursday and is ending today, with some accomplishments.

Some of the code that has been (and continues to be) worked on is merging YUV support into Cairo/Pixman, a GLX Multi-thread extension, merging gst-plugins-cairo, XRenderPutImage/XV to Pixmap support, VA-API support for GStreamer, and getting the GStreamer Cairo plug-in to work on the Nokia N900. Another proposal that came about this week was a libgstva.so abstraction library that would allow video acceleration support in GStreamer across back-ends for VA-API, VDPAU, XvBA, and other video acceleration APIs, rather than targeting a lone API. Simply supporting VA-API and VDPAU for hardware acceleration in GStreamer will be enough for most users.

Notes from this Linux video hackfest can be found on the FreeDesktop.org Wiki. Chris Wilson also just posted a blog entry about this hackfest as well. Chris shares that the GStreamer developers are excited about Cairo, but in order to properly support their requirements, Pixman will be picking up a JIT (Just-In-Time) compiler for generating optimized code to handle obscure color-space conversions, etc. Multi-threading was then brought up and to address the concerns of the GStreamer developers with regards to thread-safety, X11 needs to be using xcb and a new GLX extension is needed for OpenGL to allow more efficient multi-threading. Lastly, a release of Cairo 1.10 is being planned for January to allow some of this new Cairo work to land in the first round of 2010 Linux distribution updates.

---

