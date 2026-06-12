---
title: "Avidemux 2.6 on Precise 12.04: H.264 (x264) missing"
date: 2013-05-05
forum: Multimedia Software
---

### Post by michael37 on 2013-05-05
I installed avidemux 2.6 using the following instructions: [http://handytutorial.com/install-avidemux-2-6-in-ubuntu-12-10-12-04/](http://handytutorial.com/install-avidemux-2-6-in-ubuntu-12-10-12-04/)

I don't see x264 as one of available encoders. If I look at startup log, there are something that looks like a library loading error.

Have anyone seen a problem like this?
```

[videoEncoder6]Name :ffMpeg4 ApiVersion :5 Description :Simple ffmpeg based mpeg4 Encoder (c) 2009 Mean
[VideoEncoder6] Registered filter /usr/lib/ADM_plugins6/videoEncoders/libADM_ve_ffMpeg4.so as  Simple ffmpeg based mpeg4 Encoder (c) 2009 Mean
[videoEncoder6]Name :HUFFYUV ApiVersion :5 Description :FF Huffyuv (c) 2009 Mean
[VideoEncoder6] Registered filter /usr/lib/ADM_plugins6/videoEncoders/libADM_ve_huff.so as  FF Huffyuv (c) 2009 Mean
[videoEncoder6]Name :xvid4 ApiVersion :5 Description :Xvid4 based mpeg4 Encoder (c) 2010 Mean/Gruntster
[VideoEncoder6] Registered filter /usr/lib/ADM_plugins6/videoEncoders/libADM_ve_xvid4.so as  Xvid4 based mpeg4 Encoder (c) 2010 Mean/Gruntster
[videoEncoder6]Name :x264 ApiVersion :5 Description :x264 based mpeg4 AVC Encoder (c) 2010 Mean/Gruntster
[COLOR="#FF0000"]/usr/lib/ADM_plugins6/videoEncoders/libADM_ve_x264_other.so:WrongUI[/COLOR]
```

---

