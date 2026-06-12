---
title: "how to make video fullscreen in gstreamer"
date: 2010-01-07
forum: Multimedia Software
---

### Post by shariefbe on 2010-01-07
hello,
  I have just installed my gstreamer on my ARM board. In that i used to play the video by using command 
"gst-launch filesrc location=/root/yuvraj.mp4 ! mfw_mp4demuxer ! queue max-size-time=0 ! mfw_vpudecoder ! mfw_v4lsink"

it is working fine. but the screen is very small and it is in middle,  How to make that full screen and the letters which is in terminal is also coming along with the video. how rectify that problem? please he lp

---

### Post by shariefbe on 2010-01-07
yes i found the gst-inspect for v4lsink
see
```

root@freescale ~$ gst-inspect mfw_v4lsink
MFW_GST_V4LSINK_PLUGIN V1.6.0-r1 build on Jan  6 2010 16:52:40.
Factory Details:
  Long name:    Freescale: v4l_sink
  Class:        Sink/Video
  Description:  Video rendering device plugin used to displayYUV 4:2:0 data with the support to crop the input image used in the direct rendering of Padded a
  Author(s):    i.MX series
  Rank:         primary (256)

Plugin Details:
  Name:                 mfw_v4lsink
  Description:          Video display plug in based on V4L2
  Filename:             /usr/lib/fsl_mm_linux/lib/gstreamer-0.10/libmfw_gst_v4lsink.so
  Version:              V1.6.0-r1
  License:              unknown
  Source module:
  Binary package:       Freescale Semiconductor
  Origin URL:           www.freescale.com 

GObject
 +----GstObject
       +----GstElement
             +----GstBaseSink
                   +----GstVideoSink
                         +----MFW_GST_V4LSINK_INFO_T

Pad Templates:
  SINK template: 'sink'
    Availability: Always
    Capabilities:
      video/x-raw-yuv
                 format: I420
                  width: [ 1, 2147483647 ]
                 height: [ 1, 2147483647 ]
              framerate: [ 0/1, 100/1 ]
      video/x-raw-yuv
                 format: YV12
                  width: [ 1, 2147483647 ]
                 height: [ 1, 2147483647 ]
              framerate: [ 0/1, 100/1 ]
      video/x-raw-yuv
                 format: YUY2
                  width: [ 1, 2147483647 ]
                 height: [ 1, 2147483647 ]
              framerate: [ 0/1, 100/1 ]
      video/x-raw-yuv
                 format: NV12
                  width: [ 1, 2147483647 ]
                 height: [ 1, 2147483647 ]
              framerate: [ 0/1, 100/1 ]
      video/x-raw-rgb
                    bpp: [ 1, 32 ]
                  depth: [ 1, 32 ]


Element Flags:
  no flags set

Element Implementation:
  Has change_state() function: mfw_gst_v4lsink_change_state
  Has custom save_thyself() function: gst_element_save_thyself
  Has custom restore_thyself() function: gst_element_restore_thyself

Element has no clocking capabilities.
Element has no indexing capabilities.
Element has no URI handling capabilities.

Pads:
  SINK: 'sink'
    Implementation:
      Has chainfunc(): gst_base_sink_chain
      Has custom eventfunc(): gst_base_sink_event
      Has bufferallocfunc(): gst_base_sink_pad_buffer_alloc
    Pad Template: 'sink'

Element Properties:
  name                : The name of the object
                        flags: readable, writable
                        String. Default: null Current: "mfw_gst_v4lsink_info_t0"
  preroll-queue-len   : Number of buffers to queue during preroll
                        flags: readable, writable
                        Unsigned Integer. Range: 0 - 4294967295 Default: 0 Current: 0
  sync                : Sync on the clock
                        flags: readable, writable
                        Boolean. Default: true Current: true
  max-lateness        : Maximum number of nanoseconds that a buffer can be late before it is dropped (-1 unlimited)
                        flags: readable, writable
                        Integer64. Range: -1 - 9223372036854775807 Default: -1 Current: 20000000
  qos                 : Generate Quality-of-Service events upstream
                        flags: readable, writable
                        Boolean. Default: false Current: true
  async               : Go asynchronously to PAUSED
                        flags: readable, writable
                        Boolean. Default: true Current: true
  ts-offset           : Timestamp offset in nanoseconds
                        flags: readable, writable
                        Integer64. Range: -9223372036854775808 - 9223372036854775807 Default: 0 Current: 0
  last-buffer         : The last buffer received in the sink
                        flags: readable
                        MiniObject of type "GstBuffer"
  blocksize           : Size in bytes to pull per buffer (0 = default)
                        flags: readable, writable
                        Unsigned Integer. Range: 0 - 4294967295 Default: 4096 Current: 4096
  render-delay        : Additional render delay of the sink in nanoseconds
                        flags: readable, writable
                        Unsigned Integer64. Range: 0 - -1 Default: 0 Current: 0
  fullscreen          : If true it will be Full screen
                        flags: readable, writable
                        Boolean. Default: false Current: false
  disp-width          : gets the width of the image to be displayed
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  disp-height         : gets the height of the image to be displayed
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  axis-top            : gets the top co-ordinate of the origin of display
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  axis-left           : gets the left co-ordinate of the origin of display
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  rotate              : gets the angle at which display is to be rotated
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  crop-left-by-pixel  : set the input image cropping in the left (width)
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  crop-right-by-pixel : set the input image cropping in the right (width)
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  crop-top-by-pixel   : set the input image cropping in the top (height)
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  crop-bottom-by-pixel: set the input image cropping in the bottom (height)
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  fullscreen-width    : gets the full screen width of the display
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 240
  fullscreen-height   : gets the full screen height of the display
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 320
  base-offset         : gets the base offet for the V4L Driver for a given BSP
                        flags: readable, writable
                        Integer. Range: 0 - 1 Default: 0 Current: 0
  tv-out              : set output to TV-OUT
                        flags: readable, writable
                        Boolean. Default: false Current: false
  tv-mode             : set mode to TV-OUT
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 2
  add-buffer-len      : set addtional buffer length
                        flags: readable, writable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  setpara             : set parameter of V4L2, 1: Set V4L 2: Set ColorKey

(gst-inspect-0.10:2159): GLib-GObject-CRITICAL **: g_value_set_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
                        flags: readable, writable
                        Integer. Range: 0 - 2 Default: 0 Current: 0
  width               : gets the source image width
                        flags: readable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
  height              : gets the source image height
                        flags: readable
                        Integer. Range: 0 - 2147483647 Default: 0 Current: 0
root@freescale ~$ 

```
but now i dont know how to use this "fullscreen" flag with this mfw_v4lsink. please help me

---

