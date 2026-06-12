---
title: "GStreamer need Help"
date: 2009-06-24
forum: Multimedia Software
---

### Post by AJ/ on 2009-06-24
Hi,
we are facing a problem with pause & resume in gstreamer. We see the vedio pause but resume doesnot happen.This ONLY happens for few videos, not for all.
I also did some analysis,
I call gst_element_get_state() before and after gst_element_set_state(), to see if the state change happens properly . BUT I see that the 'gst_element_get_state()' hangs for PAUSE(as I set it to TimeOutIndifinate till state changes) after calling the gst_element_set_state().
Can anyone tell me how I can g about this??????? Bit urgent.
THX, 
Aj

---

