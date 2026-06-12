---
title: "Unable to burn DVD video that works in my domestic player"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by TimRead on 2007-03-22
Is it just me or is there something really wrong with DVD video burning in Linux for domestic players...

I am using Ubuntu Edgy and when I try to burn dvd video (in a VIDEO_TS) directory either using the default DVD writing tool that starts when I put a virgen DVD in the computer, or K3B, the process works and I can replay the DVD in a computer (under Linux or Windows) but not in my domestic DVD player (connected to my TV) I get an error... Not only that, but if I actually look at the disk, I cannot see that anything has been burnt onto it like I can when I burn the DVD from Windoze, using Nero, which incidently does run perfectly on my domestic player. 

I have even used the option -dvd-compat with growisofs, but no joy... 

As I mentioned above, it is neither the film, the disk nor the writer, because I can produce a readable copy from Nero under Windoze...

It really annoys me having to boot up windoze just to write dvds. Any ideas?

Thanks,

Tim

---

### Post by Ardrias on 2007-06-25
Try passing the -dvd-video switch at the end of your syntax, usually helps for me.

---

