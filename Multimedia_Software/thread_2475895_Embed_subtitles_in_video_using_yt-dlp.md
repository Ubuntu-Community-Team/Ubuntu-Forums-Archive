---
title: "Embed subtitles in video using yt-dlp"
date: 2022-06-11
forum: Multimedia Software
---

### Post by py-ohayo on 2022-06-11
Hello,
According to the **yt-dlp** manual, this tool allows to embed subtitles in a downloading video, but there is no any example of how to do it.
Has anyone experienced such problems?
Thanks.

---

### Post by andrew.46 on 2022-06-12
Have you experimented with the following yt-dlp option?

```

 --embed-subs  Embed subtitles in the video (only for mp4, webm and mkv videos)                                                 

```

If you have tried this and had some difficulty could you give a link to a decent Youtube clip with subtitles and I will have a go. I suspect that you will need a copy of FFmpeg installed to do the heavy lifting with the subtitles.

The subtitle options for yt-dlp are [here...]("https://github.com/yt-dlp/yt-dlp#subtitle-options")

---

### Post by py-ohayo on 2022-06-14
Yes I tried all these options.
Here is a link with subtitles I couldn't embed:
[www.arte.tv/fr/videos/092925-000-A/un-million-d-annees/](www.arte.tv/fr/videos/092925-000-A/un-million-d-annees/)

---

### Post by andrew.46 on 2022-06-16
Unfortunately that site and all of its videos seems to be behind a geographical block, not available in my country...

---

### Post by shantiq on 2022-07-06
looks [like]("https://github.com/yt-dlp/yt-dlp#subtitle-options")

```
--write-auto-subs
``` should do that  

cannot test here as ARTE site not working for me with yt-dlp at the moment; but surely that is the one

---

### Post by py-ohayo on 2022-07-06
I confused "embedding" and "burning".
Indeed, the tool embed the subtitles as metadata.
Burned-in subtitles are viewable with any player as they are rendered with frames, while embedded subtitles are only viewable with, say, "smart" players like VLC... e.g. Windows default "Movies & TV" player cannot display embedded subtitles.

---

