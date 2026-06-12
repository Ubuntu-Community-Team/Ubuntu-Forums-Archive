---
title: "How to render subtitles into avi with avconv?"
date: 2012-12-14
forum: Multimedia Software
---

### Post by sslapp on 2012-12-14
Is possible to render subtitles into an avi (rendered into de video stream) file with avconv?

Thank you.

---

### Post by andrew.46 on 2012-12-20
Looks like it is now possible:

[http://git.videolan.org/?p=ffmpeg.git;a=commit;h=28338bc2a3bb316cde2dfc308722c3cdc3d7b046](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=28338bc2a3bb316cde2dfc308722c3cdc3d7b046)

but for this you will have to compile your own, changes in the source tree of November of 2012 won't hit Ubuntu for quite some time :). I have just taken the new filter for a ride now and it works very nicely...

---

### Post by SeijiSensei on 2012-12-20
For AVI files, mencoder has had this ability for ages.  See, for instance, [http://ubuntuforums.org/showthread.php?t=1155877](http://ubuntuforums.org/showthread.php?t=1155877).

Mencoder's primary target during development was AVI, so even though it's old and not really being developed any more, mencoder still does an excellent job with AVI's.  (That's not all, of course!)

---

### Post by andrew.46 on 2012-12-21
Mind you I think we should all follow the lead of the Handbrake people and officially deprecate the avi container...

---

### Post by FakeOutdoorsman on 2012-12-21
> **sslapp said:**
> Is possible to render subtitles into an avi (rendered into de video stream) file with avconv?

Thank you.

Probably not, but you can with ffmpeg as Andrew mentioned with the "a-s-s" (the hypens are due to forum censorship) or "subtitles" filters. libav does not cherry pick or merge much from FFmpeg, so it lacks many filters among other things. Another "bonus" for Ubuntu users as a result of switching from FFmpeg to libav.

See [How to burn subtitles into the video](http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20burn%20subtitles%20into%20the%20video) for examples, and [How to Compile FFmpeg and x264 on Ubuntu](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) if you'd like to give it a try.

---

### Post by andrew.46 on 2012-12-21
> **FakeOutdoorsman said:**
> Probably not, but you can with ffmpeg as Andrew mentioned with the "a-s-s" (the hypens are due to forum censorship) or "subtitles" filters. libav does not cherry pick or merge much from FFmpeg, so it lacks many filters among other things. Another "bonus" for Ubuntu users as a result of switching from FFmpeg to libav.

Indeed the [libav git branch]("http://git.libav.org/?p=libav.git") is silent about liba*s*s...

---

### Post by SeijiSensei on 2012-12-21
> **andrew.46 said:**
> Mind you I think we should all follow the lead of the Handbrake people and officially deprecate the avi container...

To be clear, I wasn't endorsing the AVI container, but simply mentioning that mencoder does well when converting things to that target.

Matroska is clearly the best available container format, but getting commercial entities like television manufacturers to adopt anything created in the open world is like pulling teeth.  All of them.

---

### Post by evilsoup on 2012-12-21
Most modern TVs should support MP4 video. It's not as flexible as MKV (seriously terrible softsub support), but it's certainly an improvement over AVI. Of course, that doesn't help people who don't have the latest tech.

> **FakeOutdoorsman said:**
> 
See [How to burn subtitles into the video]("http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20burn%20subtitles%20into%20the%20video") for examples, and [How to Compile FFmpeg and x264 on Ubuntu]("http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide") if you'd like to give it a try.

It should be noted that, as of me writing this, that compilation guide doesn't include how to compile ffmpeg with hard-subtitles-burning support.  To do that, you need to install libass-dev at the 'installing dependencies' stage, and add the flag --enable-libass to the ./configure stage of ffmpeg.

Something that probably won't come up but that should be kept in mind, is that the subtitle filter doesn't seem able to handle filenames with funny characters, even if they're contained within "".

Fake Outdoorsman, I know it's your guide originally, would you be OK for me to add these steps into the compilation?

---

### Post by FakeOutdoorsman on 2012-12-21
> **evilsoup said:**
> It should be noted that, as of me writing this, that compilation guide doesn't include how to compile ffmpeg with hard-subtitles-burning support.  To do that, you need to install libass-dev at the 'installing dependencies' stage, and add the flag --enable-libass to the ./configure stage of ffmpeg.

That would be a good addition.

> **evilsoup said:**
> Something that probably won't come up but that should be kept in mind, is that the subtitle filter doesn't seem able to handle filenames with funny characters, even if they're contained within "".

This may have been mentioned on a ffmpeg mailing list sometime, but I have a poor memory. I recommended trawling the bug tracker and making a report if there isn't one already, or asking about it on the ffmpeg-user mailing list.

> **evilsoup said:**
> Fake Outdoorsman, I know it's your guide originally, would you be OK for me to add these steps into the compilation?

Yes, of course. It is a wiki now, but thanks for asking.

---

