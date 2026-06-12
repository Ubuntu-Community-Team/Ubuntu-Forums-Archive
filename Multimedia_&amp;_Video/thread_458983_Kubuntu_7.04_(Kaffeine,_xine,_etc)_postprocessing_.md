---
title: "Kubuntu 7.04 (Kaffeine, xine, etc): postprocessing doesn't work"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by Kuzmitch on 2007-05-30
Hello friends!

I hase sort of a problem (Kubuntu 7.04, Kaffeine player, xine library): there is no postprocessing on any mpeg4 (DivX, Xvid, etc) files. If a go to xine options -> Video -> Expert Options -> processing.ffmpeg_pp_quality all numbers which I put here (0...6) doesn't affect on results: all movies are blocky and looks terrible, especially on dark scenes or credits. Everything works fine on Winows at the same PC (sometimes I need Windows). Video decoding goes through ffmpeg.

I have also tried to use other players: VLC, Mplayer, but it looks the problem still exist. Regarding logfiles (from VLC, for example), "Using external postprocessing filter, max q = 6" displayed or similar but the picture is still crappy.

My monitor is Samsung SyncMaster 931BW connected over DVI to NVIDIA GeForce 6800 GS video, nvidia-glx drivers from repository.

Please advice any help. Where should I dig?

---

### Post by alan_new on 2007-07-16
I have the same problem. No matter what I do all is blocky.

---

### Post by alan_new on 2007-07-19
This is a changed post.

I think the correct answer to that problem is to enable direct rendering on graphic card. Now the video is what it should be. :)

---

