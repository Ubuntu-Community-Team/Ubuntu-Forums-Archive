---
title: "Batch remove subtitles from MKV"
date: 2014-04-19
forum: Multimedia Software
---

### Post by vcysion2 on 2014-04-19
I've been searching for a few days on how to do this. I know ways to do it one at a time by remuxing with mkvmerge and the gui. I am trying to find an auto batch way that will just run in the folder and do it because it is going to be over 3000 files, maybe a script or an app that I can just add the folder like JMkvpropedit. I am hoping to find a method that doesn't make me remux since its so many files and hopefuly just one that can just "delete" the sub from the mkv container.

Thanks for any help and ideas.

---

### Post by andrew.46 on 2014-04-19
I wonder if you would be better to use FFmpeg and copy both video and audio streams while excluding the subtitle streams:

```

ffmpeg -i <input> -c:v copy -c:a copy **[COLOR="#FF0000"]-sn[/COLOR]** <output>

```

This could easily be included in a *for* loop and this may be enough for your purpose...

---

### Post by FakeOutdoorsman on 2014-04-20
I think you're going to have to remux. Why do you want to remove the subtites?

Andrew's example should work for all examples except for those that contain multiple streams of the the same type due to the default behavior of [stream selection](https://ffmpeg.org/ffmpeg.html#Stream-selection).
```
ffmpeg -i input.mkv -map 0 -map -0:s -codec copy output.mkv
```

[list]
[*]**-map 0** Include all streams from the first input; your only input in this case. ffmpeg starts counting from 0, so that is why 0 means "first".
[*]**-map -0:s** A negative mapping to exclude all subtitle streams from input 0. Or you could use "-sn" instead of the negative mapping.
[*]**-codec copy** [Stream copy](https://ffmpeg.org/ffmpeg.html#Stream-copy) (remux) instead of re-encode.
[/list]

There are plenty of good Bash "for loop" examples involving ffmpeg on these forums.

---

