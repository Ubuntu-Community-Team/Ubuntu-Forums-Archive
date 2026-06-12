---
title: "RecordMyDesktop: how to crop and merge resulting videos"
date: 2014-10-18
forum: Multimedia Software
---

### Post by lads on 2014-10-18
I am presently creating a video tutorial for a software tool. I have recorded a few short videos (between 30 seconds and 4 minutes) with RecordMyDesktop that I now need to merge into a single video. The task pipeline looks like the following:

1. Convert the files from *ogv* to *avi* (or another workable format).

2. Crop unwanted sections from the videos (such as the interaction with RecordMyDesktop itself).

3. Merge the various cropped videos into a single file.

Sounds simple, but I have lived a whole saga the past few weeks trying to do it without success. Below I detail the steps I have taken so far and the problems I found.

**Converting *ogv* to *avi***

There are various threads here about this subject, pointing to multiple tools. Many of these threads seem to be outdated but I eventually [succeeded using *avconv*]("http://askubuntu.com/a/123528/177437"), e.g.:

```
avconv -i "input.ogv" -vcodec mjpeg -acodec mp2 -qscale 10 "output.avi"
```

Previously I tried with *ffmpeg*, Avidemux, Lives and others, but all of them fail with errors or crash on Ubuntu 14.04.

With *avconv* there is a visible loss of image quality and a good deal of noise is added to the audio, but none of it is catastrophic.

**Cropping**

For this task the only tool I am aware of that allows cropping at the frame level is Avidemux. Others such as Lives also advertise this functionality but are not able to perform it.

I had no errors performing this task with Avidemux but the resulting videos started to yield problems. Totem is not able to play one of them, issuing an exception; OpenShot also issues a warning when opening some of these videos cropped with Avidemux.

**Merging**

So far I have tried this task with five different tools, all of which failed:

 - **OpenShot**: filled up 4 Gb of RAM and went on to fill 4 Gb of swap, at which point the system became unresponsive, forcing a reboot. In total the cropped avi videos add up to little over 200 Mb.

 - [**avimerge**]("http://www.whileifblog.com/2011/02/09/ubuntu-merge-avi-mpg-or-mpeg-files/"): produces a merged file without issuing warning or error messages but the image and sound are out of sync. There are moments where the sound played is from the parts cropped out in the previous step.

 - **Kino**: also produces a merged file without issuing errors but completely ravishes the image, it constantly flickers and jumps up and down, making it impossible to understand.

 - [**cat** + **mencoder**]("http://www.whileifblog.com/2011/02/09/ubuntu-merge-avi-mpg-or-mpeg-files/"): the end result has similar problems as with **avimerge**.

 - **Avidemux** - eventually found out it is also able to merge files, although the process is not obvious. The resulting videos yield sound and image out of sync; when opening a merged file with a player such as Totem, the length is about the double of what is reported by Avidemux.

**The question**

At this stage I strongly suspect something is going wrong upstream of the merging step, perhaps with the cropping (and thus the detailed story).

My question comes down to: how to perform these three apparently simple tasks with videos produced with RecordMyDesktop? I would appreciate suggestions either for a completely new processing pipeline or to changes in one of the steps. Comments from experienced RecordMyDesktop users are also welcome.

---

### Post by TheFu on 2014-10-18
I've never used ogv ... but I'd do the cropping with Handbrake (assuming ogv can be an input format), then merge the videos with mkvmerge (part of mkvtools). These both work with h.264 video (THE video standard today).

AviDeMux should be able to do this stuff alone. It is just older and I haven't been impressed with the h.264 support.

---

