---
title: "Improving frame rate of screen-recording"
date: 2013-06-09
forum: Multimedia Software
---

### Post by Stonecold1995 on 2013-06-09
I'm trying to record my video game using ffmpeg's x11grab abilities but the output file plays at a very low frame rate.  Because mplayer plays it at a slightly higher frame rate than VLC I think that the video itself is too hard to decode rather than having a low frame rate itself.

The command I used to record was:
```
ffmpeg -xerror -loglevel info -f x11grab -framerate 60 -video_size 640x480 -i :0.0+2,23 -dcodec copy -f pulse -i default -sample_fmt s16 -audio_service_type ma -vol 323 -vcodec libx264 -tune touhou -acodec libvorbis  -y out.avi
```

This is the video file (a very short clip from my game) that seems to play very choppily on my computer:
[http://bayfiles.net/file/QWUj/Y1yQIW/out.avi](http://bayfiles.net/file/QWUj/Y1yQIW/out.avi)

Also, the output file was only ~20 fps I think, even though I set the ffmpeg to record at 60 fps.  Is there a way to have ffmpeg encode the video *after* recording like recordmydesktop is able to, without being even *slower* at that frame rate?  The video is suppose to play at a very smooth 60 fps...

---

### Post by FakeOutdoorsman on 2013-06-09
> **Stonecold1995 said:**
> Is there a way to have ffmpeg encode the video *after* recording like recordmydesktop is able to, without being even *slower* at that frame rate?  The video is suppose to play at a very smooth 60 fps...

You can use a fast encoder for capturing, and then re-encode this output to something more manageable.
```
ffmpeg -f x11grab -framerate 60 -video_size 640x480 -i :0.0+2,23 -f pulse -i default -vcodec libx264 -preset ultrafast -qp 0 -acodec copy output.mkv
ffmpeg -i output.mkv -vcodec libx264 -preset slow -crf 24 -pix_fmt yuv420p -acodec libvorbis -aq 4 output.mkv
```

Also see: [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?t=1392026&p=8746719&viewfull=1#post8746719).

---

### Post by Stonecold1995 on 2013-06-09
> **FakeOutdoorsman said:**
> You can use a fast encoder for capturing, and then re-encode this output to something more manageable.
```
ffmpeg -f x11grab -framerate 60 -video_size 640x480 -i :0.0+2,23 -f pulse -i default -vcodec libx264 -preset ultrafast -qp 0 -acodec copy output.mkv
ffmpeg -i output.mkv -vcodec libx264 -preset slow -crf 24 -pix_fmt yuv420p -acodec libvorbis -aq 4 output.mkv
```

Also see: [HOWTO: Proper Screencasting on Linux]("http://ubuntuforums.org/showthread.php?t=1392026&p=8746719&viewfull=1#post8746719").
Does the first line create a loseless file?  If not how do I get a lossless file (I'm not going to keep it loseless of course, way too big)?

I'm experimenting with recording with the first line you you gave, but it doesn't seem to be doing a great job.  Sometimes it records at a smooth 60 fps, but most of the time it starts out at 60 then, over a few minutes, slowly drops down to around 54 and lower, and this causes very annoying choppiness which does not look good at all for video games.  Even when it drops to 59 fps it can be slightly choppy, especially for bullets that are suppose to move very smoothly, not jump.

In addition (and worse), it seems to occasionally freeze recording, for anywhere between a fraction of a second to a few seconds (ffmpeg shows this because the frame rate drops immediately to ~50, probably because the frame rate hit 0 and the average went down).  I know it's not just my media player choking up because even when I encode the large file to a more managable size it still freezes in the exact same spot for a short time (although the audio continues to play).  I tried shutting down all programs that might be taking up CPU resources, and running ffmpeg with a very low niceness (-19) and that helped a little, but it wasn't great.

Any way to get ffmpeg to record at a perfect 60 frames without gradually slowing down or freezing for short periods of time?


In a 2:42 video, it freezes at 0:22, 0:54, 1:28, 2:04, and 2:35 for varying lengths of time (usually under a second).  This video *should* run at a very smooth 60 fps (I know it's possible, I've seen replays like that on Youtube).
[http://bayfiles.net/file/QZuT/sKsRi9/th062.mkv](http://bayfiles.net/file/QZuT/sKsRi9/th062.mkv)

---

### Post by Stonecold1995 on 2013-06-10
Could the reason the recording gradually slows down be because appending data to a large (and growing) file is slow (I have no idea if it is, just guessing)?  I tried saving the output to /tmp (which I have running in RAM because it's mounted as tmpfs) but the increase in write speed didn't help much or at all (and I should think my hard drive can handle writing ~50mbps to disk anyways, for RAM it should be no problem).

If it does have to do with the increasing file size, is there a way I can get ffmpeg to create a new file after, say, 200 MB is written so it never has to write to a file larger than that?


I also tried setting my game to run at 1/2 frameskip and set ffmpeg to record at 30 fps, but the same exact problem occurs there too.

---

### Post by FakeOutdoorsman on 2013-06-10
> **Stonecold1995 said:**
> Does the first line create a loseless file?
Yes, then the second line re-encodes this huge file to a more manageable size and to a format that should work on YouTube too (although I'd use a lower **-crf** value, such as 18 if uploading to YouTube).

> **Stonecold1995 said:**
> I'm experimenting with recording with the first line you you gave, but it doesn't seem to be doing a great job.

It is worth testing a recent build of real ffmpeg: [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide). This is always my first step when trying to figure out issues when using ffmpeg. Development is very active and bugs are being fixed often and you want to make sure that you're not experiencing a bug that has already been resolved. This can often be done by using a static build, just download, extract, and install [see [instructions](http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453)], but they do not have x11 support.

If you do not see an improvement then the next step is to see where the bottleneck is. Let me know how it turns out and then we can go from there.

---

### Post by Stonecold1995 on 2013-06-10
> **FakeOutdoorsman said:**
> Yes, then the second line re-encodes this huge file to a more manageable size and to a format that should work on YouTube too (although I'd use a lower **-crf** value, such as 18 if uploading to YouTube).



It is worth testing a recent build of real ffmpeg: [How To Compile FFmpeg and x264 on Ubuntu]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide"). This is always my first step when trying to figure out issues when using ffmpeg. Development is very active and bugs are being fixed often and you want to make sure that you're not experiencing a bug that has already been resolved. This can often be done by using a static build, just download, extract, and install [see [instructions]("http://ubuntuforums.org/showthread.php?t=2121268&p=12536453&viewfull=1#post12536453")], but they do not have x11 support.

If you do not see an improvement then the next step is to see where the bottleneck is. Let me know how it turns out and then we can go from there.
I'm about to install the real version.  Is there any easier way to do it?  My /home is set to noexec so I can't put binaries in $HOME/bin.  Is there any simpler way to install than go through all those steps when "sudo apt-get update && sudo apt-get -y dist-upgrade" would be so much easier?  Is there an up to date repository for the "real" ffmpeg?

---

### Post by Stonecold1995 on 2013-06-10
Tried compiling ffmpeg.  Everything worked until the very end, when terminal spit out a bunch of lines like this:
```
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_0_198912367'/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_2_613125930'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_1_847759065'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_1_082392200'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_1_414213562'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_2'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_1_414213562_A'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_0_382683433'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'ff_MM_FIX_0_541196100'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_1_306562965'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_0_847759065'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_0_566454497'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_0_198912367'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_2_613125930'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_1_082392200'
/tmp/alex-tmp.462395b/files/cc9egGA3.ltrans31.ltrans.o:cc9egGA3.ltrans31.o:function column_fidct_mmx.79134.10277: error: undefined reference to 'MM_FIX_1_414213562'
collect2: error: ld returned 1 exit status
make: *** [ffprobe_g] Error 1
```

Everything works until the line "LD      ffmpeg_g" appears while make is running, then it exits with the above error (well, far more lines than that).

---

### Post by FakeOutdoorsman on 2013-06-11
> **Stonecold1995 said:**
> Is there any easier way to do it?
Not really. The static builds are the easy way, but they don't always have what is needed.

> **Stonecold1995 said:**
> My /home is set to noexec so I can't put binaries in $HOME/bin.
Is anything else set to noexec?
```
$ mount | grep noexec
```

> **Stonecold1995 said:**
> Is there any simpler way to install than go through all those steps when "sudo apt-get update && sudo apt-get -y dist-upgrade" would be so much easier?
That would be ideal, but unfortunately Ubuntu doesn't roll that way (excluding any potential up-to-date third-party PPA or repository).

> **Stonecold1995 said:**
> Is there an up to date repository for the "real" ffmpeg?
Not that I know of.

---

### Post by Stonecold1995 on 2013-06-11
> **FakeOutdoorsman said:**
> Is anything else set to noexec?
```
$ mount | grep noexec
```

/proc, /sys, /dev/pts, /home, /run /run/lock, /run/user, and /proc/sys/fs/binfmt_misc.  After I reboot /tmp will also be noexec (just for security, if it breaks something I can change it back and reboot).

---

### Post by FakeOutdoorsman on 2013-06-11
I have no experience with noexec. Maybe someone else has an idea.

---

### Post by Stonecold1995 on 2013-06-11
> **FakeOutdoorsman said:**
> I have no experience with noexec. Maybe someone else has an idea.
All noexec does is prevent binary executables from being run on that filesystem for security.  Scripts still run, but not compiled executables.  Which means some of the instructions to put ffmpeg in /home/bin wouldn't work because ffmpeg would not run in that location.

But my biggest problem now is that ffmpeg won't compile at ALL, not that I can't put it in home.

---

