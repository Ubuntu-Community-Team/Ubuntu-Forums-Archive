---
title: "Help with FFmpeg please"
date: 2008-11-07
forum: Multimedia Software
---

### Post by brandon88tube on 2008-11-07
I've never been one who was great at encoding video files. I just started using FFmpeg recently and whatever I encode either comes out looking bad or it runs slow because I tried getting the quality really high and paid the price. I read up on the commands for it, but I just don't understand some of the stuff and most of the advanced stuff. What I am trying to do is take a 30 second uncompressed avi that I had rendered out and encode it with a codec that would play on a Windows computer that didn't have any extra codecs installed. The file is 30 seconds long at 30fps and 1280x720 size. I'm hoping to get this to play without being choppy and still have high quality to it, while playing on a standard Windows install. Any help would be greatly appreciate as I am getting desperate. All of my many many attempts have failed in one of those categories whether it be choppy, bad quality or just won't play on Windows.

---

### Post by xzero1 on 2008-11-07
Try this:
ffmpeg -i filename.ext  -sameq filename.mpg

This will create an mpeg1 video with mp2 audio of nearly the same quality video (-sameq) as the original file. If ffmpeg can recognize the input then should be ok.

---

### Post by brandon88tube on 2008-11-08
Yeah, I already tried that and it comes out all choppy/slow. Thanks for trying though.

---

### Post by brandon88tube on 2008-11-08
Anyone else think they can help?

---

### Post by FakeOutdoorsman on 2008-11-08
Do you need to keep it at 1280x720?  What codecs are available in a standard Windows install?  XP or Vista?  Does it come up choppy and slow on all computers, or just the Windows one?

---

### Post by brandon88tube on 2008-11-08
> **FakeOutdoorsman said:**
> Do you need to keep it at 1280x720?  What codecs are available in a standard Windows install?  XP or Vista?  Does it come up choppy and slow on all computers, or just the Windows one?

I think the ones listed in these links [http://ffmpeg.mplayerhq.hu/compat.html](http://ffmpeg.mplayerhq.hu/compat.html), [http://support.microsoft.com/kb/899113](http://support.microsoft.com/kb/899113), [http://www.downloadatoz.com/codecs/windows-media-player-xp-codecs.php](http://www.downloadatoz.com/codecs/windows-media-player-xp-codecs.php)(note that this last link states not all are installed by default) work with XP. If I can keep it at 1280x720 that would be great. Also it is choppy/slow on a couple other computers.

---

### Post by xzero1 on 2008-11-09
It could be your video system is too slow for 1280x720 playback. Some video cards do better when set for 16 bit color or you might try recoding  to a lower fps. Is your cpu maxing out on playback? Could you give us an idea of what you are trying to play this on?

---

### Post by brandon88tube on 2008-11-09
Well I'm trying to play this on some older computers, but the target audience is an unknown factor. I would want it to work on a somewhat lower end computer, that way I cover that lower end and the high end at the same time. I'm willing to drop the resolution if needed to keep the quality up. Any sample code would help. I'm looking at possibly going beyond the basic command of ```
ffmpeg -i origfile.avi -sameq -acodec (some codec) -vcodec msmpeg4v2 newfile.avi
```
I've seen some ffmpeg commands that go for a few lines with all of the advanced configuration. Maybe that would help instead of my basic one. I have even tried forcing the bitrate -b and the fps -r with not much luck.

---

### Post by FakeOutdoorsman on 2008-11-09
You should reduce the resolution since you want to maximize compatibility.  I would start at 640x360.  Try several formats that were listed on the supplied links.  A good starting point:
[LIST]
[*][Which are good parameters for encoding high quality MPEG-4?]("http://ffmpeg.mplayerhq.hu/faq.html#SEC27")
[*][Which are good parameters for encoding high quality MPEG-1/MPEG-2?]("http://ffmpeg.mplayerhq.hu/faq.html#TOC28")
[/LIST]

---

### Post by psyke83 on 2008-11-09
> **brandon88tube said:**
> I've never been one who was great at encoding video files. I just started using FFmpeg recently and whatever I encode either comes out looking bad or it runs slow because I tried getting the quality really high and paid the price. I read up on the commands for it, but I just don't understand some of the stuff and most of the advanced stuff. What I am trying to do is take a 30 second uncompressed avi that I had rendered out and encode it with a codec that would play on a Windows computer that didn't have any extra codecs installed. The file is 30 seconds long at 30fps and 1280x720 size. I'm hoping to get this to play without being choppy and still have high quality to it, while playing on a standard Windows install. Any help would be greatly appreciate as I am getting desperate. All of my many many attempts have failed in one of those categories whether it be choppy, bad quality or just won't play on Windows.

First of all, let me warn that I won't be answering your original question at all ;).

I am guessing you want to play movies on a "restricted" Windows PC? With that in mind, I really suggest you forget about recoding movies; instead grab a copy of [VLC Portable]("http://portableapps.com/apps/music_video/vlc_portable"). It'll play virtually anything you throw at it, and it's configured to run from a folder (e.g. via a USB Flash drive) without modifying the host machine's registry or hard disk in any way.

Unless you intend to play movies on a severely restricted Windows system (i.e. only whitelisted executables allowed), VLC Portable is your best option.

---

### Post by brandon88tube on 2008-11-09
> **psyke83 said:**
> First of all, let me warn that I won't be answering your original question at all ;).

I am guessing you want to play movies on a "restricted" Windows PC? With that in mind, I really suggest you forget about recoding movies; instead grab a copy of [VLC Portable]("http://portableapps.com/apps/music_video/vlc_portable"). It'll play virtually anything you throw at it, and it's configured to run from a folder (e.g. via a USB Flash drive) without modifying the host machine's registry or hard disk in any way.

Unless you intend to play movies on a severely restricted Windows system (i.e. only whitelisted executables allowed), VLC Portable is your best option.

This file is not just for me, but it is for other people at companies to look at. So I don't want to have them download extra stuff otherwise they won't bother looking at it. Its for my portfolio so... Also I don't consider it recoding because its an uncompressed file with no codecs at all. Its more of a raw file in my opinion.

---

