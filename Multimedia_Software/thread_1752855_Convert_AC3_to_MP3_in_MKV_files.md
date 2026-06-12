---
title: "Convert AC3 to MP3 in MKV files"
date: 2011-05-08
forum: Multimedia Software
---

### Post by Philio on 2011-05-08
Hi,

I've got a few videos (MKV) which have AC3 audio, I copied them to my Xoom tablet but AC3 is not supported so there is no sound. Hence I need to convert the audio to MP3, can anyone recommend a good program for doing this?

Thanks!

---

### Post by ron999 on 2011-05-08
Hi
If the files contain a video track and the one ac3 audio track FFmpeg could be used like this:-
```
ffmpeg -i input.mkv -vcodec copy -acodec libmp3lame -ab 128k output.mkv
```

---

### Post by Philio on 2011-05-08
> **ron999 said:**
> Hi
If the files contain a video track and the one ac3 audio track FFmpeg could be used like this:-
```
ffmpeg -i input.mkv -vcodec copy -acodec libmp3lame -ab 128k output.mkv
```

This works, thanks!

Still doesn't play sound on the Xoom though, will try some other formats.

---

