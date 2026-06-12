---
title: "Can't open MPEG file in Pitivi"
date: 2011-01-15
forum: Multimedia Software
---

### Post by calande on 2011-01-15
Hello,

I have a problem opening an MPEG file in Pitivi. When I try to open it, I get this error message:

> **URI**:Code%2012%20-%20Sexe%2C%20les%20nouvelles%20tendances.mpg
**Problem**:An internal error occurred while analyzing this file: Your GStreamer installation is missing a plug-in.
**Extra information**:gstdecodebin2.c(2944): gst_decode_bin_expose (): /GstPipeline:Discoverer-file:///home/charles/diskstation/public/Videos/%C3%80%20voir/Code%2012%20-%20Sexe%2C%20les%20nouvelles%20tendances.mpg/GstDecodeBin2:dbin:
no suitable plugins found


What extra package do I need? Thanks,

---

### Post by cotcot on 2011-01-15
Have you installed the gstreamer0.10-plugins-ugly ?

These are required to play back formats that are not free. 

See more info [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").

---

### Post by calande on 2011-01-16
Thanks. I'm now able to open the file but Pitivi is just too slow compared to other video editing applications... Do you know another good application instead (not Avidemux either)? I just want to remove commercials from videos. Thanks.

---

### Post by BicyclerBoy on 2011-01-16
Slow compared to what ?
Using the exact same video files ?

What is the video file info container/codec/streams ?
use 
ffmpeg -i filename.ext
or 
mediainfo

If these files are HD MPEG-4/10 H264 then linear editing is a very CPU intensive job.
You may be better off making a cut-list & then using this to cut the video with cmd line tool.

MythTV has the best (super fast & easy) cut-list GUI but may not be frame accurate.
More of a problem is.. I'm not sure its cut-lists are honoured for MPEG-4 lossless transcode. 

I believe that..
Some people use MythTV cut-list editor to get close to desired cut points, transcode to MPEG-2 & then use AviDemux to finish.

---

### Post by calande on 2011-01-16
I won't use Avidemux anymore. The audio and video are always offset. Incredible.
Pitivi is very slow compared to VideoRedo or SolvegMM Video Splitter on Windows. I don't know why. The source file is a 3GB SD MPEG-TS file recorded with a DVB-T set-top-box.

---

### Post by BicyclerBoy on 2011-01-16
Lots of people complaining about the a/v sync with that program..

Shame about PiTiVi...There are others like Cinelerra for eg.
Should be careful to compare because those windoze programs are not free I suspect.

DVB-T tuners stream mpeg2-ts but that does not answer the question of video format.
This transport stream can be different things including mpeg-2 & mpeg-4/10 H264, the audio can be all sorts.

If MythTV solves its lossless transcode cut-list issues then it would be a good candidate considering it could be the recording program anyway..

---

### Post by cotcot on 2011-01-16
> **calande said:**
> Do you know another good application instead (not Avidemux either)? I just want to remove commercials from videos. Thanks.
Looks like you are looking for an easy editor. Cinelerra and blender are very nice but high end (= needs more time to learn, but powerful) 
Try Kdenlive or Openshot.

---

### Post by calande on 2011-01-16
Thanks, I'll give them a try ;)

---

