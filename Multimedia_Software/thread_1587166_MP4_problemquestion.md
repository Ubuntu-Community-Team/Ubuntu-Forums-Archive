---
title: "MP4 problem/question"
date: 2010-10-03
forum: Multimedia Software
---

### Post by Ken Kaniff on 2010-10-03
Hi there,

I have a problem playing MP4 files. I'm running Ubuntu Lucid with restricted formats enabled.

What happens is MP4 files do open up in VLC and Movie Player. The sound appears with no problem but the video skips very badly, sometimes not moving for seconds at a time.

One thing I'm sure of is that it's not the laptop's/video card's fault. Before Ubuntu I used to run Xubuntu 10.04 and had no issued playing MP4 with VLC or Movie Player.

Do you think I'm missing a particular codec?

Thanks!
KK

---

### Post by Alessandro.g89 on 2010-10-03
if you see images, you do have the codec!
you may try to change the video output device in VLC:

ctrl+P -> video -> output

---

### Post by Ken Kaniff on 2010-10-03
> **Alessandro.g89 said:**
> if you see images, you do have the codec!
you may try to change the video output device in VLC:

ctrl+P -> video -> output

Thanks. I've been messing with the video output already, with no luck. 

One other thing. I've just tried an MP4 video file on my netbook that runs EasyPeasy (based on Ubuntu) and I get the same thing--badly skipping video.

Any suggestion is welcome. 

Thanks.

---

### Post by cchhrriiss121212 on 2010-10-03
Could be a video driver issue, what is your card? Do you have proprietary drivers installed?

---

### Post by Alessandro.g89 on 2010-10-03
does the CPU have an high load when you try playing MP4?

---

### Post by Ken Kaniff on 2010-10-03
> **cchhrriiss121212 said:**
> Could be a video driver issue, what is your card? Do you have proprietary drivers installed?
My card specs:

[I] description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom
       configuration: driver=i915 latency=0[/I]

I'm not sure if I have  proprietary drivers.



As for the CPU load it's a lot higher when playing MP4 files. For example, when playing an avi file it's: CPU1 40% and CPU2 30%, with MP4 files - CPU1 70% and CPU2 90%.

---

### Post by SeijiSensei on 2010-10-03
How big is the video?  720p or perhaps 1080p?  My guess is that it's encoded in H.264, and your computer doesn't have the horsepower to decode it in real time.

Just for information, MP4 is a "container" format, a particular file structure that places the audio, video and, if it exists, subtitle streams into a single file.  A "codec" like H.264 is a method of encoding and compressing a video stream.  Here are some other common examples:

Containers:  MP4, AVI, MKV ("Matroska"), WMV
Codecs: H.264, XviD, DivX, VP8, Vorbis

---

### Post by Ken Kaniff on 2010-10-03
> **SeijiSensei said:**
> How big is the video?  720p or perhaps 1080p?  My guess is that it's encoded in H.264, and your computer doesn't have the horsepower to decode it in real time.

Just for information, MP4 is a "container" format, a particular file structure that places the audio, video and, if it exists, subtitle streams into a single file.  A "codec" like H.264 is a method of encoding and compressing a video stream.  Here are some other common examples:

Containers:  MP4, AVI, MKV ("Matroska"), WMV
Codecs: H.264, XviD, DivX, VP8, Vorbis

The video file's dimensions are: 1280 x 720
The codec is: H.264 / AVC

The laptop may not be the most powerful (it's still a dual core though)but it ran the exact file when I had Xubuntu. Now with Ubuntu it can't do it. That's what make me wonder what's up.

---

### Post by cchhrriiss121212 on 2010-10-03
Xubuntu (uses XFCE) will use up less resources than Ubuntu (which uses Gnome), which is probably why you see a difference. Try swithcing off any compiz effects. You could also try out Smplayer, which has a multithreading support option somewhere.

---

### Post by Alessandro.g89 on 2010-10-03
I use the same driver (i915) and it's not proprietary

It seems he's already multithreading, since both CPUs are above 50%
however, it should saturate to 100% on both cores before skipping frames, so the bottleneck is somewhere else (I think)

---

### Post by HDave on 2011-01-12
Ever resolve this?  I have the exact same problem!!!

---

### Post by Ken Kaniff on 2011-01-13
Nothing's changed and nobody's offered a helpful reply either, sorry.

---

### Post by no2498 on 2011-01-13
if using ati card
click system, preferences
go down the list to multimedia systems selector, start it click video
set the plugin 

this is in the cheese help file FAQ'S


&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" (X Window System (No Xv)) as video-output.
      This means that your CPU is doing all the work. Change it to "xvimagesink"
      (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work.
    


      To change this setting, run the gstreamer-properties
      command, click the Video tab
      and change the appropriate setting.

---

### Post by BicyclerBoy on 2011-01-13
If the OP does not know what graphics driver is running then the chances are it will be the default ubuntu.

This default driver does not have any h/w acceleration at all.
Not that much is possible with the intel driver.

Please post your /etc/X11/xorg.conf &  /var/log/Xorg.0.log ?


@HDave  your OP primary problem is caused by the camera generating malformed files with non-monotonic timestamps..
The means timestamps causing negative time offsets...
One of the data streams has bad timestamps.
Either one or both (all) streams may need re-encoding & then remuxing to clean up the file. 
Did you see my last post update ?
Some brands of video capture cards have this same bug/feature.
Your secondary problem could be the same as OP.

---

### Post by Ken Kaniff on 2011-01-13
Thanks for the answers but it's not working for me.

---

### Post by HDave on 2011-01-13
@Ken -- Try upgrading your ffmpeg and vlc:

[http://www.gogogeekboy.com/2010/09/getting-h264-video-capability-into-lucid/](http://www.gogogeekboy.com/2010/09/getting-h264-video-capability-into-lucid/)

---

### Post by Ken Kaniff on 2011-01-14
> **HDave said:**
> @Ken -- Try upgrading your ffmpeg and vlc:

[http://www.gogogeekboy.com/2010/09/getting-h264-video-capability-into-lucid/](http://www.gogogeekboy.com/2010/09/getting-h264-video-capability-into-lucid/)

@HDave, this is awesome! Worked like a charm. Thank you so much!

---

### Post by HDave on 2011-01-14
No problem Ken.  Looks like soon (11.04 maybe) this problem will be gone for the entire Ubuntu community.  Can't wait for that...I gotta believe more and more people are using the new HD home video cameras and need good H.264 codec support.

That aside, I've made the decision to revert my Samsung MX-H200 camcorder back to 720p instead of 1080i because the picture quality is so much better with progressive rather than interlaced frames.

---

### Post by amarendra on 2011-07-28
No it didn't get fixed in 11.04. I am trying the link above. Lets see if I get my 1.5GB .mp4 running smoothly.

UPDATE: no, it didn't work and I messed up my system. Another reason to move to Mac (can't help mentioning it :P)

---

### Post by Ken Kaniff on 2011-07-30
After upgrading to 11.04 the problem started occurring again on my box.

---

