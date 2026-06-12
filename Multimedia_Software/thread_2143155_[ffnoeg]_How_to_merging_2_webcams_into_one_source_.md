---
title: "[ffnoeg] How to merging 2 webcams into one source via ffmpeg"
date: 2013-05-08
forum: Multimedia Software
---

### Post by neogeo1128 on 2013-05-08
I would like to merge 2 webcam sources , Cam A (/dev/video0) and Cam B (/dev/video1)
Cam A is the main and Cam B will be displayed on the lower right corner, on top of Cam A

Any ideas?

---

### Post by FakeOutdoorsman on 2013-05-08
This can be done with ffmpeg. Start by reading [Filtering Introduction](http://ffmpeg.org/ffmpeg-filters.html#Filtering-Introduction), [Filtergraph description](http://ffmpeg.org/ffmpeg-filters.html#Filtergraph-description), and [Filtergraph syntax](http://ffmpeg.org/ffmpeg-filters.html#Filtergraph-syntax-1). Using the [scale](http://ffmpeg.org/ffmpeg-filters.html#scale) and [overlay](http://ffmpeg.org/ffmpeg-filters.html#overlay-1) filters:

```
ffmpeg -f video4linux2 -i /dev/video0 -f video4linux2 -i /dev/video1 -filter_complex "[1:0]scale=iw/2:-1[a],[0:0][a]overlay=main_w-overlay_w-10:main_h-overlay_h-10" -c:v libx264 -crf 23 -preset medium -movflags faststart output.mp4
```

ffmpeg is taking the second input, which is named [1:0] and scaling it to half size.  Then overlay is taking the first input, named [0:0], and the result of the scale filter, named [a], and placing [a] over [0:0]. The section "main_w-overlay_w-10:main_h-overlay_h-10" is telling overlay to place [a] in the lower right corner. See [overlay documentation](http://ffmpeg.org/ffmpeg-filters.html#overlay-1) for an explanation of these options.

"-c:v libx264 -crf 23 -preset medium" refer to the video encoder and set quality and encoding speed. See [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for more details on those.

"-movflags faststart" allows the video to begin playback before it is completely downloaded by the viewer (progressive download). Useful if viewers will be watching your video in a browser. Otherwise you can omit this.

From the overlay docs:
> Be aware that frames are taken from each input video in timestamp order, hence, if their initial timestamps differ, it is a a good idea to pass the two inputs through a "setpts=PTS-STARTPTS" filter to have them begin in the same zero timestamp, as it does the example for the movie filter.

Resulting in:
```
ffmpeg -f video4linux2 -i /dev/video0 -f video4linux2 -i /dev/video1 -filter_complex "[0:v]setpts=PTS-STARTPTS[background];[1:v]setpts=PTS-STARTPTS,scale=iw/2:-1[foreground];[background][foreground]overlay=main_w-overlay_w-10:main_h-overlay_h-10" -c:v libx264 -crf 23 -preset medium -movflags faststart output.mp4
```

You will either have to use a [static build of ffmpeg](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453) or [compile ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) yourself for these examples to work. The fake "ffmpeg" from the repository lacks features and is buggy.

---

