---
title: "Soundconverter &quot;blinks out&quot; when selecting MP4 to convert to MP3"
date: 2023-07-03
forum: Multimedia Software
---

### Post by Randy M on 2023-07-03
Today's updates caused a few problems, but I haven't used Soundconverter in a while so I don't know when the problem began. When I select one or more files to convert, it simply exits with no message. I tried running it in debug mode from a terminal and this was the response. Any ideas or suggestions on how to get it working again? This is on Ubuntu 22.04.2. Thanks!

randy@randy-HP-Pro3500-Series:~$ soundconverter --debug
ERROR: Disabling aac-enc output. Do you have "gst-plugins-bad" installed?
INFO: soundconverter, line 237, soundconverter 4.0.3
INFO: filelist.py, line 198, analysing file integrity
INFO: filelist.py, line 218, adding: 7 files

(soundconverter:12439): GStreamer-CRITICAL **: 18:14:55.055: gst_caps_from_string: assertion 'string' failed

(soundconverter:12439): GStreamer-CRITICAL **: 18:14:55.055: gst_pad_template_new: assertion 'caps != NULL' failed

(soundconverter:12439): GStreamer-CRITICAL **: 18:14:55.055: gst_mini_object_unref: assertion 'mini_object != NULL' failed

(soundconverter:12439): GStreamer-CRITICAL **: 18:14:55.055: gst_element_class_add_pad_template: assertion 'GST_IS_PAD_TEMPLATE (templ)' failed

(soundconverter:12439): GStreamer-Video-CRITICAL **: 18:14:55.055: gst_video_decoder_init: assertion 'pad_template != NULL' failed

(soundconverter:12439): GStreamer-Video-CRITICAL **: 18:14:55.055: gst_video_decoder_init: assertion 'pad_template != NULL' failed

(soundconverter:12439): GStreamer-WARNING **: 18:14:55.055: Element vaapidecode0 has an ALWAYS template src, but no pad of the same name

(soundconverter:12439): GStreamer-WARNING **: 18:14:55.055: Element vaapidecode1 has an ALWAYS template src, but no pad of the same name

(soundconverter:12439): GStreamer-Video-CRITICAL **: 18:14:55.055: gst_video_decoder_init: assertion 'pad_template != NULL' failed

(soundconverter:12439): GStreamer-WARNING **: 18:14:55.055: Element vaapidecode2 has an ALWAYS template src, but no pad of the same name
Segmentation fault (core dumped)
randy@randy-HP-Pro3500-Series:~$

---

### Post by #&amp;thj^% on 2023-07-03
Did you notice>>" Do you have "gst-plugins-bad" installed?"
```
apt policy gstreamer1.0-plugins-bad
gstreamer1.0-plugins-bad:
  Installed: 1.22.1-1ubuntu1
  Candidate: 1.22.1-1ubuntu1
  Version table:
 *** 1.22.1-1ubuntu1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
        100 /var/lib/dpkg/status

```
Mine works  MP4 to convert to MP3 
Also have you looked at "soundKonverter"
```
apt show soundkonverter
Package: soundkonverter
Version: 3.0.1-3
Priority: optional
Section: universe/kde
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian KDE Extras Team <pkg-kde-extras@lists.alioth.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 4,207 kB
Depends: kio, libc6 (>= 2.34), libcdparanoia0 (>= 3.10.2+debian), libkf5cddb5 (>= 4:17.08.3), libkf5completion5 (>= 4.97.0), libkf5configcore5 (>= 4.97.0), libkf5configwidgets5 (>= 4.96.0), libkf5coreaddons5 (>= 4.99.0), libkf5i18n5 (>= 4.97.0), libkf5kdelibs4support5 (>= 5.13.0), libkf5kiocore5 (>= 4.96.0), libkf5kiowidgets5 (>= 4.96.0), libkf5notifications5 (>= 4.96.0), libkf5service-bin, libkf5service5 (>= 4.99.0), libkf5solid5 (>= 4.97.0), libkf5textwidgets5 (>= 4.96.0), libkf5widgetsaddons5 (>= 5.1.0), libkf5xmlgui5 (>= 4.98.0), libphonon4qt5-4 (>= 4:4.8.0), libqt5core5a (>= 5.15.1), libqt5gui5 (>= 5.14.1) | libqt5gui5-gles (>= 5.14.1), libqt5widgets5 (>= 5.14.1), libqt5xml5 (>= 5.0.2), libstdc++6 (>= 4.6), libtag1v5 (>= 1.11), phonon4qt5
Recommends: cdparanoia, faad, ffmpeg, flac, kio-audiocd, mp3gain, mplayer, mppenc, speex, timidity, vorbis-tools, vorbisgain, wavpack
Homepage: https://github.com/dfaust/soundkonverter
Download-Size: 786 kB
APT-Sources: http://us.archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
Description: audio converter frontend for KDE
 soundKonverter is a frontend to various audio converters.
 .
 The key features are:
  - Audio conversion
  - Replay Gain calculation
  - CD ripping
 .
 soundKonverter supports reading and writing tags for many formats, so the tags
 are preserved when converting files.
 .
 See README.Debian for more information on supported formats.


```
This is what I use now..

---

### Post by Randy M on 2023-07-04
I did notice the mention of gstreamer1.0-plugins-bad. Here's what a check shows. 

randy@randy-HP-Pro3500-Series:~$ apt policy gstreamer1.0-plugins-bad
gstreamer1.0-plugins-bad:
  Installed: 1.20.3-0ubuntu1
  Candidate: 1.20.3-0ubuntu1
  Version table:
 *** 1.20.3-0ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 Packages
        100 /var/lib/dpkg/status
     1.20.1-1ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages
randy@randy-HP-Pro3500-Series:~$ 

I'll give Soundkonverter a try. Thanks!

---

### Post by #&amp;thj^% on 2023-07-04
> **Randy M said:**
> 

I'll give Soundkonverter a try. Thanks!
I'm curious if it works for you, let us know please.
Randy M I also remembered a work-around for soundconverter, it was to first format to .wav.then to .mp3.
So I hope Soundkonverter does the trick for you.

---

### Post by Randy M on 2023-07-04
SoundKonverter does the job, but locked up the system twice. I had to power down by holding the power button down until it turned off, pressing the power button for a normal shutdown didn't work. Looks like I have more troubleshooting to do, but I'll mark this thread as resolved.

Thanks again!

---

