---
title: "DVgrab output format"
date: 2015-01-26
forum: Multimedia Software
---

### Post by uwe-bungto on 2015-01-26
Ubuntu Studio 14.04

man dvgrab >  **-f,** **-format** _dv1_ **|** _dv2_ **|** _raw_ **|** _dif_ **|** _qt_ **|** _jpeg_ **|** _jpg_ **|** _mpeg2_ **|** _hdv_
                 Specifies the format of the output file(s). File  format  can
                 also  be  determined  if you include an extension on the _base_
                 name. The following extensions  are  recognizable:  avi,  dv,
                 dif, mov, jpg, jpeg, and m2t (HDV).

No matter what output format I specify (dvgrab -f raw etc) the output is a .m2t file. Has anyone else have this issue? Or amy I missing something?

---

### Post by FakeOutdoorsman on 2015-01-27
Are you capturing DV or HDV? Can you show your actual command and the complete console output?

---

### Post by uwe-bungto on 2015-01-27
> **FakeOutdoorsman said:**
> Are you capturing DV or HDV? Can you show your actual command and the complete console output?
I am using a Sony HVR 1AU, which is HDV.
I would like to capture in an uncompressed form if possible so I can load it into Lightworks for editing.
I was of the impression that dvgrab -f would set the output to mov or mpeg2 or avi, how ever the output files are all
MPEG-2 transport containers
1440 x 1080
codec mpeg-2 video
Frame rate 30fps

The ^C below is crtl c to stop dvgrab

> $ dvgrab Videos/ -f raw
Found AV/C device with GUID 0x0800460103f3aa7f
Waiting for HDV...
Capture Started
^C"Videos/001.m2t":    85.15 MiB 816 frames timecode 00:00:28.03 date 2015.01.23 17:11:07
Capture Stopped
output is Videos/001.m2t

$ dvgrab Videos/ -f mpeg2
Found AV/C device with GUID 0x0800460103f3aa7f
Waiting for HDV...
Capture Started
^C"Videos/002.m2t":    55.25 MiB 531 frames timecode 00:00:45.21 date 2015.01.23 17:11:25
Capture Stopped
output is videos/002.m2t 

~$ dvgrab Videos/ -format=hdv -autosplit
Found AV/C device with GUID 0x0800460103f3aa7f
Waiting for HDV...
Capture Started
"Videos/001.m2t":    27.44 MiB   257 frames timecode 00:00:10.03 date 2015.01.23 16:13:04
"Videos/002.m2t":    15.33 MiB   149 frames timecode 00:00:15.21 date 2015.01.23 17:10:55
"Videos/003.m2t":     2.21 MiB    21 frames timecode 00:00:17.21 date 2015.01.23 17:10:57
"Videos/004.m2t":   307.79 MiB 2962 frames timecode 00:01:58.21 date 2015.01.23 17:12:38
Capture Stopped




---

### Post by FakeOutdoorsman on 2015-01-28
> **uwe-bungto said:**
> I am using a Sony HVR 1AU, which is HDV.
I would like to capture in an uncompressed form if possible so I can load it into Lightworks for editing.
I was of the impression that dvgrab -f would set the output to mov or mpeg2 or avi, how ever the output files are all
MPEG-2 transport containers
1440 x 1080
codec mpeg-2 video
Frame rate 30fps


This is correct (actually the frame rate is probably 30000/1001) and is the format your camera is using. dvgrab is just capturing what is from the tape and is not doing any re-encoding.

HD sized MPEG-2 video should be easy enough to edit in most editors on modern machines. Is Lightworks having issues with these inputs?

---

### Post by uwe-bungto on 2015-01-28
> **FakeOutdoorsman said:**
> This is correct (actually the frame rate is probably 30000/1001) and is the format your camera is using. dvgrab is just capturing what is from the tape and is not doing any re-encoding.

HD sized MPEG-2 video should be easy enough to edit in most editors on modern machines. Is Lightworks having issues with these inputs?

Lightworks unlike Final Cut X & 7 doesn't have any issues with the m2t files. I haven't found a video or audio format that it can't handle
We tried to capture the tape in both FC versions they couldn't find the camera or the tape deck that we used later. I captured the tape with dvgrag and tried to import them into FC, forget it, both version were useless.

I thought by specifying the a extensions like the dvgrab hints at, I could find a format that FC wouldn't choke on.
Well that didn't work, Linux 1 Mac 0 [-X

---

### Post by FakeOutdoorsman on 2015-01-30
Surprising that Final Cut does not support such an old format, but also unsurprising since it is FC. Are there older videos captured from the same camera or the deck via FC or whatever that FC did work with? I remember ages ago Premiere Pro used to not support raw DV which was bewildering and frustrating, so I had to re-mux which was beyond annoying.

---

### Post by uwe-bungto on 2015-01-31
> **FakeOutdoorsman said:**
> Surprising that Final Cut does not support such an old format, but also unsurprising since it is FC. Are there older videos captured from the same camera or the deck via FC or whatever that FC did work with? I remember ages ago Premiere Pro used to not support raw DV which was bewildering and frustrating, so I had to re-mux which was beyond annoying.

Like I wrote, dvgrab capture the video. It was then transferred to a  thumb drive where they were transferred to the Mac's Hdd. The person on  the Mac couldn't find the files from within either FC Pro X or FC Pro7.  The files simply did not exist.

Anyways an old Sony tape deck was dusted of and finally the file were captured from the tape..

---

### Post by Kencee on 2015-07-21
Hi!
I have the same problem...I capture with dvgrab HDV and my Final Cut don't recognize the m2t file. Somebody can help me? Thanks!

---

