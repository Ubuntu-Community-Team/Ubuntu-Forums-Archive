---
title: "Can Banshee write to an SD card?"
date: 2011-04-03
forum: Multimedia Software
---

### Post by Mylorharbour on 2011-04-03
I've star rated hundreds of tracks. All I want to do is write the 4* & 5* tracks to an SD card for use elsewhere. Banshee can use Brasero to write them to CD so at a push I could write a CD then copy it back to an SD card but that seems the long way round. Any ideas?

I'm using Banshee 1.8.1 on Lucid.

Cheers.

---

### Post by Mylorharbour on 2011-04-05
Bump........anyone?

---

### Post by knetcomp on 2011-08-20
Copy this to a file named ".is_audio_player" in the root of your SD card. It will then show up as a syncable device in banshee.

```
audio_folders=Music/
video_folders=Video/
folder_depth=2
playlist_formats=audio/x-scpls, audio/mpegurl, audio/x-mpegurl
playback_mime_types=video/mp4-generic, video/quicktime, video/mp4, video/mpeg4, video/3gp, video/3gpp2, application/sdp, audio/3gpp, audio/3ga, audio/3gpp2, audio/amr, audio/x-amr, audio/mpa, audio/mp3, audio/x-mp3, audio/x-mpg, audio/mpeg, audio/mpeg3, audio/mpg3, audio/mpg, audio/mp4, audio/m4a, audio/aac, audio/x-aac, audio/mp4a-latm, audio/wav
coverartfilename=folder.jpg
coverartfiletype=jpeg
coverartsize=200
```

---

