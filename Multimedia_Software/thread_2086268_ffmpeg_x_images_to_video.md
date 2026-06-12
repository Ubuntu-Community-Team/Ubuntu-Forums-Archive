---
title: "ffmpeg x images to video"
date: 2012-11-20
forum: Multimedia Software
---

### Post by leecooper on 2012-11-20
Hello I have pictures that appear in the following order:
Untitled_000000.jpeg
Untitled_000001.jpeg
Untitled_000002.jpeg
Untitled_000003.jpeg
Untitled_000004.jpeg
Untitled_000005.jpeg
Untitled_000006.jpeg

until : Untitled_000467.jpeg

I want to know how I make them to video AVI in highest possible quality...

some one heve comend line for _ffmpeg_ that makes it?

---

### Post by FakeOutdoorsman on 2012-11-20
AVI is a container format that can support various video and audio formats. AVI is often considered outdated since there are more flexible alternatives such as MKV (Matroska).

Are there certain video and audio formats you require? Is there a specific reason you want AVI? I can't give you a detailed example command without this information.

---

### Post by leecooper on 2012-11-20
hi ido this code

ffmpeg -loop_input -i image%d.jpeg -i music.mp3 -r 25 -qscale 1 -shortest -acodec copy video.mp4


and i get error like this 
[buffer @ 0x9184d00] Changing frame properties on the fly is not supported.
it mean?

---

### Post by syerges on 2012-11-20
3 words... Openshot Video Editor ...exactly what you need to create easily and have a great deal of easy control. If it doesn't create in .avi, then you can use the converter to convert the movie it makes.

---

### Post by FakeOutdoorsman on 2012-11-20
> **leecooper said:**
> hi ido this code

```
ffmpeg -loop_input -i image%d.jpeg -i music.mp3 -r 25 -qscale 1 -shortest -acodec copy video.mp4
```

and i get error like this 
```
[buffer @ 0x9184d00] Changing frame properties on the fly is not supported.
it mean?
```

You didn't answer any of my questions.

Errors are always more useful within the context of the complete console output.

---

### Post by syerges on 2012-11-20
> **leecooper said:**
> hi ido this code

ffmpeg -loop_input -i image%d.jpeg -i music.mp3 -r 25 -qscale 1 -shortest -acodec copy video.mp4


and i get error like this 
[buffer @ 0x9184d00] Changing frame properties on the fly is not supported.
it mean?

1. Why are you making it a .mp4 if you want a .avi?
2. It doesn't like your frame rate, -r ; frame scaling? -qscale ; and/or -shortest whatever that does. Take one out and try it, then a different one, then multiples, until it works, if you must do it by ffmpeg.

---

