---
title: "Seek advice on selecting video editing software"
date: 2022-02-05
forum: Multimedia Software
---

### Post by satimis on 2022-02-05
Hi all,

Please advise which video editor I have to use?

I have been searching for a video editor to enhance the video quality of the video captured in about 1990 with Sony V8 Video Camera on V8 tapes.  The V8 tapes were latter converted to VHS tapes.  Recently I sent 2 VHS tapes to a profession shops ripping them on DVD.  I have copied the .VOB files on DVD to computer.

Playing the .VOB files on computer I found certain sections not very clear.  I ran ffmpeg to trim those unclear secontions on computer and have tested them on AVS Video Editor applying sharpen effect.  But the result is not very good.  Maybe I'm not experienced on AVS Video Editor?

I have following video editing software downloand/running:-

AVS Video Editor - running on Windows 10
Shotcut - Running on Ubuntu 20.04
Avidemux - running on Ubuntu 20.04
Filoma - download
Video Enhancer - download
AviSynth - download

I'm running both Linux and Windows PCs here.

Please advise.  Thanks in advance

Regards

---

### Post by linuux on 2022-02-15
I plan on trying Shotcut, Kdenlive, Davinci Resolve and maybe Olive.  I dunno which to try first.   I haven't tried video editing software before but supposedly, Shotcut is pretty user friendly and good for beginners.  

It's unfortunate that more people haven't posted replies and there doesn't seem to be much interest (?) in video editing software or maybe it's just on here?   Please post folowups if you try one of those you listed. 

My computer only has 8gb of RAM and is limited to a max. of 16gb (DDR3/Intel 4th gen system) so I'm a bit concerned about that.   I might have to choose shotcut or kdenlive since they are not resource heavy, apparently.

---

### Post by satimis on 2022-02-15
> **linuux said:**
> I plan on trying Shotcut, Kdenlive, Davinci Resolve and maybe Olive.  I dunno which to try first.   I haven't tried video editing software before but supposedly, Shotcut is pretty user friendly and good for beginners.  

It's unfortunate that more people haven't posted replies and there doesn't seem to be much interest (?) in video editing software or maybe it's just on here?   Please post folowups if you try one of those you listed. 

My computer only has 8gb of RAM and is limited to a max. of 16gb (DDR3/Intel 4th gen system) so I'm a bit concerned about that.   I might have to choose shotcut or kdenlive since they are not resource heavy, apparently.
I have been searching around for solution to enhance my old 1990 video but unfortunately up-to-now having not find a solution.  I have tried it on ffmpeg and Avs Editor but the result is not much improvement.

I'm now installing DaVinci Resolve 17 on Win10 and Ubuntu 20.04 but unfortunately I couldn't make in to work on Ubuntu 20.04.  Installation went through without problem but it can't start.  DaVinci Resolve 17 works on Win10 running on bare-metal PC with graphic card installed.  It can't work on PC running AMD CPU graphics.

Afterwards I'll start my test enhancing old videos.  I have quite strong PCs here with 32G RAM installed.

If successful I'll post my result here.

---

### Post by VanillaMozilla on 2022-03-18
I think you're asking a lot.  I assume you started 8-mm video tapes.  Those do not have great quality by today's standards.  But then you have two analog conversions, plus you will have to reincode the videos from vob files.  The analog conversions could be devastating to whatever quality was there initially.  Once the quality is lost there really isn't a way to put it back.  It's possible that there is some miracle cure for lost quality as there is for still pictures, but I am not aware of such software for videos

Also, be aware that vob files are a mess internally, and are not really ideal for playback or editing.  Playback may be chaotic when they are removed from the DVDs, with synchronization problems and worse.  I think the synch problems have been fixed in recent Avidemux and other programs, but I used to use a commercial (Windows?) program to repair the files.  It won't fix the quality.

If you have problems with the vob files, you might try ripping the DVDs again with Handbrake to convert directly to .mp4 or .ogv.  You will need to crop a few lines off the bottom, and it won't restore the lost quality, but at least it does reincode pretty well.

I honestly don't know how to advise you.  I suggest you try a video forum, but I think most people have forgotten all about anything older than current digital editing programs.

---

