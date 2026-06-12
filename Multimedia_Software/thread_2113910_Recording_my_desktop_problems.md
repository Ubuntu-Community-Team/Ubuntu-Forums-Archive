---
title: "Recording my desktop problems"
date: 2013-02-08
forum: Multimedia Software
---

### Post by manolos on 2013-02-08
Hi all.

Im on Ubuntu 12.10 64 minimal install, fluxbox, with all latest updates and programs to record my desktop like recordmydesktop and instanbul. I have no problem at all, no lag, nothing. Ofcourse if i try to play my output videos with mplayer no problem.

The problem is when i upload my ogv file to youtube. The image is flickering or big pixels covering the screen. How do i fix this? Do i need to convert it before the upload?

Forgot to mention Nvidia drivers. Thanks.

---

### Post by FakeOutdoorsman on 2013-02-08
I suppose YouTube still has issues decoding Theora video from recordmydesktop. You can re-encode it with ffmpeg, which can decode these oddball files:

```
ffmpeg -i input.ogv -vcodec libx264 -preset fast -crf 18 -acodec copy output.mkv
```

I don't know if the 'tube will grok Vorbis audio in MKV. Probably can. If not:
```
ffmpeg -i input.ogv -vcodec libx264 -preset fast -crf 18 -acodec libmp3lame -aq 2 output.mkv
```

Adjust quality as described in the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide).

If you need ffmpeg (and the not bizarro junk in the repo) then you can easily use a [static build](http://ffmpeg.org/download.html#LinuxBuilds).

---

### Post by manolos on 2013-02-08
> **FakeOutdoorsman said:**
> I suppose YouTube still has issues decoding Theora video from recordmydesktop. You can re-encode it with ffmpeg, which can decode these oddball files:

```
ffmpeg -i input.ogv -vcodec libx264 -preset fast -crf 18 -acodec copy output.mkv
```

I don't know if the 'tube will grok Vorbis audio in MKV. Probably can. If not:
```
ffmpeg -i input.ogv -vcodec libx264 -preset fast -crf 18 -acodec libmp3lame -aq 2 output.mkv
```

Adjust quality as described in the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide).

If you need ffmpeg (and the not bizarro junk in the repo) then you can easily use a [static build](http://ffmpeg.org/download.html#LinuxBuilds).

thanks. i have ffmpeg but i didnt know how to use it properly.

---

