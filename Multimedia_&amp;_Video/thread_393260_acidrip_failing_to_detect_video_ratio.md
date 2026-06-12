---
title: "acidrip failing to detect video ratio"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by hotani on 2007-03-25
I have used acidrip on this particular DVD in the past (ghost in the shell SAC), crop detection worked, it ripped fine. I deleted (idiot! *smacks head*) the old .avi files and wanted to re-rip them to the computer, but acidrip is refusing to cooperate. 

Here's what happens: it sees the DVD, but "crop detection failed, is the DVD loaded?" is what I get when I attempt to use the crop detection. If I run it without that, the video ratio is wrong--it comes out as 4:3 when it should be 16:9 (video is squished--unwatchable when you know it should be 16:9!!). I have tried everything I can think of, and when I attempt to manually set the crop to 2:1, 16:9, or *anything*, the encoding fails immediately. 

What happened to acidrip? I have seen it become dysfunctional in the past after an update, has this happened again?

---

### Post by hotani on 2007-04-08
I fixed this by unchecking the 'Lock Aspect' box in the 'Scale' section. Then I set the width to 720, and height to 405 which is 16:9. This worked, but it was not perfect--there was still some empty space left above and below the video, but at least the ratio was more or less correct.

Strange that crop detection on some vids from that series worked fine while on others it did not.

---

