---
title: "Cinelerra issue: audio &quot;outruns&quot; video on newly imported clips."
date: 2013-02-23
forum: Multimedia Software
---

### Post by WhenBirdsOink on 2013-02-23
Hello,

I ran into this problem almost immediately. Have a bunch of video files that I recently converted from mp4 to mov (I double-checked the codecs and everything is compatible in Cinelerra). Whenever I open the .mov files in *any other* video editing/viewing software, everything is perfect. But when I load them into Cinelerra and view them, the audio starts out about a half-second ahead of the video, catches up by the middle, and by the end of the video is about a half-second late. This is for very short clips (~1 minute), and the problem is amplified for longer clips.

Oh! And if I grab the slider in the viewer and drag it, I will frequently receive one or more instances of the following error:  "virtual int FileMOV::read_frame(VFrame*): quicktime_read_frame/quickdime_decode_video failed, result:" Sounds very indicative of something, but I can't find much on why the "read_frame" or "decode_video" is failing. 

The only thing I can deduce is that it seems to be somehow dropping frames on import, even for these very short clips, but I can't imagine why that would be or how to stop it. I'm using a newly-installed x64 version of ubuntu 12.10 and the latest cinelerra-cv. Any help would be tremendously appreciated!

---

