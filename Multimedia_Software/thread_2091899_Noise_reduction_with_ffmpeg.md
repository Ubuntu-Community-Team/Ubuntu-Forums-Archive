---
title: "Noise reduction with ffmpeg"
date: 2012-12-06
forum: Multimedia Software
---

### Post by xxlray on 2012-12-06
I archived some old VHS tapes using an stk1160 video grabber. Naturally these are a bit noisy and I read that ffmpeg can do noise reduction in two pass mode. This is what I tried:
```
ffmpeg -i invideo.avi -sameq -vcodec libx264 -nr 1000 -pass 1 -passlogfile passlog -acodec libvo_aacenc outvideo.mp4
ffmpeg -i invideo.avi -sameq -vcodec libx264 -nr 1000 -pass 2 -passlogfile passlog -acodec libvo_aacenc outvideo.mp4
```

Now I have different issues:

1. Audio is gone after the first pass
2. The first pass result looks fragmented and a lot of frames seem to be missing
3. Second pass does not start and gives the following error message:```
[libx264 @ 0x1630d60] constant rate-factor is incompatible with 2pass.
```

---

### Post by FakeOutdoorsman on 2012-12-06
I doubt -nr requires two passes to work properly, but I've never used it. You should use the [hqdn3d](http://ffmpeg.org/ffmpeg.html#hqdn3d) filter for noise reduction. I'm unsure if the so-called "ffmpeg" from the repository has this filter. If that is the case, then you can [compile ffmpeg](http://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide), use a [PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg), or an already compiled [static build](https://ffmpeg.org/download.html#LinuxBuilds).

Do not use -sameq. It [does not mean "same quality"](http://superuser.com/a/478550) and has been removed upstream.

Encoding with two-passes is generally used if you are targeting a specific output file size. In most other cases you should do a single pass with -crf. For two-passes, the first pass does not need to encode the audio, and you don't even need to output to a file. See the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide) for more info.

[One series of tests](http://d.hatena.ne.jp/kamedo2/20120729/1343545890) shows that the native FFmpeg aac encoder provides better quality than libvo_aacenc.

Example:
```
ffmpeg -i input.avi -vcodec libx264 -crf 24 -preset slow -filter:v hqdn3d=4.0:3.0:6.0:4.5 -acodec aac -strict experimental -ab 192k output.mp4
```

---

### Post by xxlray on 2012-12-07
Thank you for the answer. I tried you command but got the following error message:```
Unrecognized option 'filter:v'
```
Afterwards I checked my ffmpeg version:```
$ ffmpeg -version
ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
```
That is why I tried to install the version from the ppas:```
$ sudo add-apt-repository ppa:jon-severinsson/ffmpeg
$ sudo apt-get update && sudo apt-get upgrade
```
There was a warning that because of Ubuntu 12.04 only an older version of ffmpeg could be added by the ppa (I forgot to copy it) and I still get the same error message from ffmpeg while its version seem to not have changed at all.
Furthermore when displaying the version of ffmpeg I can see the following warning:```
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
```
I need not to stick to ffmpeg if you can tell me how to achieve the same in avconv or transcode or whatever.

---

### Post by FakeOutdoorsman on 2012-12-07
> **xxlray said:**
> Thank you for the answer. I tried you command but got the following error message:```
Unrecognized option 'filter:v'
```

Your ffmpeg is too old. Try using "-vf" instead.

> **xxlray said:**
> Afterwards I checked my ffmpeg version:```
$ ffmpeg -version
ffmpeg version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
```

You're not using ffmpeg from FFmpeg. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017).

> **xxlray said:**
> That is why I tried to install the version from the ppas:```
$ sudo add-apt-repository ppa:jon-severinsson/ffmpeg
$ sudo apt-get update && sudo apt-get upgrade
```
There was a warning that because of Ubuntu 12.04 only an older version of ffmpeg could be added by the ppa (I forgot to copy it)

What the PPA installs will most likely be newer than what the repository provides.

> **xxlray said:**
> I still get the same error message from ffmpeg while its version seem to not have changed at all.

In that case the PPA version may not have installed properly. It appears you did not run:
```
sudo apt-get install ffmpeg
```

> **xxlray said:**
> Furthermore when displaying the version of ffmpeg I can see the following warning:```
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
```

This is a poorly worded and potentially misleading message. See the link above. It also means you're not using anything from the PPA.

> **xxlray said:**
> I need not to stick to ffmpeg if you can tell me how to achieve the same in avconv or transcode or whatever.

I do not use avconv. Someone else will have to help you with that.

---

### Post by xxlray on 2012-12-10
> **FakeOutdoorsman said:**
> In that case the PPA version may not have installed properly. It appears you did not run:
```
sudo apt-get install ffmpeg
```
That does not work either:```
$ sudo apt-get install ffmpeg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ffmpeg is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```
Nevertheless the ppa seems to be installed correctly:```
$ ls /etc/apt/sources.list.d/ | grep ffmpeg
jon-severinsson-ffmpeg-precise.list
```
Anyway the vf option seem to have worked. The result looks a lot smoother. Is it possible to protect corners somehow?

---

### Post by FakeOutdoorsman on 2012-12-10
> **xxlray said:**
> Is it possible to protect corners somehow?

Protect corners? Sorry, but I don't understand what you mean.

---

### Post by xxlray on 2012-12-11
Sorry (not a native speaker) I meant edge protection. In theory it is possible to have edge detection e.g. by a Laplace filter and apply no or a smaller linear filter for noise reduction there. I just wonder whether a practical solution exists, too.

---

### Post by FakeOutdoorsman on 2012-12-11
If you show a before and after image then maybe I can provide suggestions.

---

### Post by xxlray on 2012-12-11
I attached a noisy and a denoised still. You can see that the already poor edges get even more blurred when you look at the hand.

---

### Post by FakeOutdoorsman on 2012-12-11
hqdn3d can cause blur. FFmpeg has a filter called "edgedetect", but I don't think it can be used to tell hqdn3d what to do. Perhaps you should investigate Avisynth.

---

### Post by xxlray on 2012-12-12
It seems as if Avisynth is a really good option for video post-processing like denoising. Let's see whether I get it running...

---

### Post by FakeOutdoorsman on 2012-12-12
See [HOWTO: AviSynth video processing with WINE](http://ubuntuforums.org/showthread.php?t=1333264).

---

