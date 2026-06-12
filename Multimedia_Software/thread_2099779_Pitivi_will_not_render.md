---
title: "Pitivi will not render"
date: 2012-12-30
forum: Multimedia Software
---

### Post by 98cwitr on 2012-12-30
Tried avi, mp4, ogg, and finally ffmeg VOB containers and none will render

Error snippet

> 
/GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition0/GnlSource:gnlsource: FileSourceFactory0/GstBin:bin1/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin0/GstAviDemux:avidemux16:
streaming stopped, reason not-linked) (/usr/lib/pitivi/python/pitivi/pipeline.py:858)


Any pointers? All the gstreamer basic stuff is up to date. Am I simply missing a codec or is this something bigger?

---

### Post by 98cwitr on 2012-12-30
ERROR: Could not load classifier cascade /usr/share/opencv/haarcascades/haarcascade_frontalface_alt2.xml
Event bus error: GStreamer encountered a general stream error. gstavidemux.c(5212): gst_avi_demux_loop (): /GstPipeline:pipeline7/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin18/GstAviDemux:avidemux8:
streaming stopped, reason not-linked
ERROR [12980] [0x   -48cb5500] "<Pipeline at 0xb1a8d2c>"        pipeline          Dec 30 14:26:02      _handleErrorMessage: error from /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition1/GnlSource:gnlsource: FileSourceFactory6/GstBin:bin7/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin6/GstAviDemux:avidemux12 (__main__.GstAviDemux): GStreamer encountered a general stream error. (gstavidemux.c(5212): gst_avi_demux_loop (): /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition1/GnlSource:gnlsource: FileSourceFactory6/GstBin:bin7/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin6/GstAviDemux:avidemux12:
streaming stopped, reason not-linked) (/usr/lib/pitivi/python/pitivi/pipeline.py:858)
Traceback (most recent call last):
  File "/usr/lib/pitivi/python/pitivi/ui/mainwindow.py", line 236, in _recordCb
    self.showEncodingDialog(self.project)
  File "/usr/lib/pitivi/python/pitivi/ui/mainwindow.py", line 226, in showEncodingDialog
    project.pipeline.pause()
  File "/usr/lib/pitivi/python/pitivi/pipeline.py", line 306, in pause
    self.setState(STATE_PAUSED)
  File "/usr/lib/pitivi/python/pitivi/pipeline.py", line 280, in setState
    raise PipelineError("Failure changing state of the gst.Pipeline to %r, currently reset to NULL" % state)
pitivi.pipeline.PipelineError: Failure changing state of the gst.Pipeline to <enum GST_STATE_PAUSED of type GstState>, currently reset to NULL
ERROR [12980] [0x   -48cb5500] "<Pipeline at 0xb1a8d2c>"        pipeline          Dec 30 14:26:09      _handleErrorMessage: error from /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition1/GnlSource:gnlsource: FileSourceFactory6/GstBin:bin7/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin6/GstAviDemux:avidemux12 (__main__.GstAviDemux): GStreamer encountered a general stream error. (gstavidemux.c(5212): gst_avi_demux_loop (): /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition1/GnlSource:gnlsource: FileSourceFactory6/GstBin:bin7/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin6/GstAviDemux:avidemux12:
streaming stopped, reason not-linked) (/usr/lib/pitivi/python/pitivi/pipeline.py:858)
ERROR [12980] [0x   -48cb5500] "<Pipeline at 0xb1a8d2c>"        pipeline          Dec 30 14:26:30      _handleErrorMessage: error from /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition1/GnlSource:gnlsource: FileSourceFactory6/GstBin:bin7/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin6/GstAviDemux:avidemux12 (__main__.GstAviDemux): GStreamer encountered a general stream error. (gstavidemux.c(5212): gst_avi_demux_loop (): /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition1/GnlSource:gnlsource: FileSourceFactory6/GstBin:bin7/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin6/GstAviDemux:avidemux12:
streaming stopped, reason not-linked) (/usr/lib/pitivi/python/pitivi/pipeline.py:858)
ERROR [12980] [0x   -48cb5500] "<Pipeline at 0xb1a8d2c>"        pipeline          Dec 30 14:26:30      _handleErrorMessage: error from /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition1/GnlSource:gnlsource: FileSourceFactory6/GstBin:bin7/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin6/GstAviDemux:avidemux12 (__main__.GstAviDemux): GStreamer encountered a general stream error. (gstavidemux.c(5212): gst_avi_demux_loop (): /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition1/GnlSource:gnlsource: FileSourceFactory6/GstBin:bin7/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin6/GstAviDemux:avidemux12:
streaming stopped, reason not-linked) (/usr/lib/pitivi/python/pitivi/pipeline.py:858)
ERROR [12980] [0x   -48cb5500] "<Pipeline at 0xb1a8d2c>"        pipeline          Dec 30 14:26:30      _handleErrorMessage: error from /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition0/GnlSource:gnlsource: FileSourceFactory0/GstBin:bin1/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin0/GstAviDemux:avidemux16 (__main__.GstAviDemux): GStreamer encountered a general stream error. (gstavidemux.c(5212): gst_avi_demux_loop ():

---

### Post by sdowney717 on 2012-12-30
Why not give flowblade a try instead?

[http://www.ubuntugeek.com/flowblade-multitrack-non-linear-video-editor-for-linux.html](http://www.ubuntugeek.com/flowblade-multitrack-non-linear-video-editor-for-linux.html)
[http://www.webupd8.org/2012/06/flowblade-cool-non-linear-video-editor.html](http://www.webupd8.org/2012/06/flowblade-cool-non-linear-video-editor.html)

---

### Post by 98cwitr on 2013-01-08
installing now...ill give it a shot :)

Well...ive got a base rendering now...but wondering how I can create a title screen and menu selection...if possible.

---

