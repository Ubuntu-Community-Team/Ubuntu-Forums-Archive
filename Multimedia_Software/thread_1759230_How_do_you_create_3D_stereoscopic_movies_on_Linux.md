---
title: "How do you create 3D stereoscopic movies on Linux?"
date: 2011-05-15
forum: Multimedia Software
---

### Post by Yfrwlf on 2011-05-15
I've tried Lives, KDenlive, Avidmux, Openshot, Pitivi, and Cinelerra, and I cannot figure out how to merge two movies into a single movie.  Cinelerra no doubt has this ability due to its complexity, it just really needs a UI overhaul and lessons in usability since it takes forever just to figure out how to do basic things with it.

Someone made a script to use gStreamer to combine videos [here]("http://videomerge3d.sourceforge.net/") but even after installing the ugly plugins from the multiverse repo on Ubuntu 10.10 so that I have x264enc, I still get the ```
Pipeline is PREROLLING ...
```of doom, which just sits there waiting and isn't actually doing anything, a common problem with gStreamer apparently...

If mencoder can do the same thing I haven't figured out how.

Does anyone know how to edit movie frames so that you can stick the second video into the **same frame** on any video editor for Linux out there, or know of a way to use a command line encoder to do so?

I have two 1080p movies that I'd love to be able to merge, creating either one 3840x1080 movie or a 1920x2160 movie.

You'd think there would be more Linux users out there using dual cameras to create 3D movies.  Having such a tool is necessary to get this done so that they can be displayed on a 3D TV, or by one of the new fledgling Linux 3D movie players (when is VLC, Totem, or MPlayer going to pick up this support??).

---

### Post by Ferrat on 2011-07-25
Testing it now but seems to be working but not sure yet, will let it go on for a while and see what happens :)

Nope false alarm, doesn't work, I get further but nothing happens :/

---

### Post by JustJ on 2011-11-07
EDIT: Sorry.. just noticed that you had already linked to my script! I had experienced the prerolling issue during development but it had been ironed out and working ( for me 'only?' it seems ).  Have you had any success since then?  I'll test the script now that I've upgraded Ubuntu and see if I get the prerolling problem ( which is usually solved by putting in a !queue! to keep it from getting gridlocked).

Edit2:  Just tried my script and I'm getting gstreamer errors now as well. I'm on a new laptop and have upgraded 3 versions of Kubuntu so there's been a lot of changes! I'll see if I can track it down as I'll need this capability again sooner or later! 

-----

I was looking into this last spring.. sorry I didn't see your message at the time.

 I wrote up a script using gstreamer to do this very thing:
