---
title: "GStreamer Reinstall For Sound"
date: 2008-05-10
forum: Multimedia Software
---

### Post by Luna.jp on 2008-05-10
Good Morning,

I am having a problem with my sound and gstreamer. Actually, my sound works, but I can not control it while in Ubuntu. I get the classic error message of

"No volume control GStreamer plugins and/or devices found."

when I click my sound control button. This issue came up when I upgraded my gstreamer to .15 vice .14 for the latest Cheese for my webcam. Not my sound control is broken and so is my Cheese.

When I run gstreamer-properties I get this:

```

luna@dellnix:~$ gstreamer-properties
gstreamer-properties-Message: Skipping unavailable plugin 'autoaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasink'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'osssink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'autovideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'ximagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'xvimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'videotestsrc is-live=true'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4l2src'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'osssrc'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Skipping unavailable plugin 'audiotestsrc wave=triangle is-live=true'
gstreamer-properties-Message: Skipping unavailable plugin 'audiotestsrc wave=silence is-live=true'

```

I've also uninstalled and reinstalled gstreamer0.10-plugins-good but still no luck. I'm positive it is a gstreamer issue because I can see my sound card and it still plays music, but I can't control it from gnome.

Any ideas? How would I reinstall gstreamer back to the way it was??

OTHER INFO:

**aplay -l**

```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Modem [Intel ICH6 Modem], device 0: Intel ICH - Modem [Intel ICH6 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

lspci -v

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
        Subsystem: Dell Latitude D610 Laptop
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ed00 [size=256]
        I/O ports at ec40 [size=64]
        Memory at dfebfe00 (32-bit, non-prefetchable) [size=512]
        Memory at dfebfd00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```

and when I run **cheese** I get this

```
creating new directory: /root/.gnome2/cheese/images/
creating new directory: /root/.gnome2/cheese/videos/
** Message: Probing the webcam, please ignore the following, not applicabable tries
** Message: test pipeline for v4l2src failed:
[v4l2src ! fakesink]: no element "v4l2src"
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=640,height=480 ! fakesink]: no element "v4lsrc"
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-yuv,width=640,height=480 ! fakesink]: no element "v4lsrc"
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=320,height=240 ! fakesink]: no element "v4lsrc"
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=1280,height=960 ! fakesink]: no element "v4lsrc"
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=174,height=144 ! fakesink]: no element "v4lsrc"
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! video/x-raw-rgb,width=160,height=120 ! fakesink]: no element "v4lsrc"
** Message: test pipeline for v4lsrc failed:
[v4lsrc ! fakesink]: no element "v4lsrc"
using source: videotestsrc

(cheese:10598): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed

(cheese:10598): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed

(cheese:10598): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed

(cheese:10598): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed

(cheese:10598): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed

(cheese:10598): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed

(cheese:10598): GLib-GObject-CRITICAL **: g_object_set: assertion `G_IS_OBJECT (object)' failed

(cheese:10598): GStreamer-CRITICAL **: gst_bin_add: assertion `GST_IS_ELEMENT (element)' failed

(cheese:10598): GStreamer-CRITICAL **: gst_element_link_many: assertion `GST_IS_ELEMENT (element_1)' failed

** (cheese:10598): CRITICAL **: gst_x_overlay_set_xwindow_id: assertion `overlay != NULL' failed

```

---

### Post by Luna.jp on 2008-05-11
Also, I don't believe this is a user/group issue because those seem to be in order. Sound works perfectly, I just can't control it from gnome and it has to do with gstreamer.

---

### Post by Luna.jp on 2008-05-11
I seem to be having the same issue as listed here but I am unable to understand how to fix this problem.

[http://ubuntuforums.org/showthread.php?t=599377]("http://ubuntuforums.org/showthread.php?t=599377")


**gst-inspect** gives me this

```
coreelements:  multiqueue: MultiQueue
coreelements:  typefind: TypeFind
coreelements:  tee: Tee pipe fitting
coreelements:  filesink: File Sink
coreelements:  queue: Queue
coreelements:  identity: Identity
coreelements:  filesrc: File Source
coreelements:  fdsink: Filedescriptor Sink
coreelements:  fdsrc: Filedescriptor Source
coreelements:  fakesink: Fake Sink
coreelements:  fakesrc: Fake Source
coreelements:  capsfilter: CapsFilter
coreindexers:  fileindex: A index that stores entries in file
coreindexers:  memindex: A index that stores entries in memory
staticelements:  bin: Generic bin
staticelements:  pipeline: Pipeline object

Total count: 3 plugins, 16 features
```

---

### Post by Luna.jp on 2008-05-11
BUMP for help. Final.

---

### Post by stimpak on 2008-11-12
anyone? so help would be nice? i have the same problem :(

---

### Post by edea on 2009-04-28
Hi,
Anyone solved this? I have the same problem now with Jaunty...

---

### Post by edea on 2009-04-29
Solved! Erase the folders in /usr/local where you see there's gstreamer files related.

---

### Post by Mecasickle on 2010-03-21
Did it work for you guys!?!?! About erasing the gstreamer files in the /usr/local ??

---

### Post by raydrezack on 2010-05-30
Worked for me

```
cd /usr/local/libs
rm -R -f *gst*
```

---

