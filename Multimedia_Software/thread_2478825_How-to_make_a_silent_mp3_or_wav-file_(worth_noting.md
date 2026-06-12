---
title: "How-to make a silent mp3 or wav-file (worth noting)"
date: 2022-09-06
forum: Multimedia Software
---

### Post by engrenage on 2022-09-06
I couldn't reply to the original thread[^1] because it is marked as closed.

IMHO the best solution so far was posted by [**[COLOR=#000000]FakeOutdoorsman[/COLOR]**]("https://ubuntuforums.org/member.php?u=162846") but there is really a problem with it.

Silence is silence ; it's basically a bunch of zeroes aligned after each other.

Bitrate in an audio file determines the "resolution" of the sound ; quite similar to the number of pixels of a picture.

So if you want hours long of silence (and for the original question, this is not really the way one would want to do it, it's just a workaround) is like having a white background on your desktop : you can take a single white pixel and rescale it to whatever size you need, so you'll end up with a much smaller file.

Same for audio, so using a 48kHz bitrate for 6 or 8 hours of silence is plain naive ; for WAV, it is wiser to replace the command with (change 48000 to 1)

```
ffmpeg -ar 1 -t 60 -f s16le -acodec pcm_s16le -ac 2 -i /dev/zero -acodec copy output.wav
```

so you have a 1Hz-resolution file that will be quite exactly 48000 times smaller than [[COLOR=#000000]FakeOutdoorsman[/COLOR]]("https://ubuntuforums.org/member.php?u=162846")'s suggestion, and the exact same result to your ear. The environment (nature, the birds, the chinese children working in factories...) will see the difference. 

It can still be further improved by tuning the codec parameters [https://ffmpeg.org/ffmpeg-codecs.html#wavpack](https://ffmpeg.org/ffmpeg-codecs.html#wavpack) with additional parameters such as -q:v 1000 and skip_empty_cb true ; then your wave file will be more than 100'000x smaller than what one would "normally" come up with


[^1] : [https://ubuntuforums.org/showthread.php?t=1911430](https://ubuntuforums.org/showthread.php?t=1911430)

---

