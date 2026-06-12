---
title: "How can I use vloopback mjpeg pipe without WebcamStudio"
date: 2009-12-12
forum: Multimedia Software
---

### Post by skipx on 2009-12-12
Hi,

For a project I want to be able to send external mjpeg streams like [http://193.40.245.184/mjpg/video.mjpg](http://193.40.245.184/mjpg/video.mjpg) to /dev/video2 using vloopback.

This I want to be able to do via bash since I want to be able to switch between multiple streams and because it's part of an (art)installation that will run in an exhibition. 

The reason that I want to send these streams to /dev/video2 is so I can open /dev/video1 in PD-Extended. 

For now I have vloopback running from [http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice](http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice)
and I was able to stream my desktop and internal webcam to PD using webcamstudio (though there i could not connect to that mjpeg stream).
Running Ubuntu 9.10

Hope you guys can help me with this using ffplay, ffmpeg, mencoder or what else needed. The less re-compressing the better..

Best,
Bart

---

### Post by patrickballeux on 2009-12-12
Hi,

If I understand correctly, you have a MJPEG stream that you want to foward to the vloopback device...  Why can't you use the stream directly in a movie player like VLC or Totem?

If I remember well, the first version of WebcamStudio was in fact a bash script using FFMpeg...  Just can't remember how I did it, but there was no GUI.

Let me try to find that out, probably it is what your looking for.

Patrick

---

### Post by patrickballeux on 2009-12-12
Hi again,

I found it:

Here is the URL : [http://www.uluga.ubuntuforums.org/showthread.php?t=901612]("http://www.uluga.ubuntuforums.org/showthread.php?t=901612")

You can use FFMpeg or GStreamer.  As you can see, the first original WebcamStudio was a big bash script...  The trick is to create a piped file (mkfifo) and use mjpegyoutov4l to read that piped file and send it to the v4l device (vloopback).

Using Gstreamer, this would be easy:

```
gst-launch souphttpsrc location=http://193.40.245.184/mjpg/video.mjpg ! decodebin ! ffmpegcolorspace ! y4menc ! filesink location=output.yuv & cat output.yuv | mjpegtools_yuv_to_v4l /dev/video2

```

Let me know if it helped...

---

### Post by skipx on 2009-12-14
> **patrickballeux said:**
> 
Why can't you use the stream directly in a movie player like VLC or Totem?

I need the stream in [Pure Data (PD)]("http://puredata.info/"), which has no possibility to present mjpeg broadcasts afaik..

I'm making a (art)work which will have an interface which has a mjpeg stream playing in the middle. When people want to choose another stream they press a button and left and right in the screen will appear each 6 pictures of other streams where they can choose from. The chosen stream will then replace the one that was playing.

So to use e.g. totem will make it difficult to do this, and i think in PD i might be able to make this interface.

Will try your suggestion this week an report here again, thanks! :P

---

### Post by skipx on 2009-12-15
I'm using vloopback from [lavrsen]("http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice")and so first I issue 
```

$ sudo modprobe vloopback
$ sudo chown 666 /dev/video* 
```

I think I have to send the mjpeg stream to /dev/video1 but then I get a the first run "mjpegtools_yuv_to_v4l: EOF in frame data, stop.", and the next runs after trying again directly "Segmentation Fault". If I try later, no Segmentation fault, just the EOF one.

```

$ gst-launch souphttpsrc location=http://193.40.245.184/mjpg/video.mjpg ! decodebin ! ffmpegcolorspace ! y4menc ! filesink location=output.yuv & cat output.yuv | mjpegtools_yuv_to_v4l /dev/video1
[9] 6918
mjpegtools_yuv_to_v4l-0.2 (c) Jan Panteltje 2008-always.
mjpegtools_yuv_to_v4l: Starting video stream.
Setting pipeline to PAUSED ...
**mjpegtools_yuv_to_v4l: EOF in frame data, stop.**
~ $ Pipeline is PREROLLING ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock


$ gst-launch souphttpsrc location=http://193.40.245.184/mjpg/video.mjpg ! decodebin ! ffmpegcolorspace ! y4menc ! filesink location=output.yuv & cat output.yuv | mjpegtools_yuv_to_v4l /dev/video1
[7] 6891
mjpegtools_yuv_to_v4l-0.2 (c) Jan Panteltje 2008-always.
mjpegtools_yuv_to_v4l: Starting video stream.
**Segmentation fault**
~ $ Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
```

Using /dev/video2 gives me 'failed to open output video device'

```
$ gst-launch souphttpsrc location=http://193.40.245.184/mjpg/video.mjpg ! decodebin ! ffmpegcolorspace ! y4menc ! filesink location=output.yuv & cat output.yuv | mjpegtools_yuv_to_v4l /dev/video2
[6] 6885
mjpegtools_yuv_to_v4l-0.2 (c) Jan Panteltje 2008-always.
**mjpegtools_yuv_to_v4l: failed to open output video device, aborting.** ~ $ Setting pipeline to PAUSED ...
Pipeline is PREROLLING ...
Pipeline is PREROLLED ...
Setting pipeline to PLAYING ...
New clock: GstSystemClock
```

Any idea?

---

### Post by patrickballeux on 2009-12-15
Have you created a fifo file output.yuv?  Because it you simply write to a regular file, it will not work.

> mkfifo output.yuv
gst-launch souphttpsrc location=http://193.40.245.184/mjpg/video.mjpg ! decodebin ! ffmpegcolorspace ! y4menc ! filesink location=output.yuv & cat output.yuv | mjpegtools_yuv_to_v4l /dev/video1
rm output.yuv


Let me know...

---

### Post by skipx on 2009-12-16
> **patrickballeux said:**
> Let me know...
Thanks, it works greatly! Thanks!

I do have a (re-)sizing question, what happens with the size (width/higth) of the stream? Is the size of the source of the stream taken over by /dev/video1?

And:
In my case I will be changing streams. So I kill mjpegtools_yuv_to_v4l and start a new one (and reopen the videodevice in PD). 
Is it saver to also remove (and remake) output.yuv in between changing streams (that might have a different geometry), or does it not make a difference?

---

### Post by patrickballeux on 2009-12-16
Hi skipx

> **skipx said:**
> Thanks, it works greatly! Thanks!

I do have a (re-)sizing question, what happens with the size (width/higth) of the stream? Is the size of the source of the stream taken over by /dev/video1?

And:
In my case I will be changing streams. So I kill mjpegtools_yuv_to_v4l and start a new one (and reopen the videodevice in PD). 
Is it saver to also remove (and remake) output.yuv in between changing streams (that might have a different geometry), or does it not make a difference?

For resizing, you can do it directly in the gstreamer stream using the videoscale element.

Examble: gst-launch v4l2src device=/dev/video0 ! **videoscale ! video/x-raw-yuv,width=320,height=240** ! ffmpegcolorspace ...


See the GStreamer documentation for all options you can apply on a stream source.

As for the output.yuv, it does not matter, you can leave it in place.

Happy to have helped you.

Pat

---

### Post by skipx on 2009-12-18
> **patrickballeux said:**
> Hi skipx
Happy to have helped you.

Pat

Yes, you did! Thanks very much for your help! :P

Bart

---

