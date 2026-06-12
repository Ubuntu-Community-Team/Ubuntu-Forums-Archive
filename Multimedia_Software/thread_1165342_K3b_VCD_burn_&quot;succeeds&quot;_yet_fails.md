---
title: "K3b VCD burn &quot;succeeds&quot; yet fails"
date: 2009-05-20
forum: Multimedia Software
---

### Post by t0p on 2009-05-20
I've got some (.flv) flash video files that I want to write to video CDs (my optical drive is CD-RW but DVD-ROM).  I used ffmpeg to convert the flash video file to VCD mpeg format like so:

```
ffmpeg -i file.flv -target pal-vcd file.mpg
```

Then I used K3b to burn the file to a CD.  The burn seemed to go fine - K3b reported success.  But, after I closed K3b, the CD did not appear on my Desktop or in Places.  After I physically eject and replace the disc, it just doesn't show up on the computer.  And when I stick it in a DVD-Video player, I just get an "Unknown Disc" message.

Any idea where I have gone wrong?  And advice as to how I can do it correctly?

---

