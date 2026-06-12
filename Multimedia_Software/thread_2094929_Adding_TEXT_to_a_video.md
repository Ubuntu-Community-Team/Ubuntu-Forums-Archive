---
title: "Adding TEXT to a video"
date: 2012-12-15
forum: Multimedia Software
---

### Post by marcopb on 2012-12-15
I'm beginning to record some video using my ubuntu machine.
I'm able to use RecordMyDesktop, but now I'd like to add some text.

I like the caption used for example in this video [http://youtu.be/o6UGPpxg_VQ](http://youtu.be/o6UGPpxg_VQ) starting at 1:20 (I'm trying to contact that youtube user privately).
What Linux software is able to create that kind of text ?
Do you think RecordMyDesktop was used to record that video ? I saw some zoom actions sometime in his video.
Do you know that record software ?

Thanks for any help.

---

### Post by Merrattic on 2012-12-16
You can use Openshot to add text to video.

Titles will do it or you can create your own svg files (say with Inkscape) with transparent background, and use the overlay technique to add them. Takes some fiddling about to get the positioning right, but it works.

In Openshot it appears you have to have the overlays on a track above the video track

---

### Post by FakeOutdoorsman on 2012-12-16
You can use the drawtext filter in ffmpeg if you'd like a command-line solution. I'm unsure if the so-called "ffmpeg" in the repository contains this filter. If not, then you can [compile ffmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide), use [Jon Severinsson's FFmpeg PPA](https://launchpad.net/~jon-severinsson/+archive/ffmpeg), or use an already compiled [static build](http://ffmpeg.org/download.html#LinuxBuilds).

See [How to Encode Videos for YouTube and other Video Sharing Sites](https://ffmpeg.org/trac/ffmpeg/wiki/EncodeforYouTube). It has a bunch of drawtext examples, including one that will create a colored box around the text somewhat like the video you linked to.

One downside is really long text might have to be broken up with two drawtext filters since I'm not sure if it has any line breaking capabilities.

---

