---
title: "Mplayer crashes with h264 (AVCHD) files"
date: 2011-06-01
forum: Multimedia Software
---

### Post by azenz on 2011-06-01
I just upgraded from 10.04 to 10.10. Previously I could play my h264 encoded .MTS video files. Now mplayer gives this error:


MPlayer 1.0rc4-4.4.5 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 2011-05-30-00026.MTS.
TS file format detected.
VIDEO H264(pid=4113) AUDIO A52(pid=4608) NO SUBS (yet)!  PROGRAM N. 1
Segmentation fault

Also, VLC does not play them, either, giving an error that:

VLC does not support the audio or video format "h264". Unfortunately there is no way for you to fix this.

I have read about removing the libavutils in order to fix this, but if I want to remove the libavutil-extra-50, then it installs the libavutil50 automatically. Also, I did this and ffmpeg no longer encodes using h264. After reverting to the previous way of having libavutil-extra-50 installed, then mplayer shows the above error when playing h264. I am so incredibly frustrated with Ubuntu over all this video stuff!!! I hope someone more experienced can help out.

EDIT: the mplayer problem was solved by installing vdpau-va-driver, but VLC still does not support h264 playback. I'm kind of worried that messing around all the time will break things...I find this whole thing quite messed up, but maybe someone has had a good experience with fixing VLC h264 playback (on NVIDIA)?

---

