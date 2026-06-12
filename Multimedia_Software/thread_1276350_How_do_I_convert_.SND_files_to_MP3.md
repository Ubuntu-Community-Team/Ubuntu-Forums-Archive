---
title: "How do I convert .SND files to MP3?"
date: 2009-09-26
forum: Multimedia Software
---

### Post by fester225 on 2009-09-26
I have a single .snd file which I'd like to convert to MP3. It used to work using Winamp in Microsoft but won't play under Amarok. Sox gives me "play formats: no handler for detected file type `video/x-ms-asf'".

How do I convert this .snd file to MP3?

One Internet source says this is a standard Unix format, another says this comes from Apple.

---

### Post by ron999 on 2009-09-27
Have you tried using ffmpeg from the command line?
Try a command like this:-
```
ffmpeg -i <input-file> -acodec mp3 output.mp3
```

---

### Post by SuperSonic4 on 2009-09-27
```
ffmpeg -i input.snd -acodec libmp3lame -ac 2 output.mp3
```

You can tweak bitrate too

---

