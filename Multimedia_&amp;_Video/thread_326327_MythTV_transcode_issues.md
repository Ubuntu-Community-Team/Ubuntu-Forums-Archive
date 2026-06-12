---
title: "MythTV transcode issues"
date: 2006-12-27
forum: Multimedia &amp; Video
---

### Post by AusIV4 on 2006-12-27
I've been running a MythTV box for about 7 months now, and I just got a new tuner. The new one is an external Plextor ConvertX, and the old one is a Sabrent TV-FM. The ConvertX must record at 640x480. The Sabrent must record at 480x480. Recording mpeg4 video seems to work in both cases. The problem I'm having is that when I try to transcode the video (to remove commercials), the 640x480 video becomes completely garbled. 

I have Lossless transcoding set for the RTjpeg/MPEG4 profile. I'm guessing the issue is that the NUV container thinks the transcoded video is 480x480 (when it should still be 640x480, since it's just copied frame for frame), but I've no way of knowing that for sure.

Any ideas how I might fix this?

---

### Post by majoridiot on 2006-12-27
does this happen with a default transcoder setting, a custom one or both?

---

### Post by AusIV4 on 2006-12-27
Default.

---

### Post by tagra123 on 2006-12-27
> **AusIV4 said:**
> I've been running a MythTV box for about 7 months now, and I just got a new tuner. The new one is an external Plextor ConvertX, and the old one is a Sabrent TV-FM. The ConvertX must record at 640x480. The Sabrent must record at 480x480. Recording mpeg4 video seems to work in both cases. The problem I'm having is that when I try to transcode the video (to remove commercials), the 640x480 video becomes completely garbled. 

I have Lossless transcoding set for the RTjpeg/MPEG4 profile. I'm guessing the issue is that the NUV container thinks the transcoded video is 480x480 (when it should still be 640x480, since it's just copied frame for frame), but I've no way of knowing that for sure.

Any ideas how I might fix this?



I would try the following

from command prompt 

mythfrontend

Then use the menus

Utilities
--Setup
----TV Settings
------ Recording Profiles
-------- Software Encoders
--------------- Default   (480x480) I would try changing all of these to 640 x 480
         
--------Transcoders
------------------- I again would change these to 640x480


If this fixes it for you please post a followup

---

### Post by AusIV4 on 2006-12-28
I changed the Sabrent tuner to record at 640x480. I set all of my transcoding options to use lossless transcoding. I recorded 30 second clips on each tuner. I made a small cut and transcoded each clip. The video recorded by the Sabrent tuner transcoded flawlessly, the video recorded by the ConvertX tuner wound up garbled.

It makes me wonder if the ConvertX's hardware encoding may be different than the software encoding. I've been under the impression that the ConvertX was a fairly common encoder, and I have a hard time believing nobody has gotten it to transcode.

[EDIT]
Apparently this is a known issue. I've filed a bug report with MythTV's trac system. I've also found that cutting commercials out of the middle of a show, but not going near the ends can result in a successful transcode.

---