### Post by satimis on 2022-03-18
> **VanillaMozilla said:**
> I think you're asking a lot.  I assume you started 8-mm video tapes.  Those do not have great quality by today's standards.  But then you have two analog conversions, plus you will have to reincode the videos from vob files.  The analog conversions could be devastating to whatever quality was there initially.  Once the quality is lost there really isn't a way to put it back.  It's possible that there is some miracle cure for lost quality as there is for still pictures, but I am not aware of such software for videos

Also, be aware that vob files are a mess internally, and are not really ideal for playback or editing.  Playback may be chaotic when they are removed from the DVDs, with synchronization problems and worse.  I think the synch problems have been fixed in recent Avidemux and other programs, but I used to use a commercial (Windows?) program to repair the files.  It won't fix the quality.

If you have problems with the vob files, you might try ripping the DVDs again with Handbrake to convert directly to .mp4 or .ogv.  You will need to crop a few lines off the bottom, and it won't restore the lost quality, but at least it does reincode pretty well.

I honestly don't know how to advise you.  I suggest you try a video forum, but I think most people have forgotten all about anything older than current digital editing programs.
I have been struggling several months, searching intensively on Internet and testing Video Editing software such as Avidemux/AviSynth/Davinci Resolve 17/VirtualDub2/Shotcut/OpenShots etc. on both Linux and Windows environments.  The device used to capture video was Sony's 1st generation V8 Video Camera.

My conclusion is;
1) No single Video Editing Software can solve all problem
2) No one parameter/setting can solve all problem.

It is because the videos were captured in different environments, indoor and outdoor/nature.  All videos captured outdoor are quite clear.  Only the videos captured indoors were not sharp.

My attempt wers as follows;
1) Trim the video ripped by profession shop from VHS tape on DVD to small clips, running ffmpeg
2) Upgrade the clips to;
Resolution: 1080P 1920x1080 (16:9)
Bitrate: 3000/5000 kbps
Frame Rate: 25/30 fps
3) Edit the clips on Shotcut with different filters and settings

Now it seems working.  The videos captured indoor are much sharper.  I trust if putting more effort, treating frames with different filters and different settings, the result will be even better.  But I would stop here.

Now I'm prepared running OpenShot to assemble the clips.

Video Forum didn't help me out

Regards

---

### Post by silvainstiles1 on 2022-10-30
Hi! There are a lot of different video editors out there, and it depends on what you're looking for in terms of features and functionality. Suppose you're just looking to enhance the video quality. In that case, you might want to try video editing software that has some built-in video enhancement features, like Video Enhancer or Filmora. If you're more experienced with video editing, you might want to try more powerful software like Shotcut or Avidemux. Movavi ([https://www.movavi.com/support/how-to/compress-video-for-instagram.html](https://www.movavi.com/support/how-to/compress-video-for-instagram.html)) also has cool video editing software to offer. Ultimately, it's up to you to decide which software is best for your needs.

---

### Post by satimis on 2022-10-30
> **silvainstiles1 said:**
> Hi! There are a lot of different video editors out there, and it depends on what you're looking for in terms of features and functionality. Suppose you're just looking to enhance the video quality. In that case, you might want to try video editing software that has some built-in video enhancement features, like Video Enhancer or Filmora.
I'm searching video enhancement features to improve blur video.  Any suggestion?  Thanks

Regards

---

### Post by zhengye78 on 2023-07-28
OpenShot, Kdenlive Shotcut, Lightworks and DaVinci Resolve.
Among all of these, I use shotcut consistently. The learning curve isn't bad, supports hardware encoding, and has a decent set of out of the box effects.
but it is also somewhat basic compared to Davinci Resolve. 
Davinci Resolve is much more well known, and probably will have overtaken it with how much it gets recommended.
[https://pctechtest.com/best-video-editing-software](https://pctechtest.com/best-video-editing-software)

---

### Post by satimis on 2024-06-29
Hi all,

Finally I figure out the problem.  Only OpenShot Appimage, the daily built version, works on Ubuntu 22.O4/24.04

Download V3.2.0
[https://www.openshot.org/download/#daily](https://www.openshot.org/download/#daily)

**[COLOR="#FF0000"]Steps performed:[/COLOR]**
right click on the AppImage
-> choose Properties
-> mark the file as Executable

Right-click the AppImage -> Run (to start OpenShot)
Import video (.mp4)
add video to track

Now I can play and edit the video without problem.

I have been running OpenShot for prolonged time, on Ubuntu in the past, without problem.  Its alternative is ShotCut.  I'm not well experienced on ShotCut.  I have to start from the beginning.

Regards

---

