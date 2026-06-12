---
title: "How to reduce my file size without losing its quality?"
date: 2016-08-07
forum: Multimedia Software
---

### Post by v6rg2 on 2016-08-07
I have a 530 mb file (mp4) and want to upload it in vimeo but there is limit for upload (500 mb). So I want to reduce the size for 30 or 40 mb. How I could do this without losing quality?

---

### Post by ajgreeny on 2016-08-07
You could check the media using mediainfo to find its current bitrate quality then re-encode at lower bit rate though anything you do is likely to affect quality to a certain extent.

You may find that something like handbrake or winff will do this most easily for you unless you are happy to use avconv or ffmpeg in terminal.

---

### Post by FakeOutdoorsman on 2016-08-07
You can't technically use a lossy encoder without losing quality. However, you can't use a lossless encoder because the file will be huge, so you have to accept some quality loss. This does not necessarily mean that the output looks bad.

This is a good case for using two-pass encoding because you're targeting a specific output file size. I can't give you an exact custom example command because you did not provide any info about your input file, but an example is here:
[FFmpeg Wiki: H.264 Video Encoding](https://trac.ffmpeg.org/wiki/Encode/H.264#twopass)

---

