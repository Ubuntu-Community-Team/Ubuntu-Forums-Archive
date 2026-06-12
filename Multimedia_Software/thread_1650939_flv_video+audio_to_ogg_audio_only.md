---
title: "flv video+audio to ogg audio only?"
date: 2010-12-22
forum: Multimedia Software
---

### Post by kill4killin on 2010-12-22
Is there an application that anyone knows about that I can use to convert either an .flv or .ogg file that contains both audio and video to just an audio .ogg file (preferably vorbis+theora) without audacity? I'm fairly certain audacity could accomplish this but it seems like overkill for what I'm trying to do and the computer I'm trying to use does not run it so well.

::EDIT::
I should also mention that I've tried looking on google. I did find downloadhelper extension for firefox which uses ffmpeg to convert the files but I don't see any obvious way to strip the video.

---

### Post by Jose Catre-Vandis on 2010-12-22
You need to use the **-vn** option to avoid the video part of the file.
```
ffmpeg -i input.flv -vn -acodec vorbis -ac 2 -aq 60 output.ogg
``` (Add/amend options as necessary!)

---

### Post by kill4killin on 2010-12-22
> **Jose Catre-Vandis said:**
> You need to use the **-vn** option to avoid the video part of the file.
```
ffmpeg -i input.flv -vn -acodec vorbis -ac 2 -aq 60 output.ogg
``` (Add/amend options as necessary!)

Oh wow, thank you that was easy!

---

