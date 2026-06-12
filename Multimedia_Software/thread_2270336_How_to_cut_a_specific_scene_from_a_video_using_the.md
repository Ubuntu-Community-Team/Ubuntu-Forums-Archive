---
title: "How to cut a specific scene from a video using the terminal?"
date: 2015-03-22
forum: Multimedia Software
---

### Post by remmas-sido on 2015-03-22
Hello guys 
Let us say that I have a video in avi format, the length of this video is 3 minutes,and I want to cut the part from 00:01:30 - 00:03:00 is that possible? and does the format of the video plays an important role in cutting it,for example if I have the same video in 3 formats avi,mp4 and mkv does the command line change if the format change? my primary goal is to cut the video in avi format,but I am just asking out of the curiosity.
Thank You

---

### Post by FakeOutdoorsman on 2015-03-22
Get the real ffmpeg. It's not in the repo yet, and avconv is buggy. You have three options: [download](http://johnvansickle.com/ffmpeg/), [use a PPA](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media), or [compile](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

Example to [stream copy](https://ffmpeg.org/ffmpeg.html#Stream-copy) (just re-muxing, no re-encoding) from 00:01:30 - 00:03:00. First set the part you want to skip with -ss, then tell it the duration with -t (00:03:00 - 00:01:30 = 00:01:30 duration):
```
ffmpeg -ss 00:01:30 -i input -map 0 -c copy -t 00:01:30 output
```

or use seconds:
```
ffmpeg -ss 90 -i input -map 0 -c copy -t 90 output
```

or you can mix seconds and *HH:MM:SS.microseconds* format.
```
ffmpeg -ss 90 -i input -map 0 -c copy -t 00:01:30 output
```

Since your input is 3 minutes, and it seems you just want to skip the first 90 seconds and keep the rest, you can just use -ss:
```
ffmpeg -ss 00:01:30 -i input -map 0 -c copy output
```

Or you can use -to instead of -t. It's easier since you don't have to do any subtraction, but you have to use -ss as an output option which is slower (but possibly more accurate).
```
ffmpeg -i input -ss 00:01:30 -to 00:03:00 -map 0 -c copy output
```

[list]
[*]"-map 0" overrides the default [stream selection](https://ffmpeg.org/ffmpeg.html#Stream-selection) and makes ffmpeg map all streams instead of one stream per stream type.
[*]"-c copy" uses stream copy mode instead of re-encoding. This is fast and preserves quality.
[*]The input and output formats generally don't matter as long as you use a compatible output format (such as the same file extension as the input).
[*]Also see [FFmpeg Wiki: Seeking](http://trac.ffmpeg.org/wiki/Seeking).
[/list]

---

