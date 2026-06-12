---
title: "FFmpeg encoder CLI command to encode an entire directory (or GUI)"
date: 2011-05-21
forum: Multimedia Software
---

### Post by akand074 on 2011-05-21
Hey,

I installed the latest FFmpeg and x264 via [this]("http://ubuntuforums.org/showthread.php?t=786095") thread. I'm just wondering if there was a single command possible to encode an entire directory of videos (>100 video files) all to x264 codec with MKV container (with support for multi-threaded CPUs of course). Otherwise, is there a particular GUI front-end for the ffmpeg encoder I set up that you would particularly recommend that will allow me to do that? 

Thanks!

---

### Post by andrew.46 on 2011-05-22
It can be done with a *for* loop. Are these files all the same type, as in all .mp4, .flv or .avi?

---

### Post by akand074 on 2011-05-22
> **andrew.46 said:**
> It can be done with a *for* loop. Are these files all the same type, as in all .mp4, .flv or .avi?

Yeah, they are all in some stupid real media format, which is why I'm considering re-encoding them. Though most of them are .rmvb, a small amount are .rm, no big deal as I can just run two commands, one for each?

EDIT: Oh, and I would like the output to have the same file name as the input for each file. Not sure if that's a problem, just thought I'd mention it.

---

### Post by andrew.46 on 2011-05-22
rmvb files used to pose a bit of a problem for FFmpeg and some may still be problematic. Perhaps try a test run of something like the following, from the directory that your files are in:

```

for f in *.rmvb
do 
ffmpeg -i "$f" -acodec libfaac -aq 100 -vcodec libx264 -preset slow -crf 22 -threads 0 "${f%.rmvb}.mkv"
done

```

The FFmpeg syntax is drawn from Fakeoutdoorsman's guide. Hopefully FFmpeg will not choke on your rmvbs but some can be difficult still...

---

### Post by akand074 on 2011-05-22
Success. That worked! I just copied 5 files into a new directory to test it out and it worked fine, it didn't choke on the file types. I'll likely tweak with the ffmpeg settings from the default but the loop worked perfectly.

---

### Post by andrew.46 on 2011-05-22
Excellent news! Tweak to your heart's content that is in part what FFmpeg is all about :).

---

