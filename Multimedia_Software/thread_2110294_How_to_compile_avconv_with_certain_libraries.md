---
title: "How to compile avconv with certain libraries"
date: 2013-01-29
forum: Multimedia Software
---

### Post by gachnar on 2013-01-29
I have a few questions when it comes to compiling avconv to enable a few extra options. 

First off, what are the normal options that avconv is compiled with?
Second, how do I add the liba-s-s option? (minus the -'s) (Stupid language filter)

I know this will vaguely involve using git to clone the source and all that, can someone help me get this figured out?

---

### Post by mc4man on 2013-01-29
Not sure avconv supports libass, wouldn't be surprised if it doesn't yet, they need to figure how to 'make it their own'

You may be better served using the real FFmpeg, very good guide here - 
[https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

---

### Post by gachnar on 2013-01-30
I had tried that, as far as building ffmpeg with the libass support, but when I tried running it using the newfound filter, it didn't overly/burn-in the subtitles like I wanted. Is there something I missed?

I tried running the command as follows:

ffmpeg -i SomeVideoFile.mkv -c:v copy -c:a copy -vf "***=SomeVideoFile-Subs.***" SomeVideoFile-Transcoded.mp4

*** = a-s-s (minus the -'s)

---

### Post by gachnar on 2013-01-30
I had tried that, as far as building ffmpeg with the libass support, but when I tried running it using the newfound filter, it didn't overly/burn-in the subtitles like I wanted. Is there something I missed?

I tried running the command as follows:

ffmpeg -i SomeVideoFile.mkv -c:v copy -c:a copy -vf "***=SomeVideoFile-Subs.***" SomeVideoFile-Transcoded.mp4

---

### Post by mc4man on 2013-01-30
> **gachnar said:**
> , but when I tried running it using the newfound filter, it didn't overly/burn-in the subtitles like I wanted. Is there something I missed?

No clue here -  have only been concerned with subs previously on dvd sources & would always use DVDSubEdit  (win only

You should just start a new thread specific to FFmpeg & lib.a*s in this forum, there should be some decent responses..

---

### Post by evilsoup on 2013-01-30
```

ffmpeg -i SomeVideoFile.mkv -c:v copy -c:a copy -vf "***=SomeVideoFile-Subs.***" SomeVideoFile-Transcoded.mp4

```Video filters are fundamentally incompatible with '-c:v copy'; you'll need to re-encode . Use '-c:v libx264' for h.264 video (the standard video codec for the MP4 container), [see here]("https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide") for a guide to its usage.

---

### Post by FakeOutdoorsman on 2013-01-30
Also see [How to burn subtitles into the video with FFmpeg](https://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20burn%20subtitles%20into%20the%20video).

---

### Post by gachnar on 2013-01-30
I will go ahead and start a new thread as I have gotten ffmpeg compiled with libass and x264 support. Thanks all for the replies and help.

---

### Post by mc4man on 2013-01-30
> **gachnar said:**
> I will go ahead and start a new thread as I have gotten ffmpeg compiled with libass and x264 support. Thanks all for the replies and help.
You may want to ck. out posts 6 & 7 first

---

