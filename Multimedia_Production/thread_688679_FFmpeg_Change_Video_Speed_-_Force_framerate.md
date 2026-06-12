---
title: "FFmpeg Change Video Speed - Force framerate?"
date: 2008-02-05
forum: Multimedia Production
---

### Post by philc on 2008-02-05
I'd like to use FFmpeg to change the speed of a video, which I thought would have been easy enough by forcing the framerate.

For example, a PAL DV video with framerate of 25fps, changed to 50fps should play back twice as fast, and be half the duration.

My FFmpeg command looks like this:

ffmpeg -i input.dv -vcodec copy -acodec copy -r 50 output.dv

But this did not work and the output file is the same duration and framerate as the input file.

I also tried forcing the duration:

ffmpeg -i input.dv -vcodec copy -acodec copy -t 00:00:52 -r 50 output.dv

But just ended up with a file half the duration, but at the same speed. i.e. missing the latter half of the content.

Input file details are as follows:

  Duration: 00:01:44.1, start: 0.000000, bitrate: 28800 kb/s
    Stream #0.0: Video: dvvideo, yuv420p, 720x576 [PAR 59:54 DAR 295:216], 28800 kb/s, 25.00 tb(r)
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s

So nothing special or tricky there.

Is what I am trying to achieve possible? 

I've cross posted this to the FFmpeg mailing list as well, because I'm in the middle of an edit and am hoping for a quick answer. If someone proposes a solution on the mailing list, I'll post it back here too.

---

### Post by eye208 on 2008-02-06
The frame rate of DV is defined by time code, i.e. there is no global frame rate setting (DV supports variable frame rates too). I guess this is why you can't change the frame rate in stream copy mode.

---

### Post by philc on 2008-02-06
It was suggested on the FFmpeg mailing list that I try FFmpeg in conjunction with yuvfps, which is part of mjpegtools.

After installing mjpegtools, I used the following command:

```
ffmpeg -i input.dv -f yuv4mpegpipe - | yuvfps -s 50:1 -r 50:1  | ffmpeg -f yuv4mpegpipe -i - -b 28800k -y output.avi
```

This resulted in an AVI file at 50fps and 28Mbps. Obviously set the bitrate to what you actually need.

Thanks to Victor Paesa on the FFmpeg mailing list for this solution.

Other suggestions were to try the new libavfilter:

[http://wiki.multimedia.cx/index.php?title=Libavfilter](http://wiki.multimedia.cx/index.php?title=Libavfilter)

And another useful link here for a different method:

[http://thread.gmane.org/474C122B.9090307@signal7.de](http://thread.gmane.org/474C122B.9090307@signal7.de)

---