[http://videomerge3d.sourceforge.net/](http://videomerge3d.sourceforge.net/)


I wrote a bit more about it here - including some other example gstreamer command lines:
[http://superuser.com/questions/231938/combine-merge-left-right-video-files/259068#259068](http://superuser.com/questions/231938/combine-merge-left-right-video-files/259068#259068)

---

### Post by JustJ on 2011-11-16
:popcorn: FIXED  - or at least a workaround.

I uploaded the new version to the Sourceforge page: 
[http://sourceforge.net/projects/videomerge3d/](http://sourceforge.net/projects/videomerge3d/)

--

 It seems that the x264 encoder was the source of the problems.  After trying a few esoteric options to try to get it to work ( including removing the queue buffer limitations which exhausted my machine and restarted X ) I added in the option to use the ffmpeg library's mpeg4 encoder instead ( now default ). For now.. don't use the x264 encoder. mpeg2 also seemed problematic.

I've also made it print out the gstreamer command with the -norun option so that you can modify it first in case you want to try other encoders ( or bitrates ) etc that I haven't directly supported.

---

### Post by Yfrwlf on 2011-11-23
I downloaded the latest version from Sourceforge that you uploaded on 11/16 and I don't see any commands referencing the program "mpeg4" or any ffmpeg project-related commands that I could see.  Also, the default is still set to x264enc in the default options:

```
NUMBER_OF_FILES=0
LAUNCH_ARGS=""
audioenc="faac !"
videoenc="x264enc"
wxh="width=640, height=480"
offset="-640"
avmuxer="avimux"
```

Maybe you haven't uploaded the newer version yet? ^^

---

### Post by JustJ on 2011-11-28
Hi Yfrwlf,

 Thanks for checking it out again.

 I just downloaded it from sourceforge and it gave me the newest version.
If you enter it without any arguments it should give you output with a 5th line saying "Warning:h264 is (was) broken - use mpeg4 (default) instead"
and a line further down saying "-mpeg4_b4  bitrate = 4Mb/S (default)" ??

Try running it directly from your download directory:
bash ./videomerge3d


I downloaded it by clicking on videomerge3d on this page:
[http://sourceforge.net/projects/videomerge3d/files/](http://sourceforge.net/projects/videomerge3d/files/)

---

### Post by iceblue11 on 2012-02-14
I am searching around because this is exactly what I need to do as well. Need to replace Adobe Premier to do 3D editing. But this thread just confused the hell out of me

---

### Post by fliker09 on 2013-03-27
> ./videomerge3d -640 -ano -v Red1.avi Blue1.avi Stereo1.avi
width=640, height=480  ffenc_mpeg4 bitrate=4000000  
saving file to Stereo1.avi
./videomerge3d: line 273: [: =: unary operator expected
Running Command: gst-launch-0.10  -v  filesrc location=Red1.avi  ! decodebin name=Left  filesrc location=Blue1.avi  ! decodebin name=Right  Left. ! videoscale ! ffmpegcolorspace ! video/x-raw-yuv, width=640, height=480  ! videobox border-alpha=0 right=-640 ! queue2  ! mix.  Right. ! videoscale ! ffmpegcolorspace ! video/x-raw-yuv, width=640, height=480  ! videobox border-alpha=0 left=-640 ! queue2  ! mix.  Left. ! decodebin ! audioconvert ! audiopanorama panorama=1.00 ! queue2  ! addaudio.  Right. ! decodebin ! audioconvert ! audiopanorama panorama=-1.00 ! queue2  ! addaudio.   adder name=addaudio !    queue2  ! avmux.   videomixer name=mix ! ffmpegcolorspace ! ffenc_mpeg4 bitrate=4000000 !  avimux name=avmux ! progressreport name="Encoding Progress" ! filesink location="Stereo1.avi" 
Setting pipeline to PAUSED ...
/GstPipeline:pipeline0/GstDecodeBin:Right/GstTypeFindElement:typefind.GstPad:src: caps = video/x-msvideo
/GstPipeline:pipeline0/GstDecodeBin:Right/GstAviDemux:avidemux0.GstPad:sink: caps = video/x-msvideo
/GstPipeline:pipeline0/GstDecodeBin:Left/GstTypeFindElement:typefind.GstPad:src: caps = video/x-msvideo
Pipeline is PREROLLING ...
/GstPipeline:pipeline0/GstDecodeBin:Left/GstAviDemux:avidemux1.GstPad:sink: caps = video/x-msvideo
/GstPipeline:pipeline0/GstDecodeBin:Left/GstQueue:queue1.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstDecodeBin:Left.GstGhostPad:src0: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstDecodeBin:Left/GstQueue:queue1.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstDecodeBin:Right/GstQueue:queue0.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstDecodeBin:Right.GstGhostPad:src0: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstDecodeBin:Right/GstQueue:queue0.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstVideoScale:videoscale0.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstVideoScale:videoscale0.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstDecodeBin:Left.GstGhostPad:src0.GstProxyPad:proxypad5: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstVideoScale:videoscale1.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstVideoScale:videoscale1.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstDecodeBin:Right.GstGhostPad:src0.GstProxyPad:proxypad4: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp0.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp0.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp1.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp1.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstCapsFilter:capsfilter0.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstCapsFilter:capsfilter0.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstVideoBox:videobox0.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)1280, height=(int)480
/GstPipeline:pipeline0/GstVideoBox:videobox0.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstQueue2:queue20.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)1280, height=(int)480
/GstPipeline:pipeline0/GstQueue2:queue20.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)1280, height=(int)480
/GstPipeline:pipeline0/GstVideoMixer:mix.GstVideoMixerPad:sink_0: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)15023967/1000000, width=(int)1280, height=(int)480
/GstPipeline:pipeline0/GstCapsFilter:capsfilter1.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstCapsFilter:capsfilter1.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstVideoBox:videobox1.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)1280, height=(int)480
/GstPipeline:pipeline0/GstVideoBox:videobox1.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)640, height=(int)480
/GstPipeline:pipeline0/GstQueue2:queue21.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)1280, height=(int)480
/GstPipeline:pipeline0/GstQueue2:queue21.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)1280, height=(int)480
/GstPipeline:pipeline0/GstVideoMixer:mix.GstVideoMixerPad:sink_1: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)1280, height=(int)480
/GstPipeline:pipeline0/GstVideoMixer:mix.GstPad:src: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)1280, height=(int)480, pixel-aspect-ratio=(fraction)1/1
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp2.GstPad:src: caps = video/x-raw-yuv, width=(int)1280, height=(int)480, framerate=(fraction)120259/8000, format=(fourcc)I420, pixel-aspect-ratio=(fraction)1/1
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp2.GstPad:sink: caps = video/x-raw-yuv, format=(fourcc)YUY2, framerate=(fraction)120259/8000, width=(int)1280, height=(int)480, pixel-aspect-ratio=(fraction)1/1
/GstPipeline:pipeline0/ffenc_mpeg4:ffenc_mpeg40.GstPad:src: caps = video/x-divx, width=(int)1280, height=(int)480, framerate=(fraction)21845/1453, divxversion=(int)5
/GstPipeline:pipeline0/ffenc_mpeg4:ffenc_mpeg40.GstPad:sink: caps = video/x-raw-yuv, width=(int)1280, height=(int)480, framerate=(fraction)120259/8000, format=(fourcc)I420, pixel-aspect-ratio=(fraction)1/1
/GstPipeline:pipeline0/GstAviMux:avmux.GstPad:video_00: caps = video/x-divx, width=(int)1280, height=(int)480, framerate=(fraction)21845/1453, divxversion=(int)5
^CCaught interrupt -- handling interrupt.
Interrupt: Stopping pipeline ...
ERROR: pipeline doesn't want to preroll.
Setting pipeline to NULL ...
/GstPipeline:pipeline0/GstAviMux:avmux.GstPad:video_00: caps = NULL
/GstPipeline:pipeline0/ffenc_mpeg4:ffenc_mpeg40.GstPad:src: caps = NULL
/GstPipeline:pipeline0/ffenc_mpeg4:ffenc_mpeg40.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp2.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp2.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstVideoMixer:mix.GstVideoMixerPad:sink_1: caps = NULL
/GstPipeline:pipeline0/GstVideoMixer:mix.GstVideoMixerPad:sink_0: caps = NULL
/GstPipeline:pipeline0/GstVideoMixer:mix.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstQueue2:queue21.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstQueue2:queue21.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstQueue2:queue20.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstQueue2:queue20.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstVideoBox:videobox1.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstVideoBox:videobox1.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstVideoBox:videobox0.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstVideoBox:videobox0.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstCapsFilter:capsfilter1.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstCapsFilter:capsfilter1.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstCapsFilter:capsfilter0.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstCapsFilter:capsfilter0.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp1.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp1.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp0.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstFFMpegCsp:ffmpegcsp0.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstVideoScale:videoscale1.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstVideoScale:videoscale1.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstVideoScale:videoscale0.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstVideoScale:videoscale0.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Right.GstGhostPad:src0: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Right/GstQueue:queue0.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Right/GstQueue:queue0.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Right/GstAviDemux:avidemux0.GstPad:video_00: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Right/GstAviDemux:avidemux0.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Right/GstTypeFindElement:typefind.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Left.GstGhostPad:src0: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Left/GstQueue:queue1.GstPad:src: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Left/GstQueue:queue1.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Left/GstAviDemux:avidemux1.GstPad:video_00: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Left/GstAviDemux:avidemux1.GstPad:sink: caps = NULL
/GstPipeline:pipeline0/GstDecodeBin:Left/GstTypeFindElement:typefind.GstPad:src: caps = NULL
Freeing pipeline ... - :( What's wrong? Ubuntu 12.10. Note: there is no audio track in both videos (may be this will be important to understand what's wrong :\ )

P.S. I didn't find how to hide the quote

---

### Post by fliker09 on 2013-03-27
Found a good link for those who want to create 3D videos:

[https://vimeo.com/24555460](https://vimeo.com/24555460)

What's good about it is the fact you don't need red/cyan filters for your cameras and you can play resulting video using Bino! But you can't play it on a TV which doesn't support 3D. So I am still interested in your script!

---

### Post by oldos2er on 2013-03-27
Old thread closed.

---

