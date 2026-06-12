---
title: "Youtube to ipod (MP3)"
date: 2010-09-12
forum: Multimedia Software
---

### Post by Hi-Ho-Silver! on 2010-09-12
How would I go about converting youtube audio to an mp3 and then placing it on my ipod?

Thanks :D

---

### Post by andrew.46 on 2010-09-12
Hi Silver,

In general the best tool to use for stripping and/or converting audio from a media file is FFmpeg. I say 'in general' as Youtube's conditions of use actually preclude offline storage of their material.

However if you are interested in using FFmpeg in this way for *similar* files perhaps beef up your copy of FFmpeg by following this guide:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

Once this is done could you test your file in the following manner:

```
ffmpeg -i *my_file*
```

where you will need to substitute the actual name of your file for my_file. Post the full command and terminal output to this thread and the syntax to create an mp3 can then be demonstrated :).

Andrew

---

