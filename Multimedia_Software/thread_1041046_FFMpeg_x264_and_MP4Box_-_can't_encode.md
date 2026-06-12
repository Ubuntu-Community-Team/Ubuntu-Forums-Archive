---
title: "FFMpeg x264 and MP4Box - can't encode"
date: 2009-01-16
forum: Multimedia Software
---

### Post by listerthrawn on 2009-01-16
Hi,

I've been trying to encode some video for my iPod and I followed the guide on the wiki.  I installed ffmpeg from the repos and successfully encoded my video.

I then went to use MP4box to get it to be accepted in iTunes and when I installed gpac (from repos) it uninstalled the libavcodec-51-unstripped (or something like that, I'm not at home at the moment) and installed libavcodec51.

I ran the MP4Box which worked fine, but then when I try and encode again, ffmpeg can't find libx264.  I removed gpac and reinstalled libavcodec51unstripped and ffmpeg works again now.

Is this supposed to happen or did I do something wrong here?

Thanks

Chris

---

### Post by FakeOutdoorsman on 2009-01-16
I can confirm this.  Looks like gpac doesn't like libavcodec-unstripped-51 and demands libavcodec51.  For those who don't know, the unstripped version allows ffmpeg to encode to some restriced formats that aren't available in the default ffmpeg in the repository.  I suppose you can try to compile gpac yourself, but I haven't done this for some time and I don't remember what the dependencies are.

Another option is to compile ffmpeg and x264 because as of yesterday some new iPod presets were introduced which makes things a little easier:

[HOWTO: Compile the latest ffmpeg and x264 from source](http://ubuntuforums.org/showthread.php?t=786095)

Now encode using the presets.  For a one-pass 640x480 CRF encode:
```
ffmpeg -i input.avi -acodec libfaac -ab 128k -s 640x480 -ac 2 -vcodec libx264 -vpre hq -vpre ipod640 -crf 22 -threads 0 ffmpegoutput.mp4
```

Now run it through MP4Box so it works with iTunes:
```
MP4Box -add ffmpegoutput.mp4 newoutput.mp4
```

I don't know if gpac (or libavcodec51 specifically) will interfere with a self-compiled ffmpeg/x264.  Looks like I have some testing to do.

You could also try qt-faststart instead of gpac/MP4Box for iTunes friendlyness:
```
cd ~/ffmpeg/tools
make qt-faststart
qt-faststart ffmpegoutput.mp4 newoutput.mp4
```

**Edit:** A bug report has already been made:
[Bug #314524 in gpac (Ubuntu): gpac depends on libavcodec51, should depend on libavcodec51 | libavcodec-unstripped-51](https://bugs.launchpad.net/ubuntu/+source/gpac/+bug/314524)

> I don't know if gpac (or libavcodec51 specifically) will interfere with a self-compiled ffmpeg/x264.  Looks like I have some testing to do.
**Edit 2:** I briefly tested this and didn't run into any problems.

---

### Post by listerthrawn on 2009-01-17
Thanks very much for your thorough and detailed answer.

I'm just working through your howto now and getting it all up and working.

I'll post back when I know everything's working.

Cheers

---

### Post by listerthrawn on 2009-01-18
Everything works a treat with the newly compiled ffmpeg.  Not tried the video on my iPod yet, but I'm sure it will be good.

(I do have one minor issue, but I'll raise that in another thread)

Thanks!

---

