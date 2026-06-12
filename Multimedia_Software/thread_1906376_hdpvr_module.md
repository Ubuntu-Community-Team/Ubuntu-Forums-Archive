---
title: "hdpvr module"
date: 2012-01-09
forum: Multimedia Software
---

### Post by msknight on 2012-01-09
Hi Folks,

I'm trying to copy from a PVR that has multiple video/audio streams and in reading this - [http://www.mythtv.org/wiki/Index.php/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Index.php/Hauppauge_HD-PVR) - just over half way down it is talking about "Miscellaneous Kernel Module Options" that contain exactly what I need, namely default_video_input and default_audio_input (video_nr would be nice as well)

So if I read this right, in order to activate those options, I'd need to recompile the kernel; am I right?

If that is the case, who do I need to talk with about getting those options enabled/included by default please?

Reason being, I've been told that MythTV chops the recorded files at the top of every hour, which makes game stream capture a bit of a faff because after stream conversion to another format, the audio goes out of sync (re-synching one stream isn't hard, but resynching multiple streams that are stuck together is a pain) ... and I haven't yet come across any simple GUI application that can simply record a stream from the multiple sources on a card.

It would be great just to be able to copy from /dev/video0 to a file; I just need those extra controls

Any help gratefully appreciated.

Michelle.

---

### Post by msknight on 2012-01-12
bump

---

### Post by BicyclerBoy on 2012-01-12
That box outputs mpeg2-ts transport stream data..

You can just capture it directly into a file/pipe..
Play it directly with VLC/mplayer etc.
cat /dev/video0 > test.ts

I'm not sure why AC3 5.1 is routed over S/PDIF, must be f/w limitation not muxing AC3 with AAC.

If you need to mux in the audio from S/PDIF etc then you could look at ffmpeg
cat /dev/video0 | ffmpeg -i - -vcodec copy -sameq -acodec copy -f mpegts test.ts
& then add in another input audio stream

---

### Post by msknight on 2012-01-14
Thanks for this.

My problem is that I don't know how to get the other streams. The 5.1 audio doesn't bother me too much, but I need to get at the s-video, composite and front audio jacks.

Options on v4l2...
    default_video_input=# 
    default_audio_input=# 
... aren't working.

I think they're not in the default compile or v4l2, or possibly something else needs to be compiled in the kernel, I'm not sure.

---

### Post by BicyclerBoy on 2012-01-14
I would be very surprised if this box can/will digitise more than one video input.

ivtv-tools package:

v4l2-ctl --device=/dev/video0 --set-ctrl=controlname=value

Sets the device node to /dev/video#
    default_video_input=# 
default video input: 0=component, 1=S-Video, 2=composite 

see:
[http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR)

---

