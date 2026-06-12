---
title: "Hald (?) causing problems for DVD playback"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by Jiawen on 2006-12-31
I'm having problems playing DVDs. The disc will occasionally just spin (the drive light goes on) and nothing plays. I've tried both my DVD drives and neither works. I've also tried several different media players (Totem and gmplayer among others) and they all work the same -- they just freeze up, sometimes requiring an X restart or a whole system restart. Trying to eject the discs usually either ends up with a "Writing to media" dialog box coming up ("Writing to media"?!? I don't want the system to *burn* anything -- these are pre-recorded discs!), or just nothing -- no response, the light stays on and the disc keeps spinning.

Checking the process list, I find that gmplayer is uninterruptible. After Googling a bit, it seems that this is due to hald. hald-addon-storage is listed as an uninterruptible  process every time I have this problem. Someone else on these forums recently had [a similar problem]("http://ubuntuforums.org/showthread.php?t=242096"). I've seen [a post on a Fedora forum]("http://www.fedoraforum.org/forum/showthread.php?p=673765#post673765") that indicates it might have to do with auto-mounting media. I now have both "Mount removable drives when hot-plugged" and "Mount removable media when inserted" unchecked, but this hasn't stopped the problem. 

I've also seen [a thread here]("http://ubuntuforums.org/showthread.php?t=90379&highlight=uninterruptible") that mentions a similar problem, but I have no idea how to go about doing things with the kernel. If there's a way to fix the problem without mucking about in the kernel, I'd love to know it; if I *have* to change things with the kernel, I could use some guidance in how to do so!

Please help! Thanks.

---

### Post by Jiawen on 2007-01-14
Bump. This is a major problem; it affects pretty much anything I want to do with a disc -- burning, playing, opening, everything. Is there any solution? ](*,)

---

