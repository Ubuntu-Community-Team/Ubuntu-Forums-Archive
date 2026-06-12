---
title: "Error nuvexport DivX"
date: 2010-09-16
forum: Mythbuntu
---

### Post by ftirapelle on 2010-09-16
Hi

I have the following problem using nuvexport-Divx:

Invalid value '-part' for option 'mv4'

Any ideas?

```

Choose a function, or episode(s) to remove:  c
Where would you like to export the files to? [.] /home/mythtv/videos
Enable Myth cutlist? [Yes]
Enable noise reduction (slower, but better results)? [No]
Enable deinterlacing? [Yes]
Crop broadcast overscan border (0-5%) ? [1.5]
Audio bitrate? [128]
Variable bitrate video? [No]
Video bitrate? [960]
Default resolution based on requested dimensions.
Width? [624]
Height? [464]

Now encoding:  Il prescelto:  Untitled
Encode started:  Wed Sep 15 22:56:18 2010
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Waiting for mythtranscode to set up the fifos.
Starting ffmpeg.
processed:  0 of 224822 frames at 0 fps (~%, eta: unknown) 

ffmpeg had critical errors:

Invalid value '-part' for option 'mv4'

Cleaning up temp files.
Cleaning up child processes.

```

---

### Post by avelach on 2010-09-16
Have you tried invoking "nuvexport" rather than "nuvexport-divx" and selecting Export to DivX (or to XviD)?

---

### Post by ftirapelle on 2010-09-17
Yes, this is exactly what I meant. I have invoked nuvexport and than selected Export to DivX

---

