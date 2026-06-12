---
title: "How to convert DVDs to MP4 (H264)?"
date: 2008-06-14
forum: Multimedia Software
---

### Post by the lemming on 2008-06-14
Hello

Could somebody please explain how I can convert movies which are unencrypted VOBs into MP4 H264?

I have a large collection of DVDs which I am in th process of putting onto my hard drive so that I don't have to worry about the DVD disks corrupting. I am also hoping that one day I will have a portable device that I can then use to watch my movies while "on the go".

At the moment I'm using DVD Shrink to make movies onto a 4.5gb blank disk and then re-encode the VOB files again with Stax Rip so that I can create MP4 files that are a 10th of their original size.  However I'm doing this with free Microsoft applications but I'd like to learn how to do this with Ubuntu.

I am NOT asking how to unencrypt movies.  I'm just asking how to convert VOBs to MP4.

Cheers

---

### Post by Trollslayer on 2008-06-14
> **the lemming said:**
> Hello

Could somebody please explain how I can convert movies which are unencrypted VOBs into MP4 H264?

I have a large collection of DVDs which I am in th process of putting onto my hard drive so that I don't have to worry about the DVD disks corrupting. I am also hoping that one day I will have a portable device that I can then use to watch my movies while "on the go".

At the moment I'm using DVD Shrink to make movies onto a 4.5gb blank disk and then re-encode the VOB files again with Stax Rip so that I can create MP4 files that are a 10th of their original size.  However I'm doing this with free Microsoft applications but I'd like to learn how to do this with Ubuntu.

I am NOT asking how to unencrypt movies.  I'm just asking how to convert VOBs to MP4.

Cheers

You can transcode them into another format. I use MythTV to improt DVDs as VOBs or ISOs.

---

### Post by cozmicharlie on 2008-06-14
I use Avidemux but there are other methods also.  You can use ffmpeg or mencoder via the command line.  The commands are really very easy and if you are repeating the same functions you could use a script.  Check the forums, you can probably find one.  If you want a gui for ffmpeg then Winff is a small front end for ffmpeg.  The problem with winff is you have to encode each vob separately.  I use vobmerge in wine to merge the vob into one vob then encode with winff.  Handbrake is another very powerful program but not as easy to install.  For me, I went with Avidumux.  It does everything I want.  You also may want to look at compiling ffmpeg and x264 from source rather than use the one from the repos (there is a good tutorial in the forums).  If you decide to use ffmpeg from the repos make sure it is from the medibuntu repository.

---

