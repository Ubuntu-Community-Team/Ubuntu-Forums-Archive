---
title: "Large mp4 file damaged, repair ideas?"
date: 2020-08-30
forum: Multimedia Software
---

### Post by ra7411 on 2020-08-30
This is a 13.6 gig mp4. 
Running this: ffmpeg -i Ren1.mp4 output.webm

gave this:
 
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x560e2e8128c0] moov atom not found
Ren1.mp4: Invalid data found when processing input

Avidemux, Handbrake, VLC can't open it.

Any ideas? Uploading to an online repair site gave initial images indicating repair might be possible, but my isp would take forever to upload it, so I think I need software on my machine to do it, if it's going to get done at all.

Thanks

---

### Post by shantiq on 2020-09-07
have you tried mpv player if there are gaps in a video file it will skip to next bit maybe give it a shot see what it does

```
sudo apt install mpv 
```

then right-click on mp4 and open with mpv

---

### Post by Yellow Pasque on 2020-09-07
[https://github.com/anthwlock/untrunc](https://github.com/anthwlock/untrunc)

---

