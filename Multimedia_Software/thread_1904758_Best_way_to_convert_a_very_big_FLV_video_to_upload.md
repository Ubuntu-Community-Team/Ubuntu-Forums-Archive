---
title: "Best way to convert a very big FLV video to upload it to youtube"
date: 2012-01-05
forum: Multimedia Software
---

### Post by matubaum on 2012-01-05
Hello Community,

I have this problem. I want to upload a video .flv to youtube but is very big (1.8G, Duration: 20 minutes). So I want to know which is the best way to reduce its size, then I'll be able to upload it.

It's just a videotutorial I did with RecordMyDesktop, and edited it with Pitivi. I'd prefer, not to do it again because It was a lot of job, so I just want to reduce its size. But maybe I don't have another choice.

Thanks for any suggestion.

---

### Post by FakeOutdoorsman on 2012-01-05
Can you show some info about your video?
```
ffmpeg -i input.flv
```
This will also show your ffmpeg version so I can give you an example command with the right options suitable for your ffmpeg version.

---

### Post by matubaum on 2012-01-05
Hi, Thanks for the reply...
I put the  output for that command in pastebin: [http://pastebin.com/1wUVMe6a](http://pastebin.com/1wUVMe6a)

---

### Post by FakeOutdoorsman on 2012-01-05
The audio may be troublesome:
```
[flv @ 0x850b2a0] Unsupported audio codec (7)
```
Do you know anything about the audio? How did you make the file? Can you create and upload a small sample (mediafire or datafilehost are ok)? This will make a 2 MB sample from your video:
```
dd if=ProyectoNuevo2.flv of=sample.flv bs=1024 count=2000
```

---

