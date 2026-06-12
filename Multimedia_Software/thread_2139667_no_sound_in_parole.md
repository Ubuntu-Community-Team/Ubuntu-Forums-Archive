---
title: "no sound in parole"
date: 2013-04-27
forum: Multimedia Software
---

### Post by frabato56 on 2013-04-27
Hi All,

I just did a clean install of xubuntu 13.04 last night and all is well except that there is no sound while playing a dvd in parole. The same dvd plays fine with sound in vlc and gmusicbrowser has sound. I've installed restricted extras and libdvdcss but still no sound. Does anyone have any clues for me?

Thanks

---

### Post by pqwoerituytrueiwoq on 2013-04-27
did check the volume in parole and make sure it is not muted

---

### Post by frabato56 on 2013-04-27
> **pqwoerituytrueiwoq said:**
> did check the volume in parole and make sure it is not muted Yes, the volume is up. The problem is specific to parole. I have sound in vlc and gmusicbrowser, just wondering if anyone else is having this problem or knows of this issue. Okay, I just checked parole with a flac file and the sound is fine, I checked a different dvd and the sound is fine. I play "Hell Freezes Over" by the Eagles (dvd) and there's no sound. I play the same dvd in vlc and the sound is fine.

?????????????

Thanks

---

### Post by pqwoerituytrueiwoq on 2013-04-27
as in these locations, there are multiple volume controls
[[IMG]http://en.zimagez.com/miniature/screenshot-04272013-085048pm.png[/IMG]]("http://en.zimagez.com/zimage/screenshot-04272013-085048pm.php")
if those are all good, parole must mt be registering the audio codec right

---

### Post by frabato56 on 2013-04-27
> **pqwoerituytrueiwoq said:**
> as in these locations, there are multiple volume controls
[[IMG]http://en.zimagez.com/miniature/screenshot-04272013-085048pm.png[/IMG]]("http://en.zimagez.com/zimage/screenshot-04272013-085048pm.php")
if those are all good, parole must mt be registering the audio codec right
The volume is turned up in all three places but the sound is not registering in the pulseaudio mixer as it does when sound is playing from other sources (not the Eagles dvd). Could my Eagles dvd require a different codec than my other dvd's?

---

### Post by pqwoerituytrueiwoq on 2013-04-27
it could it depends how how it was encoded, i just remembered something
[https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/10.04/musicvideophotos/C/video-dvd.html)

---

### Post by frabato56 on 2013-04-27
Install the libdvdnav4, libdvdread4, gstreamer0.10-plugins-bad and gstreamer0.10-plugins-ugly packages.
All of those programs are installed so I guess it still remains a mystery. My workaround is to use vlc but I do like parole so I'm still curious about this issue.

Thanks for the replies.

---

### Post by Yellow Pasque on 2013-04-28
You might want to look here for an example of how to get a debug log: [https://bugzilla.gnome.org/show_bug.cgi?id=575568](https://bugzilla.gnome.org/show_bug.cgi?id=575568) It would be interesting to know what format the audio is encoded in.

---

### Post by frabato56 on 2013-04-28
> **Temüjin said:**
> You might want to look here for an example of how to get a debug log: [https://bugzilla.gnome.org/show_bug.cgi?id=575568](https://bugzilla.gnome.org/show_bug.cgi?id=575568) It would be interesting to know what format the audio is encoded in.
Well I wasn't able to figure out how to get a debug log but using lsdvd I found that audio is DTS (frequency 48000)

---

### Post by Yellow Pasque on 2013-04-28
Do you have gstreamer0.10-ffmpeg installed?
```
$ gst-inspect-0.10 ffdec_dca
Factory Details:
  Long name:	FFmpeg DCA (DTS Coherent Acoustics) decoder
  Class:	Codec/Decoder/Audio
  Description:	FFmpeg dca decoder
  Author(s):	Wim Taymans <wim.taymans@gmail.com>, Ronald Bultje <rbultje@ronald.bitfreak.net>, Edward Hervey <bilboed@bilboed.com>
  Rank:		none (0)

Plugin Details:
  Name:			ffmpeg
  Description:		All FFmpeg codecs and formats (local snapshot)
  Filename:		/usr/lib/x86_64-linux-gnu/gstreamer-0.10/libgstffmpeg.so
  Version:		0.10.13
  License:		GPL
  Source module:	gst-ffmpeg
  Binary package:	FFmpeg
  Origin URL:		http://ffmpeg.org/

GObject
 +----GstObject
       +----GstElement
             +----ffdec_dca

Pad Templates:
  SRC template: 'src'
    Availability: Always
    Capabilities:
      audio/x-raw-float
               channels: [ 1, 6 ]
                   rate: [ 4000, 96000 ]
             endianness: 1234
                  width: 32
      audio/x-raw-int
               channels: [ 1, 6 ]
                   rate: [ 4000, 96000 ]
                 signed: true
             endianness: 1234
                  width: 16
                  depth: 16

  SINK template: 'sink'
    Availability: Always
    Capabilities:
      audio/x-dts
               channels: [ 1, 6 ]
                   rate: [ 4000, 96000 ]


Element Flags:
  no flags set

Element Implementation:
  Has change_state() function: 0x7f20c2e29e90
  Has custom save_thyself() function: gst_element_save_thyself
  Has custom restore_thyself() function: gst_element_restore_thyself

Element has no clocking capabilities.
Element has no indexing capabilities.
Element has no URI handling capabilities.

Pads:
  SRC: 'src'
    Implementation:
      Has custom eventfunc(): gst_ffmpegdec_src_event
      Has custom queryfunc(): gst_ffmpegdec_query
      Has custom iterintlinkfunc(): gst_pad_iterate_internal_links_default
      Has getcapsfunc(): gst_pad_get_fixed_caps_func
      Has acceptcapsfunc(): gst_pad_acceptcaps_default
    Pad Template: 'src'
  SINK: 'sink'
    Implementation:
      Has chainfunc(): gst_ffmpegdec_chain
      Has custom eventfunc(): gst_ffmpegdec_sink_event
      Has custom queryfunc(): gst_pad_query_default
      Has custom iterintlinkfunc(): gst_pad_iterate_internal_links_default
      Has setcapsfunc(): gst_ffmpegdec_setcaps
      Has acceptcapsfunc(): gst_pad_acceptcaps_default
    Pad Template: 'sink'

Element Properties:
  name                : The name of the object
                        flags: readable, writable
                        String. Default: "ffdec_dca0"

```

---

### Post by frabato56 on 2013-04-28
> **Temüjin said:**
> Do you have gstreamer0.10-ffmpeg installed?

Yes.

---

