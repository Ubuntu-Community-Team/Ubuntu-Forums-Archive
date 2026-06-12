---
title: "FLV -&gt; Flac"
date: 2011-06-30
forum: Multimedia Software
---

### Post by Spae on 2011-06-30
Anyway to rip the audio from an flv and convert to flac or mp3 without quality loss?

---

### Post by andrew.46 on 2011-06-30
> **Spae said:**
> Anyway to rip the audio from an flv and convert to flac or mp3 without quality loss?

It can be done with FFmpeg (although converting between lossy formats is not the best), but the exact syntax depends on the contents of your flv file. Sometimes these can contain aac sound and then it is simply a matter of copying the aac into a new container. Can you install a copy of FFmpeg and run the command:

```

ffmpeg -i ***[COLOR="Red"]my_file.flv[/COLOR]***
```

against one of your files, of course substituting the name of your own file for ***[COLOR="Red"]my_file.flv[/COLOR]***. It should be a simple matter to suggest the appropriate syntax then...

---

