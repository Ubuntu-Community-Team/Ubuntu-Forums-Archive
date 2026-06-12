---
title: "Tracing problems with streaming"
date: 2009-08-04
forum: Multimedia Software
---

### Post by bcschmerker on 2009-08-04
I have been experimenting with a Dynex DX-WEB1C USB camera (a type supported in BerliOS UVCVideo); I found that the DX-WEB1C is not always called properly when streaming to certain Websites, particularly LiveVideo (which spools up the camera for an upload-speed test only to lose the camera at recording time).  How does one go about tracing the failure to reinitialize?  I'd prefer to have a straight report for the appropriate BugZilla service.

Addendum:  Same problem occurs with a Logitech QuickCam Communicate Deluxe S7500 (SPCA527 CCD; P/N 960-000247), ID#046d:09a2 (previous firmware was ID#046d:0992).

---

### Post by bcschmerker on 2009-08-18
Update:  I found out at Launchpad.net that the [GNU Numeric Object Modeling Environment Group](http://www.gnome.org/) is already working on  [known bugs in GStreamer](https://bugs.launchpad.net/gstreamer) that may be contributing to my problem as explained above; GNOME has released a fix for [GStreamer common files](http://bugzilla.gnome.org/show_bug.cgi?id=482660), while the Firefox MPEG plugin is triaged (see also the [bug log for GStreamer0.10-FFMPEG](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10-ffmpeg) at Launchpad).  Will update upon testing a Fix Release on my Everex. ):P

---

### Post by bcschmerker on 2011-01-17
I found that the GStreamer problem was fixed sometime after 8.04-LTS, as the streaming problem does not occur in 10.04-LTS. ):P

---

