---
title: "What filetype is this/how do I play it?"
date: 2008-12-04
forum: Multimedia Software
---

### Post by es926 on 2008-12-04
Hello,

Does anybody know what filetype this ([http://FileHost.JustFreeSpace.Com/468b.mp4](http://FileHost.JustFreeSpace.Com/468b.mp4)) is? 

The header starts out "$ftypmp42mp42isom3gp63g2a3gp4]&#65533;moovlmvhd" which makes me expect it to be an mp4 or m4a file, but I can't get it to play with any program I've tried. mplayer treats it as a video file that's just random static for a second or two. faad gives me "Error: Bitstream value not allowed by specification". file just returns "data".

If anybody has any information about how to play, convert, or repair this file I would really appreciate it!

Thanks!

---

### Post by wolfen69 on 2008-12-04
.mp4 is the file type that ipods and psp's play. i believe the file may be corrupted, as i have other .mp4's that play just fine with vlc.

---

### Post by es926 on 2008-12-04
Thanks for the reply.

I have other mp4s that play fine too, but in the header they say "ftypM4A" (not sure if that makes a difference).

I tried to reconstruct this file from sniffed packets containing streaming music (just to learn about how that stuff works :-). The file definitely plays correctly through the stream player so I don't think it's corrupt. The fact that the header seemed so readable made me think that the file was unencrypted. If I just stream an mp3 and use my code to reconstruct it it works fine so I don't think that that's the problem. Is it possible that they made a special file format (or modified one) specifically to stop people from doing what I'm trying to do?

---

