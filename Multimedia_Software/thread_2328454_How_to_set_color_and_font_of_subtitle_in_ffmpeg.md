---
title: "How to set color and font of subtitle in ffmpeg?"
date: 2016-06-21
forum: Multimedia Software
---

### Post by v6rg2 on 2016-06-21
I used this codes for burning subtitle on my video file:

```
ffmpeg -i "input-file" -vf subtitles=filename="subtitile-file.srt":force_style='font-name' -acodec ac3 -vcodec h264 out.mkv
```

But I dont know how to set color and font. Please help me.

---

### Post by FakeOutdoorsman on 2016-06-21
You can use the "ASS v4 styles":
```
-vf "subtitles=subtitle-file.srt:force_style=FontName='Lobster Two,PrimaryColour=&H000000FF'"
```

[list]
[*]In PrimaryColour the H00 is the alpha (transparency). H00 is fully opaque, and FF (ie. 255 in decimal) is fully transparent/invisible.
[*]The 0000FF in the example is a hexadecimal to set the color. In this case it is bright red. Note that it is in the opposite order of HTML colors (red would be FF0000 in HTML).
[*]Alternatively, you could use Aegisub to style the subtitles and then save as an ASS file. Then you wouldn't have to use force_style.
[*]Also see [subtitles filter documentation](http://ffmpeg.org/ffmpeg-filters.html#subtitles) and [ASS Tags](http://docs.aegisub.org/3.2/ASS_Tags/).
[/list]

---

### Post by v6rg2 on 2016-07-25
> **FakeOutdoorsman said:**
> You can use the "ASS v4 styles":
```
-vf "subtitles=subtitle-file.srt:force_style=FontName='Lobster Two,PrimaryColour=&H000000FF'"
```

Thanks a lot. But I have another question. How to set font size? And how work color codes here? I want to set #F4FA58 and dont now how I could.

---

