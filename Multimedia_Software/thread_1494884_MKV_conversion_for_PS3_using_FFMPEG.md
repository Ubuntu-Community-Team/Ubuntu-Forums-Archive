---
title: "MKV conversion for PS3 using FFMPEG?"
date: 2010-05-27
forum: Multimedia Software
---

### Post by imtyler on 2010-05-27
It seems more and more people are encoding with the MKV container on bit torrent these days, and a lot of the shows I'm watching are starting to release almost exclusively with .mkv formatted videos. This is not a problem if I want to watch the shows on my computer but I've become accustomed to watching them on my PlayStation3 using my thumb drive. It seems the offical documentation for the PS3 includes a list of supported codecs ([http://manuals.playstation.net/document/en/ps3/3_15/video/filetypes.html](http://manuals.playstation.net/document/en/ps3/3_15/video/filetypes.html)), but when I use FFMPEG to convert with libxvid video and aac audio in the MP4 container my PS3 says the output video is not supported. I've also tried most combinations of libxvid, libx264, mpeg4 for -vcodec and aac, libmp3lame for -acodec in several different container formats but nothing seems to work. I have found one option that always works:

```
ffmpeg -i inputfile.mkv -sameq -ac 2 outputfile.mpeg
```I don't like doing it this way, however, as the output file is twice the size and the audio quality is terrible. If I don't reduce the audio channels to only two using -ac 2 FFMPEG throws an error (apparently MKV audio supports 6 channels). And preserving the video quality in MPEG video using -sameq produces too a large file (and I prefer to keep my files as lossless as possible). Ideally I want to save the files on an external HD I have but if a single episode of a show is 1.5 GB it's not very pratical.

Anyway, the PS3 docs say it supports h264 and xvid with aac audio, but apparently I'm doing something wrong. Has anyone sucessfully used FFMPEG to convert an MKV to MP4 for use on a PS3? Or any ideas?

---

### Post by imtyler on 2010-06-02
I eventually noticed most of the MKV files I had were already H264 video so insted of re-encoding them I just threw in -vcodec copy and converted the audio to aac. The following works:

```
ffmpeg -i input.mkv -vcodec copy -acodec aac -sameq output.mp4
```

And because aac supports the proper audio channels the -ac argument is not required. I feel stupid but I'm posting the solution for anyone who runs in to the same problem.

---

### Post by ron999 on 2010-06-02
That's good.:)

I think that you could also have done the job using:-

First
mkvextract to extract the h264 and aac tracks
Then second
MP4Box to wrap them in a mp4 container.

mkvextract is part of the package mkvtoolnix
and
MP4Box is part of the package gpac

---

### Post by andrew.46 on 2010-06-02
Hi imtyler,

If you use *-acodec aac* you will be using FFmpeg's native aac encoder which many have found lacking in quality. It would be interesting to run a comparison with the external encoder *-acodec libfaac* if that is available to your copy of FFmpeg. If it is not available it is [easily added]("http://ubuntuforums.org/showthread.php?t=1117283"). BTW just have a look if you need to add an *-ab* option as well, I am not sure what the default setting for this is but you may be dropping sound quality too much...

All the best,

Andrew

---

