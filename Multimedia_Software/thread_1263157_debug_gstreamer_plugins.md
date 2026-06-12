---
title: "debug gstreamer plugins"
date: 2009-09-10
forum: Multimedia Software
---

### Post by 2008cwang on 2009-09-10
I want to debug my gstreamer codec plugin using remote cross-target debugging with GDB and GDBserver. 
We use gst-launch to build the gstream pipeline application. When I use remote cross-target debugging with GDB and GDBserver to debug it, I can only see the source code of gst-launch 's very up layer called gst-run.c, and my own plugin code seems invisible. So, I cannot set breakpoint etc.
 
Is this because I don't have the source for gst-launch?
 
Do I really need to write my own gstreamer application in order to debug it?
I am new to the area, I appreciate any help you might offer. Thanks.
 
 
cindy

---

### Post by monster on 2009-11-10
Have you found a solution how to debug your plugin?
If yes, could you please post it here?

---

