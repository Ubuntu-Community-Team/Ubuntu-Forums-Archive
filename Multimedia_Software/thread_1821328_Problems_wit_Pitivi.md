---
title: "Problems wit Pitivi"
date: 2011-08-08
forum: Multimedia Software
---

### Post by Crazy K on 2011-08-08
Hey guys, I'm having a problem with Pitivi movie editor. I'm trying to render a video that is of MP4 format (Editing it with title and such). And whenever I render it I get these errors: 

```
Problem:GStreamer encountered a general stream error.
Extra information:qtdemux.c(2959): gst_qtdemux_loop (): /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition1/GnlSource:gnlsource: FileSourceFactory3/GstBin:bin4/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin5/GstQTDemux:qtdemux5:
streaming stopped, reason not-negotiated
```

And this: 
```
Problem:Could not demultiplex stream.
Extra information:qtdemux.c(520): gst_qtdemux_post_no_playable_stream_error (): /GstPipeline:pipeline0/GstBin:bin0/GnlComposition:gnlcomposition1/GnlSource:gnlsource: FileSourceFactory3/GstBin:bin4/pitivi+elements+singledecodebin+SingleDecodeBin:pitivi+elements+singledecodebin+singledecodebin5/GstQTDemux:qtdemux5:
no known streams found
```

When I went to render I did this: 

I go to modify; for video output I put 720p
Audio Output I put CD

For these I put: 

Container: MP4 Muxer [MP4Mux]
Audio Codec: FFmpeg ALAC (Apple Lossless Audio Codec) encoder [ffenc_alac]
Video Codec: FFmpeg MPEG-4 part 2 encoder [ffenc_mpeg4]

I have another computer with ubuntu and there's more choices on that. What do I need to do to fix this? Thanks! 

I need replies soon though, need to get this video made as soon as I can. 

Just tried different formats and that seemed to work. I'll update you all if any problems arise.

---

