---
title: "timelapse with avconv"
date: 2014-08-02
forum: Multimedia Software
---

### Post by guine42 on 2014-08-02
Im trying to make some timelapse videos and Im able to get decent results with avconv using this command:
```
avconv -f image2 -i DSC_%04d.tif -s hd1080 -r *fps* test.avi
```
The thing that is confusing me is every video comes out to be 6 seconds long regardless of the frames per second that I use, even if the total number of photos Im using totals to significantly fewer frames than there should be for a 6 second video at a very high fps(one of the videos I've tried has 164 photos and even at 48 frames per second the video is still 6 seconds long even though Im only providing enough frames for about 3.5 second of video).  So I guess what Im trying figure out is what is happening to get the information to make those extra frames for the video as well has how can I tell avconv to make a different length video(I've tried -t and a different number of seconds but that doesn't seem to be doing anything).
Thanks

---

### Post by coffeecat on 2014-08-04
*Thread moved to **Multimedia**.*

Plus free bump.

---

### Post by coldraven on 2014-08-04
While we wait for fakeoutdoorsman to come along and sort this out have a look at this. :)
[http://www.omgubuntu.co.uk/2011/08/slowmo-video-timelapse-linux](http://www.omgubuntu.co.uk/2011/08/slowmo-video-timelapse-linux)

---

### Post by FakeOutdoorsman on 2014-08-04
> **coldraven said:**
> While we wait for fakeoutdoorsman to come along and sort this out have a look at this. :)
Thanks for the vote of confidence, but I don't actually use avconv so I'm not very familair with its general usage.

With ffmpeg from FFmpeg you can try:
```
ffmpeg -i input -vf scale=1080:-2,format=yuv420p -codec:v libx264 output.mkv
```

To change the frame rate of the input (default is 25), and therefore the output:
```
ffmpeg -framerate 48 -i input -vf scale=1080:-2,format=yuv420p -codec:v libx264 output.mkv
```

To change the frame rate of the input (default is 25), and also the output in case the output needs to be some standard frame rate or something; results in frame drops or dupes:
```
ffmpeg -framerate 48 -i input -vf fps=25,scale=1080:-2,format=yuv420p -codec:v libx264 output.mkv
```
or
```
ffmpeg -framerate 48 -i input -vf scale=1080:-2,format=yuv420p -codec:v libx264 -r 25 output.mkv
```

Notes:
[list]
[*]There may be some bugs involving fps video filter and -r, so if you doesn't work as expected then try one or the other as shown above.
[*]The -2 in scale automatically returns a value that (mostly) retains the aspect ratio and ensures that the output is divisible by 2 which is required by the encoder libx264 in this case.
[*]"format=yuv420p" makes sure the output uses a chroma subsampling scheme that is compatible with dumb players.
[/list]

You can get a static build of from the [FFmpeg Download](http://ffmpeg.org/download.html) page, or you can follow a [guide to compile ffmpeg](http://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

> **coldraven said:**
> [http://www.omgubuntu.co.uk/2011/08/slowmo-video-timelapse-linux](http://www.omgubuntu.co.uk/2011/08/slowmo-video-timelapse-linux)
slomoVideo is fun to try and I agree that it might be good for timelapse (for [example](http://slowmovideo.granjow.net/videos.html)). I've used it a few times. Once in a while the "optical flow" will be incorrect, but if I recall correctly the official site shows how to fix that.

---

### Post by guine42 on 2014-08-06
Thanks, I may have to try playing around with ffmpeg then.

---

